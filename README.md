# Happy Birthday — the full thing 🎂

A single-page animated birthday surprise: candles you blow out, a music-box
version of "Happy Birthday" that plays automatically, a photo/video gallery,
message balloons, a birthday calendar, a typewritten letter, and a reply box
that sends their thank-you straight to you on WhatsApp or email.

It's one self-contained file — `index.html` — with no build step, no
dependencies, and no server required.

## 1. Open it in VS Code

1. Unzip this folder and open it in VS Code (`File > Open Folder...`).
2. Install the **Live Server** extension (by Ritwick Dey) if you don't have
   it — it's the easiest way to preview the page with live reload.
3. Right-click `index.html` and choose **"Open with Live Server"**, or just
   double-click `index.html` in your file explorer to open it directly in a
   browser. Either way works for previewing.

## 2. Personalize it

Open `index.html` and scroll down to the `<script>` tag near the bottom.
Everything you need to edit lives in the `CONFIG` object at the top of it:

| Field | What it does |
|---|---|
| `NAME` | Your friend's name |
| `CANDLES` | Number of candles on the cake |
| `BIRTHDATE` | `YYYY-MM-DD` — powers the "days alive" counter and the calendar |
| `SIGNED` | How you sign the letter |
| `MY_WHATSAPP` | Your WhatsApp number, country code first, no `+` or spaces (e.g. `919876543210`) — this is where their reply goes |
| `MY_EMAIL` | Your email — the other option for their reply |
| `GIFT_MESSAGE` | The line revealed when they open the gift box |
| `MEDIA` | Your photos/videos — see below |
| `CAL_PHOTO` | A photo of them for the calendar (optional) |
| `BALLOONS` | An array of hidden messages, one per balloon |
| `LETTER` | The full birthday letter |

You can also personalize the link itself without touching the code, by
adding `?name=Rahul&from=Aditya` to the end of the URL.

### Adding your own photos and videos

Create a folder called `media` next to `index.html`, drop your files in
(e.g. `media/1.jpg`, `media/clip.mp4`), then reference them in the `MEDIA`
array:

```js
MEDIA: [
  { src: "media/1.jpg", caption: "the first one" },
  { src: "media/clip.mp4", caption: "peak chaos" },
],
```

Leaving `src` empty just shows a soft placeholder instead of a broken image,
so it's safe to add captions before you have the files ready.

## 3. Push it to GitHub

From a terminal in this folder:

```bash
git init
git add .
git commit -m "Birthday site"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

(Create the empty repository on GitHub first at github.com/new, without a
README or .gitignore, then use the URL it gives you above.)

## 4. Deploy it on Render

1. Go to [render.com](https://render.com) and sign in (GitHub login is
   easiest).
2. Click **New +** → **Static Site**.
3. Connect the GitHub repository you just pushed.
4. Render should auto-detect the settings from `render.yaml` in this repo.
   If it asks manually instead, use:
   - **Build Command:** leave blank
   - **Publish Directory:** `.`
5. Click **Create Static Site**. Render will give you a live URL
   (something like `https://happy-birthday-site.onrender.com`) within a
   minute or two.

Send that link to your friend. Every time you push a change to GitHub,
Render redeploys automatically.

## What's inside

- `index.html` — the entire site: HTML, CSS, and JavaScript in one file.
- `render.yaml` — tells Render this is a static site with no build step.
- `.gitignore` — keeps OS junk files out of your repo.

No npm, no React, no backend — just open, edit, and deploy.
