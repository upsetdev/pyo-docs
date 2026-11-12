# Pyo Docs

The content of [pyo.dev/docs](https://pyo.dev/docs). This repo only holds the
writing: [pyo-web](https://github.com/upsetdev/pyo-web) renders it.

## Editing

Pages are MDX files in `content/`, and each folder's `meta.json` sets the order
in the sidebar. The four segments in the sidebar's switcher are the folders
`(core)`, `cli`, `api` and `mcp`. The brackets keep `(core)` out of the URLs. To preview your changes, run the site next to this repo:

```bash
cd ../pyo-web
bun run dev      # copies the docs, then serves http://localhost:3000/docs
```

## Generated pages

Don't edit these: they come from the code, so they can't drift from it.

- `content/cli/commands.mdx`, from the CLI's own help
- `content/mcp/tools.mdx`, from the tool list in `crates/pyo-api/src/mcp.rs`
- `openapi/pyo.json`, the API reference, from the API's code

To update them, with the `pyo` repo next to this one:

```bash
cargo build -p pyo-cli                # in ../pyo
bun run generate                      # here
cargo run -p pyo-api --bin openapi    # in ../pyo, writes openapi/pyo.json here
```

## Icons

Pages and cards take an icon by name: `icon: rocket` in a page's frontmatter, or
`<Card icon="rocket" ... />`. The names are in `src/lib/docs-icons.tsx` in
pyo-web.

## License

The code and content are under the [Apache License 2.0](./LICENSE).
