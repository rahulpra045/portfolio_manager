# Portfolio Review Manager – Update Files

This repository holds the update files for the Portfolio Review Manager desktop application (Pvt Ltd).

The application checks this repository to see whether a newer version is available. No client data, fund data, PINs or settings are stored here. All of that stays on the firm's own laptops.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The application page for the current version |
| `version.json` | Version number, release note and checksum of `index.html` |

## How updates work

1. When the application starts on the main laptop, it reads `version.json` from this repository.
2. If the version number is newer than the one installed, an "Update available" message appears.
3. On clicking **Update now**, the application fetches `index.html`, checks it against the checksum in `version.json`, keeps a backup of the previous version, and reloads.
4. If there is no internet connection, the check is skipped and the application works as normal.
5. Other laptops on the network follow the main laptop and get the update from it automatically.

Updates never change the firm's data. A **Roll back** button in the application (Firm Settings → Application updates) returns to the previous version.

## Releasing a new version

1. Replace `index.html` and `version.json` with the new files supplied together.
2. Commit the changes to the `main` branch.

The `build` number in `version.json` must be higher than the previous one, and the `sha256` must match the uploaded `index.html`. If they do not match, the application refuses the update and nothing is changed.
