# Cloud Resume

> My personal resume, deployed to AWS and automatically updated on every push.

A static resume website built with HTML and CSS, hosted on AWS S3, and wired up with a CI/CD pipeline using GitHub Actions. The goal was to go beyond just writing a resume — I wanted to actually deploy it like a real project, with automated deployments and cloud hosting.

🔗 **Live site:** [zikri-cloud-resume-2026.s3-website.us-east-2.amazonaws.com](http://zikri-cloud-resume-2026.s3-website.us-east-2.amazonaws.com)

---

## What This Project Demonstrates

- **AWS S3 static hosting** — the site is served directly from an S3 bucket configured for public web hosting
- **CI/CD with GitHub Actions** — every push to `main` automatically syncs the latest files to S3, no manual upload needed
- **End-to-end ownership** — from writing the code locally, committing to Git, through to a live URL on AWS

---

## How It Works

```
Local changes → Git commit → Push to GitHub → GitHub Actions → AWS S3 → Live site
```

1. Resume files (`index.html`, `style.css`, `script.js`, `assets/`) are edited locally
2. Changes are pushed to the `main` branch on GitHub
3. GitHub Actions picks up the push and runs the deploy workflow (`.github/workflows/`)
4. The workflow syncs the updated files to the S3 bucket using the AWS CLI
5. The live site reflects the changes instantly

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, JavaScript |
| Hosting | AWS S3 (static website hosting) |
| CI/CD | GitHub Actions |
| Version Control | Git, GitHub |

---

## Project Structure

```
Cloud_Resume/
├── .github/workflows/   # GitHub Actions deploy workflow
├── assets/              # Images and supporting files
├── index.html           # Main resume page
├── style.css            # Stylesheet
├── script.js            # Minor scripting
└── Mohamad_Zikri_Resume.pdf  # Downloadable PDF version
```

---

## Deployment Setup

The deployment is fully automated, but here's what was configured to make it work:

**AWS side**
- Created an S3 bucket with static website hosting enabled
- Set bucket policy to allow public read access

**GitHub side**
- Added AWS credentials (`AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, `AWS_REGION`, `S3_BUCKET`) as GitHub repository secrets
- Created a workflow file that runs `aws s3 sync` on every push to `main`

Once set up, no manual steps are needed — push to GitHub and the site updates automatically.

---
