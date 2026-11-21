# 360° Tour Studio

A browser-based 360° panoramic tour authoring studio. It uses Three.js from jsDelivr and plain HTML/CSS/JavaScript. No build step, server, API key, or backend is required.

## Features
- Import multiple equirectangular JPG/PNG/WebP panoramas
- 360° mouse/touch drag, zoom, fullscreen
- Add interactive hotspots and link rooms together
- Upload a floor plan and place room markers
- Responsive dark editor UI
- Smartphone device-orientation control (browser/device support required)
- Export a standalone HTML tour with embedded panorama images
- Save and reopen a complete JSON project backup (panoramas embedded)

## Run locally
Because this app uses JavaScript modules and browser security APIs, serve the folder over HTTP rather than opening `index.html` directly.

### Option A — Python
```bash
cd panorama-tour-studio
python -m http.server 8000
```
Open http://localhost:8000

### Option B — VS Code
Install the **Live Server** extension, right-click `index.html`, then choose **Open with Live Server**.

## Publish on GitHub Pages
1. Create a new repository on GitHub, for example `360-tour-studio`.
2. Upload `index.html`, `styles.css`, `app.js`, and `README.md` to the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, select **Deploy from a branch**.
5. Select branch `main` and folder `/ (root)`, then click **Save**.
6. Wait for GitHub Pages to publish. Your site URL will look like `https://YOUR-USERNAME.github.io/360-tour-studio/`.
7. Open that HTTPS URL on your phone. Import/viewer projects are created in the editor; export a standalone HTML tour and upload that HTML (or its contents as a separate Pages site) to share the finished tour.

## Smartphone gyroscope
- Device orientation is requested only after the user taps the motion button.
- iOS Safari requires an explicit permission prompt. Android browser support varies by device and browser.
- For reliable device orientation, use the deployed HTTPS URL. GitHub Pages provides HTTPS automatically.
- If the browser does not expose a gyroscope/orientation sensor, use touch drag instead.

## Panorama preparation
- Use equirectangular 2:1 images, e.g. 6000 × 3000 px.
- Keep the horizon level and avoid black borders.
- Large panoramas use more memory. For mobile use, 4096 × 2048 or 6000 × 3000 is a practical starting point.

## Notes and limitations
- This is a front-end prototype. Project data is held in the current page session; use **Save project** to download a complete JSON backup (including embedded panorama images), then **Open project** to restore it.
- The standalone export embeds panorama images and loads Three.js from jsDelivr, so an internet connection is needed when opening the exported tour.
- Floor plan markers are visual scene markers; clicking them in the exported viewer is not yet wired to switch scenes. Scene-to-scene hotspot navigation is functional.
- Browser orientation APIs are subject to browser security policies, permissions, and hardware support. No browser API can guarantee gyroscope access on every phone/browser combination.
