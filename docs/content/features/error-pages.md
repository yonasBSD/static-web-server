# Error Pages

**`SWS`** provides custom HTML error pages for the HTTP `404` and `50x` status errors.

This feature is enabled by default and can be controlled either by the string `--page404` ([SERVER_ERROR_PAGE_404](./../configuration/environment-variables.md#server_error_page_404)) or the `--page50x` ([SERVER_ERROR_PAGE_50X](./../configuration/environment-variables.md#server_error_page_50x)) arguments.

!!! info "Tip"
    Either `--page404` and `--page50x` have defaults (optional values) so they can be specified or omitted as required.

Below is an example of how to customize those HTML pages.

```sh
static-web-server \
    --port 8787 \
    --root ./my-public-dir \
    --page404 ./my-page-404.html \
    --page50x ./my-page-50x.html
```

## Fallback Page for use with Client Routers

It is possible to provide a HTML file to be used as fallback page when `GET` request paths dont exist.
The fallback page will be served with a `200` status code, useful when using client routers like `React Router` or similar.
If the path is not specified or simply doesn't exist then this feature will not be activated.

!!! info "The fallback page path is not relative to the root"
    The fallback page is an independent path, so provide a valid relative or absolute path.

It can be set with the `SERVER_FALLBACK_PAGE` environment variable or with the CLI argument `--page-fallback`.

```sh
static-web-server \
    --port 8787 \
    --root ./my-public-dir \
    --page-fallback ./my-public-dir/index.html
```
