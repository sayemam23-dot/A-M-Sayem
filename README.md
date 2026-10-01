# A M Sayem — Portfolio

A static, responsive personal portfolio site built with plain HTML, CSS and JavaScript (no frameworks, no build step). Designed to be hosted for free on GitHub Pages.

This is the **single-file build**: all CSS and JavaScript are inlined directly inside `index.html`, and all images/files live in one flat `assets/` folder (no subfolders). This is deliberate — nested folders are the #1 reason GitHub's web upload breaks portfolio sites, so this version has as few moving parts as possible.

## Folder structure

```
/
├── index.html          ← the whole site: markup, styling and script all in one file
├── assets/
│   ├── profile.jpg     ← your photo (add this)
│   ├── Sayem-CV.pdf    ← your CV (add this)
│   └── favicon.png     ← site icon (add this)
└── README.md
```

## Run it locally

No install needed — just double-click `index.html` to open it in a browser.

## How to update your portfolio content

Everything content-related lives in **one place**: the `portfolioData` object near the bottom of `index.html`, inside the `<script>` tag. Search the file (Ctrl+F) for:

```
EDIT THIS SECTION TO UPDATE YOUR PORTFOLIO
```

### Add a project
Copy this shape into the `projects` array:
```js
{
  name: "Project Name",
  category: "Category",
  description: "One or two sentences.",
  role: "Your role",
  tools: ["Tool 1", "Tool 2"],
  outcome: "What happened / result",
  github: "",     // optional
  demo: "",       // optional
  caseStudy: ""   // optional link or anchor
}
```
It will automatically appear as a card in the Projects section — no other HTML editing required.

### Add research, experience, certifications, or achievements
Same idea — each has its own array (`research`, `experience`, `certifications`, `achievements`) in the same `portfolioData` object. Copy an existing object in that array, fill in your details, save.

### Update skills or "currently learning"
Edit the `skills` object (grouped by category) or the `currentlyLearning` array, same place.

### Update your name, email, links
Edit the `personal` object at the very top of `portfolioData`. This automatically fills in every email/LinkedIn/GitHub/resume link across the whole site (nav, hero, footer, contact) — change it once, it updates everywhere.

## How to add your photo, CV and favicon (and avoid the folder problem)

GitHub's web "Upload files" button frequently **drops empty or nearly-empty folders**, or flattens them, especially if you select files through the file-picker dialog instead of dragging them in. To avoid that entirely:

1. Go to your repo on GitHub → **Add file → Create new file**.
2. In the filename box, type `assets/profile.jpg` — yes, with the slash. GitHub will create the `assets` folder automatically the moment you use a `/` in the filename.
   - You can't paste a binary image into the text editor this way, so instead: create a throwaway text file first (e.g. type `assets/.keep` as the filename, leave the body empty, commit). This makes the `assets` folder exist in the repo.
3. Now go back to **Add file → Upload files**. With the `assets` folder already existing, GitHub will show it as a destination — open it, then drag your `profile.jpg`, `Sayem-CV.pdf`, and `favicon.png` in directly.
4. Commit.

If you'd rather do it in one step: drag the entire `assets` folder (not the zip, the extracted folder) straight from your computer's file explorer onto the GitHub upload page — dragging a folder (rather than clicking "choose your files") is what preserves its structure.

Filenames matter (GitHub Pages is case-sensitive) — keep them exactly:
- `assets/profile.jpg`
- `assets/Sayem-CV.pdf`
- `assets/favicon.png`

If a file is missing, nothing breaks — the photo box just shows an empty placeholder and the CV/favicon links simply won't resolve until you add them.

## Dark mode

A light/dark toggle (the ◐ button in the nav) is included and saves your preference in the visitor's browser (`localStorage`), so it's remembered on their next visit.

## Deploy on GitHub Pages

1. Create a new GitHub repository (e.g. `portfolio`) and upload `index.html`, `assets/`, and `README.md` to the repo root — not inside any extra subfolder.
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to `Deploy from a branch`.
4. Choose the `main` branch and the `/ (root)` folder, then save.
5. GitHub will give you a URL shaped like:
   ```
   https://YOUR_USERNAME.github.io/YOUR_REPOSITORY/
   ```
   It can take a minute or two to go live after the first deploy — hard-refresh (Ctrl+Shift+R) if it looks unstyled right after deploying.

Every path in this project is relative (e.g. `assets/profile.jpg`, never `/assets/profile.jpg`), so the site works correctly whether it's hosted at a domain root or in a subfolder like `github.io/repository-name/`.

## Checklist — what you still need to provide

- [ ] Add your photo at `assets/profile.jpg`
- [ ] Add your CV at `assets/Sayem-CV.pdf`
- [ ] Add a favicon at `assets/favicon.png`
- [ ] (Optional) Add an Open Graph cover image at `assets/og-cover.png` and update the `og:image` tag in `index.html` to match
- [ ] Fill in the two research paper placeholders in the `research` array once you have titles/conference names/abstracts
- [ ] Fill in ITM Club role/period/responsibilities in the `experience` array once decided
- [ ] Add any additional projects, certifications, or achievements as they happen
