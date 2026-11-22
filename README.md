# KineMotion Assets

Public, versioned hosting for KineMotion downloadable packs.

## Why public

In-app downloads use unauthenticated HTTPS URLs. No token is embedded in the app. Private repos require auth, so this repo stays public.

## Release layout

Each release tag (for example `v1.0.0`) contains:

- `asr-hi-en-base-v1.zip`
- `asr-multilingual-tiny-v1.zip`
- `fonts-extended-v1.zip`
- `fonts-indic-v1.zip`
- `manifest-v1.json`

Download URL form:

```text
https://github.com/silent5441/kinemotion-assets/releases/download/v1.0.0/<asset-name>
```

## Manifest

See `schema/manifest-v1.schema.json`.

Each entry pins:

- `id`, `kind`, `version`, `label`
- `url`, `sha256`, `size`
- `languages`, `license`, `recommended`

The app verifies SHA-256 before install.

## Integrity policy

- SHA-256 is pinned in the app build, not fetched blindly from the network.
- ZIP entries are validated: no `../`, no absolute paths, no executables or symlinks.
- Install is atomic; old version is removed only after success.

## Licensing

Model and font licenses are shipped inside each pack as `LICENSE.txt`.
Only permissive or OFL licensed assets are published.

## Updating

1. Build pack zip.
2. Compute `sha256sum` and byte size.
3. Update manifest.
4. Create a new release tag. Never overwrite an existing tag's assets.

## Status

Phase 0 bootstrap. Actual packs are added in later phases.
