# Getting Started with Create Blocklet

This project was bootstrapped with [Create Blocklet](https://github.com/blocklet/create-blocklet).

This blocklet is a static project, which means this is a frontend application. It's contained `client` code.

## Launch on Blocklet Server

[![Launch on Blocklet Server](https://assets.arcblock.io/icons/launch_on_blocklet_server.svg)](https://install.arcblock.io/?action=blocklet-install&meta_url=https%3A%2F%2Fgithub.com%2Flinchen1987%2Frobertmao-com-website%2Freleases%2Fdownload%2Fv0.2.0%2Fblocklet.json)

## File Structure

- public/ - static files
  - favicon.ico - favicon
  - favicon.svg - favicon
- screenshots/ - Screenshots
- site/ - Client side code (A standard Blocklet Page project)
- .gitignore - Git ignore file
- .prettierrc - Prettier configuration
- blocklet.md - Blocklet README
- blocklet.yml - Blocklet configuration
- LICENSE - License file
- logo.png - Blocklet logo file
- Makefile - Makefile
- package.json - Npm package file
- README.md - A guide for this blocklet
- version - Version file

## Development

1. Make sure you have [@blocklet/cli](https://www.npmjs.com/package/@blocklet/cli) installed

   Blocklet needs blocklet server as a dependency. So you need to install it first.  
   `npm install -g @blocklet/cli`  
   See details in [https://docs.arcblock.io/abtnode/en/introduction/abtnode-setup#use-the-binary-distribution](https://docs.arcblock.io/abtnode/en/introduction/abtnode-setup#use-the-binary-distribution)

2. Init blocklet server & start blocklet server

   Before starting an blocklet server, you need to init blocklet server.  
   `blocklet server init --mode=debug`  
   `blocklet server start`  
   See details in [https://docs.arcblock.io/abtnode/en/introduction/abtnode-setup#configure-abt-node](https://docs.arcblock.io/abtnode/en/introduction/abtnode-setup#configure-abt-node)

3. Go to the project directory `cd [name]`
4. Install dependencies: `npm install` or `yarn` or `pnpm`
5. Start development server: `blocklet dev`

## Bundle

After developing a blocklet, you may need to bundle it. Use `npm run bundle` command.

## Deploy

- If you want to deploy this blocklet to local blocklet server, you can use `blocklet deploy .blocklet/bundle` command(Make sure the blocklet is bundled before deployment.)
  > Or you can simply use `npm run deploy` command.
- If you want to deploy this blocklet to remote blocklet server, you can use the command below.

  ```shell
  blocklet deploy .blocklet/bundle --endpoint {your blocklet server url} --access-key {blocklet server access key} --access-secret {blocklet server access secret}
  ```

  > Make sure the blocklet is bundled before deployment.

## Upload to blocklet store

- If you want to upload the blocklet to any store for other users to download and use, you can following the following instructions.

  Bump version at first.

  ```shell
  make bump-version
  ```

  Then config blocklet store url.
  You can use those store url in below.

  1. [https://store.blocklet.dev/](https://store.blocklet.dev/)
  2. [https://dev.store.blocklet.dev/](https://dev.store.blocklet.dev/)
  3. A blocklet store started by yourself.
     > Make sure you have installed a `blocklet store` on your own blocklet server. Check it on here: [https://store.blocklet.dev/blocklet/z8ia29UsENBg6tLZUKi2HABj38Cw1LmHZocbQ](https://store.blocklet.dev/blocklet/z8ia29UsENBg6tLZUKi2HABj38Cw1LmHZocbQ)

  ```shell
  blocklet config set store {store url}
  ```

  Get a `accessToken` from blocklet store.

  > Why we need a `accessToken`?  
  > A `accessToken` is genrate by blocklet store, which help us upload our blocklet to any store.

  Set `accessToken` to blocklet config

  ```shell
  blocklet config set accessToken {accessToken}
  ```

  Upload a new version to a store.

  > Make sure the blocklet is bundled before upload.

  ```shell
  blocklet upload
  ```

  Or you can simply use `npm run upload` command.

- You also can upload a new version to blocklet store by Github CI.  
  Bump version at first.

  ```shell
  make bump-version
  ```

  Push your code to Github main/master branch, or make a pull request to the main/master branch.  
  The CI workflow will automatically upload a new version to a store.

## Q & A

1. Q: How to change a blocklet's name?

   A: Change the `name` field in the `package.json` file, change the `name` field in the `blocklet.yml` file.

   You can also change the `title` field and `description` field in the `blocklet.yml` file.

   Run `blocklet meta` command, you will get a `did` config, copy the `did` value.

   Replace this command `"bundle": "PUBLIC_URL='/.blocklet/proxy/{did}' npm run build",` in `package.json`

   Replace `did` field in the `blocklet.yml`

2. Q: How to change a blocklet's logo?

   Change the `logo.png` file root folder.

   Or you can change the `logo` field in the `blocklet.yml` file.

   > Make sure you have added the logo path to the `blocklet.yml` file `files` field.

## Learn More

- Full specification of `blocklet.yml`: [https://github.com/blocklet/blocklet-specification/blob/main/docs/meta.md](https://github.com/blocklet/blocklet-specification/blob/main/docs/meta.md)
- Full document of Blocklet Server & blocklet development: [https://docs.arcblock.io/abtnode/en/introduction](https://docs.arcblock.io/abtnode/en/introduction)

## License

The code is licensed under the Apache 2.0 license found in the
[LICENSE](LICENSE) file.
