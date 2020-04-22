This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/zeit/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

## Deploy on Azure App Service

**Azure**

- Create resource / Web App
  - Publish: Code
  - Node: 12 LTS
  - Operation System: Linux
- On the resource, go to Settings / Configuration
  - In General Settings:
    - Major version: LTS
    - Startup Command: **yarn start:azure** or **npm run start:azure**

- On the resource, go to Settings / Configuration
  - In Application settings
    - Add new variables:
      - **PORT = 80**
      - WEBSITE_NODE_DEFAULT_VERSION = 12-lts   *(it is optional)*

If you want to use web.config, there's an [example](https://blogs.msdn.microsoft.com/azureossds/2016/04/18/sample-nodejs-app-on-azure-app-services/) and [the options](https://github.com/tjanczuk/iisnode/blob/master/src/samples/configuration/web.config) of the file.

**Github**

- In your repository `https://github.com/<my-user>/<my-repo>/settings/`secrets
- Add Secret value
  - name: AZURE_APPSERVICE_PUBLISH_PROFILE
  - value: `<azure-portal/your-app-service-resource/settings/deployment-center/deployment-credentials/get-publish-profile>`
- Go to `https://github.com/<my-user>/<my-repo>/actions/new`
  - Click on `Set up a workflow yourself` button
  - Include [this content](https://github.com/ricardocanelas/nextjs-dynamic-azure-example/blob/master/.github/workflows/master_nextjs-dynamic-azure-example.yml) as an example

[More Tips](https://microsoft.github.io/AzureTipsAndTricks/blog/tip233.html)
