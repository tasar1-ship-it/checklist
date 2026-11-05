# Checklist Lukas — PWA

Packing checklist deployable as a Progressive Web App on GitHub Pages.

## Files

- `index.html` — main app with localStorage persistence
- `manifest.json` — PWA manifest
- `service-worker.js` — offline cache
- `icon-180.png`, `icon-192.png`, `icon-512.png` — app icons

## Deploy to GitHub Pages

Suggested repo name: **`checklist`**
Final URL: `https://tasar1-ship-it.github.io/checklist/`

### One-time setup

```bash
cd ~/Downloads
mkdir checklist && cd checklist

# Copy all files from this folder into the repo
# (index.html, manifest.json, service-worker.js, icon-*.png)

git init
git add .
git commit -m "Initial commit: Lukas packing checklist PWA"
git branch -M main
git remote add origin https://github.com/tasar1-ship-it/checklist.git
git push -u origin main
```

Then on GitHub:
1. Create the empty repo `checklist` under `tasar1-ship-it` first (before the push above)
2. After push: **Settings → Pages → Source: `main` branch, root → Save**
3. Wait ~1 minute for first deploy

### Updates later

```bash
cd ~/Downloads/checklist
git add .
git commit -m "Update checklist"
git push
```

## Lukas iPhone setup (one time, ~30 sec)

1. Open Safari → go to `https://tasar1-ship-it.github.io/checklist/`
2. Tap the Share button (square with arrow)
3. Scroll down → tap **Add to Home Screen**
4. Tap **Add**

The icon now sits on his home screen. Tapping it opens fullscreen — no Safari bars. Checks persist across sessions, app restarts, even airplane mode (cached).

## Notes

- localStorage key: `lukas_checklist_v1` — survives app restarts but is per-device
- If you edit the checklist content later, bump `CACHE_NAME` in `service-worker.js` from `lukas-checklist-v1` to `-v2` so devices fetch the new version
- The reset button asks for confirmation before clearing
