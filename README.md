# siamcreations.app

The company site at the apex. One page, no build step, no JavaScript.

- `index.html` — the page
- `styles.css` — design tokens shared with the OmniHub site
- `CNAME.example` — rename to `CNAME` once the apex DNS points here; Pages
  claims the custom domain as soon as that file is present
- `404.html` — fallback for unknown paths

## Serving it

GitHub Pages, from the repository root of the default branch.

## DNS (IONOS)

The apex currently points at an IONOS placeholder host (`74.208.236.215`)
and does not answer over HTTPS. To serve this page instead, replace the apex
`A` records with GitHub Pages' addresses:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

Leave `MX` (`mx00/mx01.ionos.com`), `SPF`, DKIM and DMARC untouched: mail is
independent of the `A` records, so `support@siamcreations.app` keeps working.
`omnihub.siamcreations.app` is a separate Pages site and is unaffected.

Then in the repository: Settings → Pages → Custom domain
`siamcreations.app`, wait for the certificate, and enable "Enforce HTTPS".

## Why the apex matters

Paddle reviews the website registered on the seller account. A reviewer landing
on a parking page, or on a URL that fails over HTTPS, is a rejection waiting to
happen. This page exists so that `https://siamcreations.app` describes the
business and links to the products.

## Editing

Prices and product copy live in `index.html`. The OmniHub card links to the
product site rather than repeating its prices, so the two cannot disagree for
long: the authoritative price is always the one on the checkout page.
