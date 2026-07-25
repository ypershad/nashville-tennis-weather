# Nashville Tennis Weather

A free, mobile-friendly web page that tells you when and where it's good to play tennis around Nashville, based on live weather (rain, feels-like temp, wind). It's a single file — `index.html` — with no server, no API key, and no build step. Weather comes from the free [Open-Meteo](https://open-meteo.com) API, fetched directly in the browser.

## Three modes
1. **Scan courts** — pick a day, see playable time windows for every court (sorted by most clear time).
2. **Check a slot** — pick a court + time, get a yes/maybe/no with the reasons.
3. **Find a court** — pick a time, get courts ranked best-to-worst for that moment.

## Put it online for free (5 minutes)

**GitHub Pages**
1. Create a free GitHub account and a new repository (e.g. `tennis-weather`).
2. Upload `index.html` to the repo (drag-and-drop in the web UI works).
3. Repo → **Settings → Pages** → Source: **Deploy from a branch** → Branch: `main`, folder `/root` → Save.
4. Wait ~1 minute. Your public URL is `https://<your-username>.github.io/tennis-weather/`. Share it / add to your phone home screen.

**Netlify (even faster)** — go to app.netlify.com, drag the folder onto the page, done. You get an instant public URL.

You can also just double-click `index.html` to open it locally — it still needs internet to reach Open-Meteo.

## Adding or editing courts (the part you'll do)
Open `index.html` in any text editor and find the `COURTS` array near the top (it's clearly marked `EDIT ME: COURTS`). Copy a line and change the name, area, and coordinates:

```js
{ name:"New Court Name", area:"Neighborhood", lat:36.1234, lon:-86.7890 },
```

To get `lat`/`lon`: open Google Maps, right-click the exact spot, and the first two numbers in the menu are latitude and longitude. Save the file and re-upload. That's it — the new court shows up in all three modes automatically.

> Note: **Farm & Forge Club** uses an approximate College Grove location — replace its `lat`/`lon` with the exact spot when you have it.

## Tuning the rules
Right below the courts is an `EDIT ME: PLAYABILITY THRESHOLDS` (`CONFIG`) block. Change any number and save:
- `temp` — feels-like cutoffs. Currently: below 40° = No, 40–45° = caution, 90–95° = caution, above 95° = No.
- `rain` — the hard stop. Any measurable precip or ≥70% chance = No; 40–70% = caution.
- `wind` — minor; gusts ≥30 mph = caution only.
- `hours` — the daily scan window (default 6am–10pm).
