# bny-corp.com

The one-page site for BNY, served by GitHub Pages at https://bny-corp.com.

## Do not edit `index.html` here

It is generated. The source lives in the private `us_deal_flow` working tree
(`ybenaya/us-deal-flow` on GitHub), and everything it says about the buy box —
the market, the price band, the ZIP list — is derived from
`config/markets/indianapolis.yaml` there. Editing this copy means the next deploy
silently reverts it.

To change what the page says:

```
# in the us_deal_flow working copy
us-deal-flow publish                       # regenerate from the market config
Copy-Item site/dist/index.html ../bny-corp-site/index.html
git -C ../bny-corp-site commit -am "Update buy box" && git -C ../bny-corp-site push
us-deal-flow publish --live                # confirm what is actually served
```

That last step is not ceremony. The outreach email sends every recipient to
this domain instead of attaching anything, so a page that is stale, or a deploy
that never happened, is the first impression a wholesaler gets. It has already
gone wrong twice: the copy once advertised two metros the business had left,
and this domain served a Squarespace "under construction" notice on the day the
first outreach was nearly sent.

`index.html` here is the comment-stripped build. The source file carries the
reasoning behind the wording and which claims are deliberately left off, which
is an internal record and not something to publish in page source.

`CNAME` binds the custom domain. `.nojekyll` stops Pages running the file
through Jekyll, which it has no reason to do for a single hand-written page.
