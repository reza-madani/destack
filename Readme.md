(ALPHA)

# Get started

### Installing the plugin
1. Run `npm i next-grapejs-plugin`

2. Create `pages/api/builder/handle.js` with the following:
```js
import { handleData } from 'next-grapejs-plugin'
export default (req, res) => handleData(req, res, [require('fs'), require('path')])
```

3. Then create a Next.js page with:

```js
import { MarkdownProvider, getStaticDataProps } from 'next-grapejs-plugin'

import '../node_modules/grapesjs/dist/css/grapes.min.css'

export const getStaticProps = () => getStaticDataProps([require('fs'), require('path')]) 

export default function Home({html, css}) { return (<MarkdownProvider html={html} css={css}/>) }
```

Deploy a new Next.js app on Vercel:
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/git/external?repository-url=https://github.com/vercel/next.js/tree/canary/examples/progressive-web-app&project-name=progressive-web-app&repository-name=progressive-web-app)

<details>
<summary>Development</summary>
<br>

1. `git clone https://github.com/LiveDuo/next-grapejs-plugin` and cd in there

2. `npm i --legacy-peer-deps` (see note below)

3. `npm link`

4. create a Next.js project and cd into it

5. `npm link next-grapejs-plugin`

6. `npm link ../next-grapejs-plugin/node_modules/grapejs`

7. add `pages/api/builder/handle.js` and `pages/[component].js` as shown above.

8. move back into `next-grapejs-plugin` folder

9. `npm link ../\*\*the-next-project-folder\*\*/node_modules/react`

**Note:** If you are installing npm packages into the plugin remember to install with `--legacy-peer-deps`. If you missed that remember to delete `node_modules/react` and `node_modules/react-dom` folders and run step 5 again. If you know a better way to do this please let me know.
</details>

# TODO
### Launch
1. Fix "Basic", "Extra" and "Forms" blocks (default to closed)
    - Fix Device selector icons
    
    - Change "Basic" and "Forms" blocks to tailwind HTML blocks
    - Need tailwind-like icons for "Basic" and "Forms" blocks

    - Trim down new code
    - (OK) Look into default to close
2. Check images upload 

### Later
4. Write tests
5. Max width settings (+colors)
6. Move builder API route to next.config.js
