# Vite + Vue + Multi app issue
## Issue 
Following this in the docs:

https://vitejs.dev/guide/build.html#multi-page-app

Works on build but not on dev.

Dev server seem to always serve `<root>/index.html`. Even on `localhost:3000/nested`
## Directory structure
```
|-package.json
|-vite.config.js
|-index.html (points to src/main.js)
|-src/
|---main.js
|---App.vue
|-nested/
|---index.html
|---nested.js
|---App.vue
```
## Vite Config
According to the docs added the following build config
```
...
 build: {
    rollupOptions: {
      input: {
        main: resolve(__dirname, 'index.html'),
        nested: resolve(__dirname, 'nested/index.html')
      }
    },
  },
...
```

## Conclusion 
`npm run build` then serve `/dist` Folder => OK

**`npm run dev` Goto `localhost:3000/nested` you will still get the main app.**