# Mitti Studio (YuvaIntern Junior Frontend Developer Internship)

A responsive landing page for a beginner pottery studio, built with semantic HTML5, CSS3 and vanilla JavaScript. No frameworks or dependencies.

- **Week 1:** responsive landing page
- **Week 2:** accessible booking modal (demo only)
- **Week 3:** accessibility review and improvements
- **Week 4:** performance optimization (this version)

## Project structure
```
mitti-landing/
  src/                   readable source files: edit these
    index.html
    css/style.css
    js/main.js
  build.js               build script (Node.js, no packages needed)
  dist/                  optimized site: upload or open this
    index.html           minified, with the CSS inlined
    js/main.<hash>.js    minified JavaScript with a content hash in the name
    _headers             cache rules for Netlify / Cloudflare Pages
  measurement/           scripts used to take the lab measurements
  performance-report.md  before and after analysis
```

## Run the optimized site
Open `dist/index.html` in a browser. No server is needed.

## Rebuild after editing
1. Edit the files in `src/`.
2. Run `node build.js` in this folder (Node.js 14 or newer).
3. Open `dist/index.html` to check the result.

## Week 4 optimizations
| Change | Why |
|---|---|
| HTML, CSS and JS minified by `build.js` | Smaller files, shorter download and parse time |
| Minified CSS inlined in `index.html` | The first paint no longer waits for a second request |
| Content hash in the JS file name, plus cache rules in `_headers` | The script can be cached for a year; a changed file gets a new name automatically |
| Inline icon in the page head | Stops browsers from requesting a missing `/favicon.ico` |

Already in place before Week 4: the script loads with `defer`, only system fonts are used (no font downloads), there are no images, and the scroll listener is passive.

Details, measurements and the ideas that were tested but not kept are in `performance-report.md`.

## Accessibility and features
All Week 1 to Week 3 features are unchanged: responsive menu, booking modal with validation and focus management, newsletter form, visible focus rings, reduced-motion support. The optimized build passes the same scripted accessibility (34) and regression (25) checks as the Week 3 version.

## Limitations
- The booking and newsletter forms are front-end demonstrations. Nothing is sent or stored.
- Measurements come from a scripted Chromium lab test, not from real users.
- Cache rules in `_headers` only work on hosts that read that file. They were not tested on a live host.
