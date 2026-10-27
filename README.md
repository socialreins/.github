# SocialReins

SocialReins is an open-source social media manager. Write a post once, send it to every platform, and pull it back from all of them when you need to.

⭐ **If SocialReins looks useful, star [socialreins/web](https://github.com/socialreins/web) and [socialreins/brain](https://github.com/socialreins/brain).** Stars help other people find the project and tell us it is worth building.

## What it will do

These are being built now (see Status below).

- **Publish and schedule** to Facebook Pages, Instagram, Threads, LinkedIn, Bluesky and X, now or at a time you pick.
- **Take posts down everywhere** a post went out, in one step.
- **Sets and lists:** group accounts into sets, and posts into ordered lists.
- **Built for AI agents:** a REST API and an MCP server let your agents post for you.

## Status

SocialReins is early. The landing page and the hosted-version waitlist are live at [socialreins.com](https://socialreins.com). Publishing, accounts and the MCP server are being built now. Watch or star the repos to follow along.

## Repositories

| Repo | What it is |
|---|---|
| [web](https://github.com/socialreins/web) | **Main repo, start here.** The website and the app, built with Next.js |
| [brain](https://github.com/socialreins/brain) | The API server, written in Rust (Axum, SeaORM, Postgres) |
| [.github](https://github.com/socialreins/.github) | This org profile, plus the contributing guide, security policy and code of conduct for every repo |

## Run it locally

You need Git, Docker, Rust (stable) and Node 24.

**1. Start the API (brain)**

```sh
git clone https://github.com/socialreins/brain.git
cd brain
docker compose up -d postgres
export DATABASE_URL=postgres://brain:brain@localhost:5432/socialreins_brain
cargo run -p socialreins-brain        # http://localhost:8080
```

Migrations run when the server starts. Check it with `curl http://localhost:8080/health`. Port 5432 taken? Run `PG_PORT=55433 docker compose up -d postgres` and use that port in `DATABASE_URL`.

**2. Start the website and app (web)**, in a second terminal

```sh
git clone https://github.com/socialreins/web.git
cd web
cp .env.example .env.local            # NEXT_PUBLIC_API_URL=http://localhost:8080
npm ci
npm run dev                           # http://localhost:3000
```

Open http://localhost:3000. Today that is the landing page and the waitlist; the app arrives as features ship. The waitlist form talks to your local brain, which already allows requests from `http://localhost:3000`.

Each repo's README lists its tests, checks and environment variables.

## Self-host

A production self-host guide (Docker images, environment, upgrades) lands in [socialreins/web](https://github.com/socialreins/web) once the full app ships. Until then, both repos include the `Dockerfile` we deploy with.

## Hosted version

Rather not run servers? Join the waitlist at [socialreins.com](https://socialreins.com) for the hosted version, a paid subscription coming later.

## Contributing

- Read the [contributing guide](https://github.com/socialreins/.github/blob/main/CONTRIBUTING.md) and the [Code of Conduct](https://github.com/socialreins/.github/blob/main/CODE_OF_CONDUCT.md).
- Bugs and ideas: open an issue in [web](https://github.com/socialreins/web/issues), or in [brain](https://github.com/socialreins/brain/issues) for the API.
- Security problems: do not open an issue. Email security@socialreins.com, see the [security policy](https://github.com/socialreins/.github/blob/main/SECURITY.md).

## License

[AGPL-3.0](https://github.com/socialreins/web/blob/main/LICENSE). Built by Bytech.

⭐ Enjoying it? [Star web](https://github.com/socialreins/web) and [star brain](https://github.com/socialreins/brain).

## About this repo

This repo holds organization-wide files. `profile/README.md` is the profile shown on [github.com/socialreins](https://github.com/socialreins) (keep it in sync with this README). `CONTRIBUTING.md`, `SECURITY.md`, `CODE_OF_CONDUCT.md` and the issue templates in `.github/ISSUE_TEMPLATE/` are the defaults for every repo in the org that has none of its own.
