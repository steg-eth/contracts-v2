# steg-eth/contracts-v2

This is a mirror of [ensdomains/contracts-v2](https://github.com/ensdomains/contracts-v2). Steg keeps it as an evidence archive for its ENSv2 work.

## Branches

- `main` tracks upstream `main` byte for byte. The workflow in `.github/workflows/sync-upstream.yml` runs on this branch every six hours. It fast-forwards `main` and copies tags. Nobody commits to `main` here.
- `pin/*` branches freeze the commits that Steg documents cite. They survive force-pushes and deletions upstream.
  - `pin/pr465-5079ac1c`: PR #465 at `5079ac1c`, the mainnet deployment records after the root registry redeploy.
  - `pin/pr453-ed37923e`: PR #453 at `ed37923e`, the `DNSTLDResolver` bump.
  - `pin/pr419-3690d94`: PR #419 at `3690d94`, the `SET_SUBREGISTRY` change.
- `steg` holds only this README and the workflow. It is the default branch so that the schedule runs.

## Notes

- GitHub disables scheduled workflows in a public repository after 60 days without activity. If the sync stops, run it once by hand from the Actions tab.
- The default token cannot push commits that add or change workflow files. With it, the workflow uses GitHub's fork sync for `main` and copies every tag it is allowed to push; it lists the tags it had to skip. Two historical tags (`v0.0.1-namechain`, `sepolia-deployment-2026-05-28`) carry an older workflow file and are therefore not here. To mirror everything, add a repository secret `SYNC_TOKEN`: a fine-grained token with Contents and Workflows write on this repository. The workflow uses it when present.
- Upstream ships its own CI in `.github/workflows/main.yml`. A push made with `SYNC_TOKEN` would run it here, so the sync disables every workflow except itself after each run. Nothing but the sync runs in this repository.
- Issues and pull requests belong upstream. This repository does not accept them.
