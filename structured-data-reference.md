# Structured data reference — Naira2Dollar Deals

Schemas already **live on the site** (open the page source to see them):

| Schema | File |
|---|---|
| Organization | `index.html` |
| WebSite (with SearchAction) | `index.html` |
| FAQPage | `index.html`, `blog/blog-post-template.html` |
| BreadcrumbList | `blog/index.html`, `blog/blog-post-template.html` |
| Blog / CollectionPage | `blog/index.html` |
| BlogPosting (Article) | `blog/blog-post-template.html` |
| HowTo | `blog/blog-post-template.html` |

Below are ready-to-paste `<script type="application/ld+json">` snippets for the remaining types you listed. A few of these (JobPosting, Course, Event, Dataset, LocalBusiness) don't map naturally onto a deals/reviews site as it exists today — they're included and adapted to the closest realistic use case, with a note on when you'd actually want them. Drop any of these into the `<head>` (or just before `</body>`) of the relevant page, and fill in the placeholder values.

---

## LocalBusiness
Use this **only if** you open a physical storefront, showroom, or office people can visit — an online-only deals site shouldn't use LocalBusiness, since it implies a visitable location and can hurt local SEO if the address is fake. If you ever add a pop-up shop or office, adapt this:

```json
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "Naira2Dollar Deals",
  "image": "https://www.naira2dollardeals.com/assets/storefront.jpg",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "123 Example Street",
    "addressLocality": "Lagos",
    "addressRegion": "LA",
    "postalCode": "100001",
    "addressCountry": "NG"
  },
  "telephone": "+234-000-000-0000",
  "openingHours": "Mo-Fr 09:00-17:00"
}
```

## ContactPage / ContactPoint
Add to a dedicated `/contact.html` page, or keep the `ContactPoint` already nested inside the `Organization` schema on `index.html`:

```json
{
  "@context": "https://schema.org",
  "@type": "ContactPage",
  "name": "Contact Naira2Dollar Deals",
  "url": "https://www.naira2dollardeals.com/contact.html",
  "mainEntity": {
    "@type": "Organization",
    "name": "Naira2Dollar Deals",
    "contactPoint": {
      "@type": "ContactPoint",
      "email": "hello@naira2dollardeals.com",
      "contactType": "customer support",
      "areaServed": "Worldwide",
      "availableLanguage": "English"
    }
  }
}
```

## Service
Fits if you ever formalize "deal-sourcing" or "sponsored review" as a service you offer to brands:

```json
{
  "@context": "https://schema.org",
  "@type": "Service",
  "serviceType": "Product review and deal-sourcing",
  "provider": {
    "@type": "Organization",
    "name": "Naira2Dollar Deals"
  },
  "areaServed": "Worldwide",
  "description": "Independent product testing and deal curation for online shoppers.",
  "url": "https://www.naira2dollardeals.com/"
}
```

## Event
Only relevant if you run a live event (a webinar, live shopping stream, in-person meetup). Example for a hypothetical Black Friday livestream:

```json
{
  "@context": "https://schema.org",
  "@type": "Event",
  "name": "Naira2Dollar Deals — Black Friday Live Picks",
  "startDate": "2026-11-27T18:00:00-00:00",
  "endDate": "2026-11-27T19:00:00-00:00",
  "eventAttendanceMode": "https://schema.org/OnlineEventAttendanceMode",
  "eventStatus": "https://schema.org/EventScheduled",
  "location": {
    "@type": "VirtualLocation",
    "url": "https://www.naira2dollardeals.com/live"
  },
  "organizer": {
    "@type": "Organization",
    "name": "Naira2Dollar Deals",
    "url": "https://www.naira2dollardeals.com/"
  }
}
```

## VideoObject
Add this to any blog post or product review that embeds a video (unboxing, demo, etc.):

```json
{
  "@context": "https://schema.org",
  "@type": "VideoObject",
  "name": "Unboxing: the $29.99 noise-cancelling earbuds",
  "description": "A two-minute unboxing and first-impressions look at this week's deal of the week.",
  "thumbnailUrl": "https://www.naira2dollardeals.com/assets/video/earbuds-thumb.jpg",
  "uploadDate": "2026-09-02T09:00:00-00:00",
  "contentUrl": "https://www.naira2dollardeals.com/assets/video/earbuds-unboxing.mp4",
  "embedUrl": "https://www.youtube.com/embed/VIDEO_ID"
}
```

## JobPosting
Only relevant if you hire (e.g., a part-time deal researcher or writer). Example:

```json
{
  "@context": "https://schema.org",
  "@type": "JobPosting",
  "title": "Part-time Deal Researcher",
  "description": "Source, verify, and write up daily deals across electronics, home, and beauty categories.",
  "datePosted": "2026-09-09",
  "validThrough": "2026-10-09",
  "employmentType": "PART_TIME",
  "hiringOrganization": {
    "@type": "Organization",
    "name": "Naira2Dollar Deals",
    "sameAs": "https://www.naira2dollardeals.com/"
  },
  "jobLocationType": "TELECOMMUTE",
  "applicantLocationRequirements": {
    "@type": "Country",
    "name": "Remote — worldwide"
  }
}
```

## Course
Only relevant if you launch paid/free educational content (e.g., "How to build a deals site" or "Smart online shopping 101"). Example:

```json
{
  "@context": "https://schema.org",
  "@type": "Course",
  "name": "Smart Online Shopping 101",
  "description": "A short email course on spotting real discounts, verifying reviews, and avoiding fake flash sales.",
  "provider": {
    "@type": "Organization",
    "name": "Naira2Dollar Deals",
    "sameAs": "https://www.naira2dollardeals.com/"
  }
}
```

## Dataset
Only relevant if you publish raw data (e.g., a downloadable CSV of tracked prices over time). Example:

```json
{
  "@context": "https://schema.org",
  "@type": "Dataset",
  "name": "Naira2Dollar Deals — Weekly Price Tracker",
  "description": "Historical price data for products featured on Naira2Dollar Deals, updated weekly.",
  "url": "https://www.naira2dollardeals.com/data/price-tracker.csv",
  "creator": {
    "@type": "Organization",
    "name": "Naira2Dollar Deals"
  },
  "distribution": {
    "@type": "DataDownload",
    "encodingFormat": "text/csv",
    "contentUrl": "https://www.naira2dollardeals.com/data/price-tracker.csv"
  }
}
```

---

### Note on "Business" and "Product" structured data
Your list included "Business structured data" — that's covered by the `Organization` schema already on `index.html`. If you'd rather mark up individual deal cards as `Product` + `Offer` (recommended for the deals grid, since it can trigger price/rating rich snippets in Google), let me know and I'll wire that into `index.html` next — it wasn't in your original list but it's the highest-value addition for a deals site specifically.
