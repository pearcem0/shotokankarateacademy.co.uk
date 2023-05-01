# shotokankarateacademy.co.uk

A static site quickly and easily generated with [Hugo](https://gohugo.io/getting-started/quick-start/), styled with a modified version of the [Design template](https://themes.gohugo.io/hugo-scroll/) by [Jan Raasch](https://www.janraasch.com/)

## Development

A brief list of noteable reminders for future reference

- Install Hugo (see the [Hugo Quickstart Guide](https://gohugo.io/getting-started/quick-start/))
- Command Line Interface commands:
  - `hugo new homepage/newpage.md`
    - This creates a new file in the `content` folder under the `homepage` directory
  - `hugo server -D` (run the server with Draft mode enabled, which should rebuild as changes are made and saved)
  - View the site locally at http://localhost:1313/ (unless stated otherwise in the terminal!)
  - `hugo -D` (Build the static pages, output should go to ./public/ by default)

### Adding Themes

(As per [Hugo Quickstart Guide](https://gohugo.io/getting-started/quick-start/)) First, download the theme from GitHub and add it to your site’s themes directory:
- Command Line Interface commands:
  - `git submodule add [<url>] themes/[<name of theme>]`

For example:

- `git submodule add https://github.com/s4n7h0/hugo-theme-timeline themes/timeline`

You may choose to fork a repository for a theme to make your own changes or additions: 

- `git submodule add https://github.com/pearcem0/hugo-theme-timeline themes/timeline`

## Build & Deployment

Currently deployed to AWS (Amazon Web Services).

- Static files stored in Amazon S3 with Static website hosting enabled.
- DNS and HTTPS redirection configured with [CloudFlare](https://support.cloudflare.com/hc/en-us/articles/360037983412-Configuring-an-Amazon-Web-Services-static-site-to-use-Cloudflare).


### Automated Deployment

To automate the build and deployment there is a Github Actions Workflow in the `.git/workflows/main.yml` file that that runs when code is merged.

#### Pre-requisites

To provide permissions for the workflow to upload files to the Amazon S3 Bucket, you will need to add Github secrets to restore the values for a valid AWS Access Key Pair (AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY) along with the name of the S3 buckets (BUCKET_NAME and STAGING_BUCKET_NAME) and the region that the bucket is deployed in (AWS_REGION).

### Manual Deployment

#### Local build

- `hugo server -D` (run the server with Draft mode enabled, which should rebuild as changes are made and saved)
- View the site locally at http://localhost:1313/ (unless stated otherwise in the terminal!)
- `hugo -D` (Build the static pages, output should go to ./public/ by default)

#### Uploading files to S3

Something _like_...
`aws s3 cp public/ s3://<bucket name> --recursive --profile <profile name>`

## Errors or Omisions?

If you spot something wrong, or have something to add feel free to create a Pull Request.