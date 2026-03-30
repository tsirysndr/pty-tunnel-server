# pty-tunnel-server releases

Automated GitHub Actions workflow that builds [`pty-tunnel-server`](https://github.com/vercel/sandbox/tree/main/packages/pty-tunnel-server) from the [vercel/sandbox](https://github.com/vercel/sandbox) monorepo and publishes pre-built binaries as GitHub Releases.

## What is pty-tunnel-server?

`pty-tunnel-server` is a self-contained Go binary that provides a WebSocket-based pseudo-terminal (PTY) tunnel. It enables secure remote terminal access inside a Vercel sandbox environment without requiring Node.js or any runtime dependencies.

## Release artifact

Each release publishes the following asset:

| File | OS | Arch |
|------|----|------|
| `pty-server-linux-x86_64.tar.gz` | Linux | x86_64 |

The archive contains a single executable: `pty-tunnel-server`.

## Triggering a release

Push a semver tag to this repository:

```sh
git tag v1.0.0
git push origin v1.0.0
```

The workflow will:
1. Clone `vercel/sandbox`
2. `cd` into `packages/pty-tunnel-server`
3. Cross-compile for Linux x86_64 (`GOOS=linux GOARCH=amd64`)
4. Package the binary into `pty-server-linux-x86_64.tar.gz`
5. Upload the tarball to the GitHub Release created by the tag

## Workflow

See [`.github/workflows/release.yml`](.github/workflows/release.yml).