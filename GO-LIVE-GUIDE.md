# Welcome Baptist Church Website — Go-Live & Handoff Guide

This guide has two parts:

- **Part 1 — Setup (Trent does this once).** Creating the GitHub account, publishing the site with Netlify, and connecting the church's domain.
- **Part 2 — Weekly Updates (the church's tech contact).** How to add sermons and keep the site current. Print this part and give it to him.

**Total cost: $0/month.** GitHub is free, Netlify is free. The only cost is the domain renewal (~$10–20/year), which the church already pays.

---

# PART 1 — One-Time Setup (Trent)

## Step 1: Create a GitHub account for the church

GitHub is a website that stores the website's files. Think of it as a Dropbox folder that the live website is built from — every time a file changes, the live site updates automatically.

1. Go to **github.com** and click **Sign up**.
2. Use an email the church controls (e.g., info@welcomebaptistonline.com).
3. Pick a username like **welcomebaptistchurch**.
4. Choose the **Free** plan.
5. Save the username and password somewhere safe — you will hand these over later.

> Why a church account instead of your own? So that when you hand over the keys, the church owns its own website. You'll add yourself as a collaborator so you can still help.

## Step 2: Create a repository and upload the website files

A "repository" (repo) is just a folder on GitHub.

1. Once logged in, click the **+** in the top-right corner → **New repository**.
2. Repository name: **church-website**
3. Set it to **Public** (required for free hosting; the files are just your public website anyway).
4. Click **Create repository**.
5. On the next page, click the link that says **uploading an existing file**.
6. Open the `welcome-baptist` folder on your computer. Select ALL the files and the `css` folder inside it, and drag them into the GitHub upload box.
   - Important: drag the *contents* of the folder, not the folder itself. `index.html` must end up at the top level of the repo.
7. Scroll down, click **Commit changes** (green button).

Your files are now on GitHub. ("Commit" just means "save.")

## Step 3: Publish the site with Netlify

Netlify is the free hosting service that takes the GitHub files and serves them as a live website.

1. Go to **netlify.com** → **Sign up** → choose **Sign up with GitHub** (this links the two accounts — sign up while logged in to the church's GitHub account).
2. Click **Add new site** → **Import an existing project** → **GitHub**.
3. Authorize Netlify when asked, then select the **church-website** repository.
4. Leave every setting at its default and click **Deploy**.
5. In about a minute, the site is live at a temporary address like `random-name-12345.netlify.app`. Click it and verify the site looks right.
6. Optional: in **Site settings → Change site name**, rename it to something like `welcomebaptist.netlify.app`.

**This temporary address is also your demo link** — you can send it to the pastor before the domain is ever touched.

From now on: any file changed in GitHub automatically republishes the live site in ~60 seconds. That's the whole magic.

## Step 4: Point the church's domain at the new site

The church owns **welcomebaptistonline.com**. Right now it points at their old host (Crownweb). You need access to wherever the domain is registered.

1. Ask the church: "Who pays the bill for the website/domain?" Get the login for the domain registrar. If Crownweb manages the domain as part of their hosting package, ask Crownweb to either hand over the domain login or transfer the domain to a registrar the church controls (Namecheap or Cloudflare are good, ~$10–15/year). **Do not cancel Crownweb until the new site is live.**
2. In Netlify: **Domain settings** → **Add custom domain** → enter `welcomebaptistonline.com`.
3. Netlify will show you exactly what to change. The simplest option: at the registrar, set the domain's **nameservers** to the ones Netlify lists (this hands DNS to Netlify and everything else is automatic, including free HTTPS/the padlock icon).
4. Wait up to a few hours for it to take effect. The old site is now replaced by the new one.
5. THEN cancel the Crownweb hosting (keep the domain registration paid!).

### Before cancelling Crownweb — copy the files off the old server

The photos and sermon audio currently live on Crownweb's server. When it's cancelled, they vanish. Before that:

1. Download the photos and sermon files from the old site.
2. Convert sermons from .wma to .mp3 (free at cloudconvert.com, or ask Claude to do it) — .wma files don't play on iPhones.
3. Upload them into the GitHub repo (create an `images` folder and a `sermons` folder) and update the links in the HTML.
4. (Claude can do this whole step for you — just ask.)

## Step 5: Hand over the keys

Give the tech contact:

1. The GitHub username and password (and the email account it's tied to).
2. The Netlify login (same — it's the GitHub login).
3. Part 2 of this guide, printed.

To keep your own access for support: in the repo, go to **Settings → Collaborators → Add people** and add your personal GitHub account.

---

# PART 2 — Weekly Updates (Tech Contact's Cheat Sheet)

Everything below happens in a web browser at **github.com**. You never need to install anything. Every change you save ("commit") automatically updates the live website about 60 seconds later.

## How to add a new sermon

1. Log in at github.com and open the **church-website** repository.
2. **First, upload the audio file:** click the `sermons` folder → **Add file → Upload files** → drag the MP3 in → **Commit changes**.
   - Name files consistently, e.g. `butler-2026-06-14.mp3` (no spaces).
3. **Then, add it to the sermons page:** click `sermons.html` → click the **pencil icon** (top right of the file) to edit.
4. Find the current month's section (search for `sermon-month`). Copy an existing sermon entry — it looks like this:

```
<li><span><span class="title">Bro. Roger Butler</span> <span class="date">&mdash; June 7, 2026</span></span>
  <a class="listen" href="sermons/butler-2026-06-07.mp3">Listen</a></li>
```

5. Paste it directly above the previous week's entry, then change three things: the preacher's name, the date, and the file name in `href="..."`.
6. Click **Commit changes** (green button). Done — check the live site in a minute.

### Starting a new month
Copy a month heading line and the `<ul class="sermon-list">` ... `</ul>` block, paste it above the old month, and update the month name.

## How to update the calendar / events

The events calendar is a Google Calendar embedded in the site. You don't edit the website at all:

1. Log in to the church's Google account.
2. Open Google Calendar and add/edit events normally.
3. The website shows the changes automatically.

(If the calendar page hasn't been set up yet, ask Trent — it's a one-time embed.)

## How to change text anywhere on the site

1. In the repo, click the page file (`index.html` = homepage, `about.html`, `services.html`, etc.).
2. Click the **pencil icon** to edit.
3. Find the text you want to change (Ctrl+F works). Change only the words between the `>` and `<` symbols — don't delete the tags around them.
4. **Commit changes**.

## If something breaks

Don't panic — GitHub keeps every previous version forever.

1. In the repo, click **History** (clock icon) on the file you changed.
2. Find the last version that worked, open it, and restore it.
3. Or just contact Trent: trent@dmprocessing.com.

## Golden rules

- Change words, not code. If you didn't mean to touch something starting with `<`, undo it.
- One change at a time, then check the live site.
- Never delete files you don't recognize (especially anything in `css`).
- The site can always be fixed — nothing is permanent.
