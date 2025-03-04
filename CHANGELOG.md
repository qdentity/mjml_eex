# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.9.1] - 2022-02-10

### Changed

- Relax `phoenix_html` to make it compatible with phoenix 1.7.
- Upgrades the dependencies to the latest version.

## [0.9.0] - 2022-09-05

### Added

- MJML EEx now has Telemetry support for the rendering process. Take a look at the
  `MjmlEEx.Telemetry` module for more details.

### Changed

- The configuration options that are passed to MJML EEx have change in structure
  and there is now a `:compiler_opts` entry for options that are passed to the
  configured compiler.

## [0.8.1] - 2022-07-22

### Fixed

- Removed `:erlexec` as an `:extra_application` so it does not cause compilation errors.

## [0.8.0] - 2022-07-22

### Changed

- `:erlexec` is now an optional dependency. If you attempt to use the Node compiler without this dependency
  an error will be raised. The error message contains information on pulling it down and starting the `:erlexec`
  application.

## [0.7.0] - 2022-05-26

### Added

- You can now chose your MJML compiler. By default the Rust NIF compiler is used, but there is also an
  adapter for the Node MJML compiler.

## [0.6.0] - 2022-05-06

### Added

- The `render_static_component` function can be used to render components that don't make use of any assigns. For
  example, in your template you would have: `<%= render_static_component MyCoolComponent, static: "data" %>` and this
  can be rendered at compile time as well as runtime.
- The `render_dynamic_component` function can be used to render components that make use of assigns at runtime. For
  example, in your template you would have: `<%= render_dynamic_component MyCoolComponent, static: @data %>`.

### Changed

- When calling `use MjmlEEx`, if the `:mjml_template` option is not provided, the module attempts to find a template
  file in the same directory that has the same file name as the module (with the `.mjml.eex` extension instead
  of `.ex`). This functions similar to how Phoenix and LiveView handle their templates.

### Removed

- `render_component` is no longer available and users should now use `render_static_component` or
  `render_dynamic_component`.

## [0.5.0] - 2022-04-28

### Added

- Templates can now either be compiled at runtime or at compile time based on the options passed to `use MjmlEEx`

## [0.4.0] - 2022-04-27

### Fixed

- Calls to `render_component` now evaluate the AST aliases in the context of the `__CALLER__`
- EEx templates, components and layouts are tokenized prior to going through the MJML EEx engine as not to escape MJML content

## [0.3.0] - 2022-04-17

### Added

- Ability to inject a template into a layout

## [0.2.0] - 2022-04-15

### Added

- Ability to render MJML component partials in MJML templates via `render_component`
- Macros for MJML templates
- Custom EEx engine to compile MJML EEx template to HTML
