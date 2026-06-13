# NineTrail — hosted website (legal & support)

Self-contained, dependency-free pages ready to host anywhere:

| File | Purpose | Used as |
|------|---------|---------|
| `index.html` | Landing page | App Store **Marketing URL** (optional) |
| `privacy.html` | Privacy Policy | **Privacy Policy URL** (required by both stores) |
| `terms.html` | Terms of Use | App Store EULA / Terms link |
| `support.html` | Support + FAQ + contact | App Store **Support URL** (required) |

All pages cross-link with **relative** links, so they work on any host as long as
the four files sit in the same folder. Contact email is `sontoshbhn@gmail.com`.
Effective date is **June 3, 2026** — edit it in `privacy.html` and `terms.html`
if you publish on a different day.

---

## Option A — GitHub Pages (free, recommended)

1. Create a public repo, e.g. `ninetrail-site`, and put these four files at its root.
2. Repo **Settings → Pages → Build and deployment → Deploy from a branch →
   `main` / `(root)`** → Save.
3. After a minute your live URLs will be (replace `<user>` with your GitHub name):
   ```
   https://<user>.github.io/ninetrail-site/privacy.html
   https://<user>.github.io/ninetrail-site/terms.html
   https://<user>.github.io/ninetrail-site/support.html
   https://<user>.github.io/ninetrail-site/            (index)
   ```
4. Open each URL in a browser to confirm it loads.

*(Alternatively serve the `website/` folder via Netlify drop, Cloudflare Pages,
Firebase Hosting, or any static host — the files need no build step.)*

---

## After hosting: where to paste the final URLs

### 1. In the app (one small file — string constants only)
`lib/core/constants/app_constants.dart` → replace the two placeholders:
```dart
static const String privacyPolicyUrl = 'PASTE your hosted privacy.html URL';
static const String termsUrl          = 'PASTE your hosted terms.html URL';
```
`supportEmail` is already set to `sontoshbhn@gmail.com`. Then run
`flutter analyze` and rebuild. *(The in-app Privacy screen already shows the full
summary natively; these URLs power the “Full policy” / “Terms” buttons.)*

### 2. Google Play Console
- **App content → Privacy policy** → privacy.html URL
- **Store listing** has no separate support/terms fields; include the support
  email in **Store settings → Contact details**.

### 3. App Store Connect
- **App information → Privacy Policy URL** → privacy.html URL
- **App information → Support URL** → support.html URL
- **App information → Marketing URL** (optional) → index.html URL
- **Version → App Review Information** can reference terms.html if asked; iOS uses
  Apple's standard EULA unless you add a custom one (terms.html can serve as it).

See `SUBMISSION_CHECKLIST.md` (Phase 1) for the full sequence.
