# Reddit Scraper: Deleted & Removed, Mods, Hidden Profiles

Get Reddit posts and comments as clean data, **including the ones that were deleted or removed**: you get the **original text and author when the archive captured them before the removal** (most posts' authors, about a third of removed post bodies, a minority of moderator-removed comments; numbers below), **who removed it** (the author, a moderator, AutoModerator or Reddit) and the **moderators' removal reason** when they left one. Also the **full moderator list** of any public subreddit, its rules, settings and posting requirements, and the history of **hidden profiles**.

**[Run it on Apify](https://apify.com/pomlabs/reddit-posts-comments-scraper?utm_source=github&utm_medium=readme&utm_campaign=reddit-posts-comments-scraper)**: no install, no login, free credit on a new Apify account.

## What you get

- **Removed and deleted content**: every post and comment says if it was removed, **by whom** (author, moderator, AutoModerator, Reddit) and whether it happened after the archive captured it. When it did, you still get the **original text and author**
- **Removal reason**: when the moderators left a notice on the removed post or comment (the `<subreddit>-ModTeam` message, AutoModerator or a moderator's reply), you get its text in `removalNoticeText`
- **Edited comments and posts, before and after**: every item says if it was edited and when. If the edit came after the archive captured it, you get the **text from before the edit**, and with `includeEditedText` also the **current text**, side by side (`bodyText` and `textAfterEdit`)
- **Full moderator list** of any public subreddit, the one Reddit shows only to logged-in users: username, moderator since, permissions. No account needed
- **Subreddit report**: rules, settings (restricted posting, allowed post types, NSFW, quarantine, flair), post requirements (banned domains, title and body rules), full moderator list, bots, wiki pages, top commenters and posters, the percentage of posts and comments removed, split by who removed them, how many removals came with a notice, the most used notices, and how many were removed for low karma or a new account
- **User profiles, hidden profiles included**: the user's own posts and, if you turn comments on, the user's own comments, even when the user hid their activity on Reddit ("Content and activity: hidden"), because the history comes from a public Reddit archive, not from the profile page
- **User report**: karma and totals, first and last activity, every subreddit the user was active in, and how much of their content was removed, also for hidden profiles
- **Newest comments of a subreddit or a user**, across all posts, with a filter for only deleted-by-author or only removed-by-moderator
- **Posts**: title, text, author, subreddit, flair, score, upvote ratio, number of comments, NSFW flag, external link, gallery images, post date and link
- **Comments**: text, author, score, depth, parent comment and post, date and link, in reading order (each comment is one item)
- **Keyword inside a subreddit**: only posts whose title or text contains your words
- **Reddit-wide search**: the most relevant posts for any keywords
- **Date range and order**: newest or oldest first, from/to any date
- **Clear status for problems**: `invalid_url`, `not_found`, `no_results` or `error`

## Pricing

**You pay only for items delivered: $0.002 per post or comment.** Invalid links and sources with no results are listed with the reason and never charged.

That is the free-plan price; Apify paid plans (Bronze, Silver, Gold) pay less per item.

## Call it by API

```bash
curl -X POST "https://api.apify.com/v2/acts/pomlabs~reddit-posts-comments-scraper/run-sync-get-dataset-items?token=YOUR_APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"startUrls": ["https://www.reddit.com/r/webscraping"]}'
```

Python:

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")
run = client.actor("pomlabs/reddit-posts-comments-scraper").call(run_input={"startUrls": ["https://www.reddit.com/r/webscraping"]})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Use it from Claude, Cursor or any MCP client

```bash
claude mcp add reddit-posts-comments "https://mcp.apify.com?tools=pomlabs/reddit-posts-comments-scraper" -t http
```

## Ready-made examples

- [See deleted Reddit comments on a post](https://apify.com/pomlabs/reddit-posts-comments-scraper/examples/see-deleted-reddit-comments-on-a-post)
- [Subreddit moderator list, rules and settings](https://apify.com/pomlabs/reddit-posts-comments-scraper/examples/subreddit-moderator-list)
- [See deleted Reddit comments by user (hidden profiles too)](https://apify.com/pomlabs/reddit-posts-comments-scraper/examples/see-deleted-reddit-comments-by-user)

## More Actors by Pom Labs

- [YouTube Transcript Scraper: Translate, No Login · $3/1K](https://apify.com/pomlabs/youtube-transcript-scraper?utm_source=github&utm_medium=readme&utm_campaign=reddit-posts-comments-scraper)
- [Instagram Transcript Scraper: Reels, TikTok, Facebook, Hook](https://apify.com/pomlabs/social-video-transcript?utm_source=github&utm_medium=readme&utm_campaign=reddit-posts-comments-scraper)
- [LinkedIn Company Scraper (No Cookies): Posts, Similar Companies](https://apify.com/pomlabs/linkedin-company-scraper?utm_source=github&utm_medium=readme&utm_campaign=reddit-posts-comments-scraper)
- [YouTube Comments Scraper + Replies, Shorts · No API Key · $1/1K](https://apify.com/pomlabs/youtube-comments-scraper?utm_source=github&utm_medium=readme&utm_campaign=reddit-posts-comments-scraper)
- [Instagram Profile Scraper: Exact Followers, Reels Views](https://apify.com/pomlabs/instagram-profile-data?utm_source=github&utm_medium=readme&utm_campaign=reddit-posts-comments-scraper)
- [LinkedIn Profile Scraper (No Cookies) + Similar Profiles](https://apify.com/pomlabs/linkedin-profile-scraper?utm_source=github&utm_medium=readme&utm_campaign=reddit-posts-comments-scraper)
- [Threads Scraper: Keyword Search, Posts & Profiles · No Login](https://apify.com/pomlabs/threads-scraper?utm_source=github&utm_medium=readme&utm_campaign=reddit-posts-comments-scraper)
- [AliExpress Scraper: Exact Units Sold, Prices, Search · $1/1K](https://apify.com/pomlabs/aliexpress-scraper?utm_source=github&utm_medium=readme&utm_campaign=reddit-posts-comments-scraper)
- [AI Brand Visibility Tracker - ChatGPT, Claude & Perplexity](https://apify.com/pomlabs/ai-brand-visibility?utm_source=github&utm_medium=readme&utm_campaign=reddit-posts-comments-scraper)
- [Mercado Livre & Amazon BR Coupon Code Checker](https://apify.com/pomlabs/mercadolivre-coupon-checker?utm_source=github&utm_medium=readme&utm_campaign=reddit-posts-comments-scraper)
- [Page Time Machine · Wayback Diff + AI · No Login · $2.5/1K](https://apify.com/pomlabs/page-time-machine?utm_source=github&utm_medium=readme&utm_campaign=reddit-posts-comments-scraper)
- [Video Downloader: TikTok No Watermark, Instagram, YouTube, X](https://apify.com/pomlabs/video-downloader?utm_source=github&utm_medium=readme&utm_campaign=reddit-posts-comments-scraper)
- [NSFW Image Detector & Image Tagger - Moderation + Categories](https://apify.com/pomlabs/image-moderation-tagger?utm_source=github&utm_medium=readme&utm_campaign=reddit-posts-comments-scraper)
- [Google Trends Scraper: Related Queries, No 429 · $2/1K](https://apify.com/pomlabs/google-trends-scraper?utm_source=github&utm_medium=readme&utm_campaign=reddit-posts-comments-scraper)

Full documentation, input fields and output format: [Reddit Scraper: Deleted & Removed, Mods, Hidden Profiles on Apify](https://apify.com/pomlabs/reddit-posts-comments-scraper?utm_source=github&utm_medium=readme&utm_campaign=reddit-posts-comments-scraper).
