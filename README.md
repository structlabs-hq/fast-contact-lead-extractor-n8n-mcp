# Fast Contact, Lead & Tech Stack Extractor — n8n Workflow & MCP Server

lead generation API for AI agents and automation. B2B contact enrichment. B2B contact extractor and lead enrichment API: company emails, phones, social profiles, decision-makers, website tech stack and ad pixels in one fast HTTP run.

- **Apify Actor:** [Fast Contact, Lead & Tech Stack Extractor](https://apify.com/structlabs/fast-contact-lead-extractor)
- **MCP server:** `https://mcp.apify.com/?actors=structlabs/fast-contact-lead-extractor`
- **n8n workflow:** [`n8n/fast-contact-lead-extractor-workflow.json`](n8n/fast-contact-lead-extractor-workflow.json)
- **Pricing:** Gold: $1.275 per 1,000 pages + $29.75 per 1,000 verified leads + $0.05 per 1,000 starts. [Full pricing](https://apify.com/structlabs/fast-contact-lead-extractor)

## Quick start with n8n

1. Download [`n8n/fast-contact-lead-extractor-workflow.json`](n8n/fast-contact-lead-extractor-workflow.json).
2. In n8n: **Workflows → Import from File**.
3. Add `APIFY_TOKEN` to the n8n environment (Settings → Environment Variables).
4. Open the workflow, adjust the schedule, and run once to test.
5. The HTTP Request node calls `run-sync-get-dataset-items` and returns the rows directly.

## Quick start with Python

```bash
export APIFY_TOKEN=apify_api_...
python examples/quickstart.py
```

## Quick start with Node.js

```bash
export APIFY_TOKEN=apify_api_...
node examples/quickstart.mjs
```

## Input

```json
{
  "startUrls": [
    "https://www.apify.com"
  ],
  "maxPagesPerDomain": 2,
  "maxDecisionMakers": 5,
  "verifyEmailDomains": true
}
```

## Sample output

Real sanitized rows from a verified cloud run (emails and phone numbers masked):

```json
[
  {
    "domain": "stripe.com",
    "website": "https://stripe.com",
    "start_url": "https://stripe.com",
    "emails": [
      "sales@example.com"
    ],
    "phones": [
      "+1-555-0100"
    ],
    "social_profiles": {},
    "technologies": [
      "Next.js",
      "Nginx"
    ],
    "ad_pixels": {
      "gtm_id": [
        "GTM-XXXXXXX"
      ]
    },
    "decision_makers": [],
    "verified_decision_makers": 0,
    "email_domain_valid": true,
    "email_domains": [
      {
        "domain": "stripe.com",
        "mx_found": true,
        "status": "mx_found"
      }
    ],
    "pages_scanned": 3,
    "pages_succeeded": 3,
    "error": null,
    "elapsed_ms": 548,
    "scraped_at": "2026-11-20T08:34:23Z"
  },
  {
    "domain": "apify.com",
    "website": "https://apify.com",
    "start_url": "https://apify.com",
    "emails": [
      "sales@example.com"
    ],
    "phones": [],
    "social_profiles": {
      "linkedin": [
        "http://linkedin.com/company/apify",
        "https://www.linkedin.com/company/apify"
      ],
      "tiktok": [
        "https://www.tiktok.com/@apifytech",
        "https://www.tiktok.com/@apifyoffice"
      ]
    },
    "technologies": [
      "AWS",
      "Google Analytics",
      "Google Tag Manager",
      "HubSpot",
      "Intercom",
      "Next.js"
    ],
    "ad_pixels": {
      "gtm_id": [
        "GTM-XXXXXXX"
      ]
    },
    "decision_makers": [],
    "verified_decision_makers": 0,
    "email_domain_valid": true,
    "email_domains": [
      {
        "domain": "apify.com",
        "mx_found": true,
        "status": "mx_found"
      }
    ],
    "pages_scanned": 3,
    "pages_succeeded": 2,
    "error": null,
    "elapsed_ms": 2008,
    "scraped_at": "2026-11-20T08:34:23Z"
  },
  {
    "domain": "gymshark.com",
    "website": "https://gymshark.com",
    "start_url": "https://www.gymshark.com",
    "emails": [
      "sales@example.com"
    ],
    "phones": [],
    "social_profiles": {
      "facebook": [
        "https://www.facebook.com/GymShark",
        "https://www.facebook.com/gymshark"
      ],
      "youtube": [
        "https://www.youtube.com/user/GymSharkTV"
      ],
      "instagram": [
        "https://www.instagram.com/gymshark"
      ],
      "x": [
        "https://www.twitter.com/gymshark",
        "https://x.com/gymshark"
      ],
      "tiktok": [
        "https://www.tiktok.com/@gymshark"
      ]
    },
    "technologies": [
      "AWS",
      "Intercom",
      "Next.js",
      "Nginx",
      "Shopify"
    ],
    "ad_pixels": {},
    "decision_makers": [
      {
        "name": "Alex M.",
        "title": "Founder",
        "email": "alex@example.com",
        "email_source": null,
        "email_domain_valid": null,
        "source_url": "https://www.gymshark.com/pages/about-us"
      }
    ],
    "verified_decision_makers": 0,
    "email_domain_valid": true,
    "email_domains": [
      {
        "domain": "gymshark.com",
        "mx_found": true,
        "status": "mx_found"
      }
    ],
    "pages_scanned": 6,
    "pages_succeeded": 3,
    "error": null,
    "elapsed_ms": 1864,
    "scraped_at": "2026-11-20T08:34:23Z"
  }
]
```

## MCP configuration

Copy [`mcp/mcp_config.json`](mcp/mcp_config.json) into your MCP client (Claude Desktop, Cursor, Windsurf):

```json
{
  "mcpServers": {
    "apify-fast-contact-lead-extractor": {
      "url": "https://mcp.apify.com/?actors=structlabs/fast-contact-lead-extractor"
    }
  }
}
```

Then ask your agent to run the Actor and return the dataset rows.

## Links

- Apify Store: https://apify.com/structlabs/fast-contact-lead-extractor
- n8n: https://n8n.io
- MCP: https://modelcontextprotocol.io

## License

MIT
