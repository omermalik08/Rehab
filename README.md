# Solutions Rehab & Therapy Owner Dashboard

Sites-compatible dashboard for a rehab and therapy company providing PT, OT, and ST services across SNFs.

The root page redirects to the imported owner dashboard at:

```text
/rehab-dashboard/index.html
```

## What Is Included

- `public/rehab-dashboard/index.html` - the runnable, self-contained dashboard served by the site.
- `dashboard-source/` - the lightweight rebuild package used to recreate the dashboard HTML, including the template, build script, required JSON snapshots, and helper scripts.
- `.openai/hosting.json` - Sites project metadata for deployment.

## Dashboard Coverage

The dashboard includes:

- company, facility, discipline, and therapist productivity
- revenue modeled from billable minutes, payer mix, and service-code rates
- CPT code volume and reimbursement views
- forecast and pace tracking
- scorecards and facility comparisons
- live-upload productivity panels

The shipped dashboard uses de-identified/source snapshot files from `dashboard-source/data`. Do not add PHI or patient-identifiable data to this repository.

Raw workbooks and oversized pipeline extracts are intentionally kept out of the deployable source tree. The hosted dashboard only needs the static HTML in `public/rehab-dashboard/index.html`.

## Local Development

```bash
npm run dev
```

The app uses Vinext/Next as the Sites-compatible wrapper. The main product surface is the static dashboard HTML in `public/rehab-dashboard/index.html`.

## Rebuilding The Static Dashboard

From `dashboard-source/`:

```bash
python build.py
```

That regenerates `dashboard-source/index.html` from `template.html` and the JSON files under `dashboard-source/data`. After rebuilding, copy the regenerated file to `public/rehab-dashboard/index.html`.

## Production Validation

```bash
npm run build
```

Run this before saving or deploying a Sites version.
