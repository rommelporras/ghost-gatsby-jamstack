# Ghost and Gatsby - JAMStack

A starter template to build a free and lightning fast JAMStack websites with [Ghost headless CMS](https://ghost.org) & [Gatsby](https://gatsbyjs.org)

**Demo:** https://gatsby.ghost.org

# Installing

```bash
# With Ghost & Gatsby CLI
npm install ghost -g
npm install gatsby-cli -g
```

```bash
# From Ghost-Gatsby-JAMStack source
git clone https://github.com/rommelporras/ghost-gatsby-jamstack.git
cd ghost-gatsby-jamstack
```

Then install dependencies

```bash
cd gatsby-starter-ghost
npm install
```

# Ghost Quickstart Install

If you want to run your own instance of Ghost, in most cases the best way is to use Ghost **CLI tool**

```
$ npm install ghost-cli -g
```

&nbsp;

Then, if installing locally add the `local` flag to get up and running in under a minute - [Local install docs](https://ghost.org/docs/install/local/). Go to `ghost-3` directory.

```
$ ghost install local
```

&nbsp;

or on a server run the full install, including automatic SSL setup using LetsEncrypt - [Production install docs](https://ghost.org/docs/install/ubuntu/)

```
$ ghost install
```

&nbsp;

Check out Ghost [official documentation](https://ghost.org/docs/) for more information about the [recommended hosting stack](https://ghost.org/docs/concepts/hosting/) & properly [upgrading Ghost](https://ghost.org/faq/upgrade-to-ghost-2-0/), plus everything you need to develop your own Ghost [themes](https://ghost.org/docs/api/handlebars-themes/) or work with [Ghost API](https://ghost.org/docs/api/).

[Setup Ghost Blog on AWS EC2 and RDS (AWS Free tier)](https://www.devopscycle.com/setup-ghost-blog-on-aws-ec2-rds-free-tier/) guide.
&nbsp;

# Running Gatsby

Start the development server. You now have a Gatsby site pulling content from headless Ghost.

```bash
gatsby develop
```

By default, the starter will populate content from a default Ghost install located at https://gatsby.ghost.io.

To use your own install, you will need to edit the `.ghost.json` config file with your credentials. Change the `apiUrl` value to the URL of your Ghost site. For Ghost(Pro) customers, this is the Ghost URL ending in `.ghost.io`, and for people using the self-hosted version of Ghost, it's the same URL used to access your site.

Next, update the `contentApiKey` value to a key associated with the Ghost site. A key can be provided by creating an integration within Ghost Admin. Navigate to Integrations and click "Add new integration". Name the integration appropriately and click create.

To use this starter without issues, your Ghost installation needs to be at least on version `2.10.0`.

The default Ghost version that is used for this starter is `3.x`. If your Ghost installation is on a lower version, you will need to pass in a `version` property in your `.ghost.json` settings:

**Ghost >=2.10.0 <3.0.0**
```json
{
    "apiUrl": "https://gatsby.ghost.io",
    "contentApiKey": "9cc5c67c358edfdd81455149d0",
    "version": "v2"
}
```

**Ghost <=3.0.0**
```json
{
    "apiUrl": "https://gatsby.ghost.io",
    "contentApiKey": "9cc5c67c358edfdd81455149d0"
}
```

&nbsp;

# Deploying with Netlify

The starter contains three config files specifically for deploying with Netlify. A `netlify.toml` file for build settings, a `/static/_headers` file with default security headers set for all routes, and `/static/_redirects` to set Netlify custom domain redirects.

To deploy to your Netlify account, hit the button below.

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/TryGhost/gatsby-starter-ghost)

Content API Keys are generally not considered to be sensitive information, they exist so that they can be changed in the event of abuse; so most people commit it directly to their `.ghost.json` config file. If you prefer to keep this information out of your repository you can remove this config and set [Netlify ENV variables](https://www.netlify.com/docs/continuous-deployment/#build-environment-variables) for production builds instead.

Once deployed, you can set up a [Ghost + Netlify Integration](https://docs.ghost.org/integrations/netlify/) to use deploy hooks from Ghost to trigger Netlify rebuilds. That way, any time data changes in Ghost, your site will rebuild on Netlify.

&nbsp;

# Optimising

You can disable the default Ghost Handlebars Theme front-end by enabling the `Make this site private` flag within your Ghost settings. This enables password protection in front of the Ghost install and sets `<meta name="robots" content="noindex" />` so your Gatsby front-end becomes the source of truth for SEO.

&nbsp;

# Extra options

```bash
# Run a production build, locally
gatsby build

# Serve a production build, locally
gatsby serve
```

Gatsby `develop` uses the `development` config in `.ghost.json` - while Gatsby `build` uses the `production` config.

&nbsp;

# Copyright & License

Copyright (c) 2019 Rommel Porras - Released under the [MIT license](LICENSE).
