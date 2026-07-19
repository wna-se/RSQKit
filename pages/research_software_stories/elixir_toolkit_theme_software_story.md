---
title: "Research Software Story - ELIXIR Toolkit Theme"
search_exclude: true
description: "A Jekyll theme designed to support easy deployment of documentation websites, as well as more complex sites requiring a central tool table and linking towards ELIXIR resources."
contributors: []
page_id: elixir_toolkit_theme_software_story
affiliations: []
---

## The Problem

### Reusable infrastructure for publishing static knowledge websites across ELIXIR and beyond
The [ELIXIR Toolkit Theme (ETT)](https://elixir-belgium.github.io/elixir-toolkit-theme/) is a [Jekyll](https://jekyllrb.com) theme designed to support easy deployment of documentation websites, as well as more complex sites requiring a central tool table and linking towards [ELIXIR](https://elixir-europe.org) resources. It is intended to provide a modern, lightweight, and flexible theme, with a sidebar to handle sizable amounts of content and a robust search function. This theme was initially set-up for [ELIXIR Research Data Management Kit (RDMkit)](https://rdmkit.elixir-europe.org/) and [ELIXIR Belgium’s RDM Guide](https://rdm.elixir-belgium.org), both resources providing data management guidelines and good practices for the life sciences, but has now been adopted by more than thirty known sites inclduing the [Research Software Quality Toolkit (RSQKit)](https://everse.software/RSQKit/).

The theme provides layouts, navigation, styling, search, and other common features used to publish a feature rich Jekyll-based static website. Being part of the website infrastructure developed for the RDMkit, requirements were added in response to the practical needs of a large, community-maintained knowledge resource. Drawing on experience with existing Jekyll themes, including the Jekyll Documentation Theme and Just the Docs, the developers found that no available option provided the required combination of flexible navigation, search, structured resource information, contributor attribution, branding, and maintainability. The theme was therefore developed alongside the websites it powered.

Other projects encountered similar needs. Rather than independently rebuilding the same publishing components, they chose to reuse the infrastructure developed for RDMkit. The theme was consequently elevated to a software product provided as an ELIXIR Belgium Node Service on its own, independently versioned, and distributed for use by other documentation and knowledge-base websites. Today, a quick way to use the theme is to reference it as a remote theme for {% tool "github-pages" %} but it can also be installed, configured, and deployed anywhere using Ruby and Jekyll.

The theme now provides a configurable foundation for more than thirty known sites, including RSQKit, [WorkflowHub website](https://about.workflowhub.eu/), [FAIRDOM](https://fair-dom.org/), the [Data Stewardship Handbook](https://elixir-europe.github.io/ds-handbook/), and resources operated by ELIXIR Nodes and the Australian BioCommons.

## User Community

### Supporting knowledge-resource teams with different roles and levels of technical experience

The theme is developed and maintained primarily by ELIXIR Belgium, with Bert Droesbeke as its principal maintainer. Contributions, requirements, and bug reports also come from ELIXIR Nodes, international partners, and projects that use the theme.

The user community includes three overlapping groups:

* **Content authors and editors:** Data stewards, researchers, trainers, and project staff create and update pages using Markdown and YAML. They benefit from structured templates, contributor attribution, resource records, and navigation systems without needing to edit the underlying layouts.
* **Site maintainers:** Research software engineers and technically experienced project members configure branding, navigation, deployment, metadata, and integrations. They generally need familiarity with Git and GitHub, but do not need to maintain a complete web application.
* **Theme contributors:** Developers work on reusable layouts, styling, JavaScript behaviour, plugins, and deployment workflows. Problems identified by one adopter can become improvements available to every project using a later release.

This range of users has shaped the software. The theme must remain approachable for people writing content while still offering enough flexibility for technically complex knowledge resources.

Development and release management remain concentrated within ELIXIR Belgium. Public project documentation does not describe a formal governance structure specific to the theme. This maintainer-led model allows decisions to be made efficiently, but the concentration of detailed technical knowledge and release responsibility in one principal maintainer creates a continuity risk.

## Technical Aspects

The ELIXIR Toolkit Theme is a Jekyll theme packaged as the Ruby gem `elixir-toolkit-theme`. It is research software infrastructure rather than scientific analysis software: it provides the publishing layer on which documentation, guidance, and community knowledge resources are built.

An adopter repository contains its own Markdown pages, YAML data, navigation configuration, and branding choices. Shared layouts, styles, search, metadata, and interface components remain in the versioned theme dependency. This separation allows many websites to use the same infrastructure without copying the theme source into each repository.

Development began in 2021. As of July 2026, the latest release is version 6.1.0, and the repository records 65 versioned releases.

The principal capabilities can be grouped into three areas:

* **Publishing and navigation:** Responsive layouts, configurable sidebars and top navigation, multiple website sections, custom branding, full-text search, tables of contents, and page tagging.
* **Knowledge-resource management:** Central YAML records for tools and resources, contributor and editor attribution, affiliations, and reusable links between pages and external resources.
* **Discovery and integration:** Sitemap generation, schema.org and other metadata attributes, analytics integrations, and links to ELIXIR services such as bio.tools, FAIRsharing, TeSS, RDMkit, the FAIR Cookbook, and the Data Stewardship Wizard.

The central tools and resources table is particularly important for larger knowledge sites. Instead of repeatedly entering information about a tool on individual pages, editors can define a structured record once and refer to it throughout the website. This supports more consistent names, identifiers, descriptions, and external links.

### Libraries and Systems

The software relies on a compact stack of established web technologies:

* **Core:** Jekyll, Ruby, Liquid templates, Markdown, YAML, SCSS, HTML, and {% tool "javascript" %}.
* **Interface:** Bootstrap 5 provides the responsive layout, Lunr.js powers client-side search, and DataTables supports searchable and sortable resource tables.
* **Extension:** The separate `elixir-toolkit-theme-plugins` Ruby gem adds improved tool tagging and deployment-related branch detection.
* **Integration:** `jekyll-sitemap`, schema.org metadata, analytics services, and links to relevant ELIXIR registries and knowledge resources.

Adopters primarily need to understand Markdown, YAML configuration, and Git-based workflows. Knowledge of Liquid, SCSS, and {% tool "javascript" %}. becomes necessary only when contributing to or substantially customising the shared theme.

## Software Practices

### Sharing improvements through version control, automated builds, and versioned releases

Development takes place openly on {% tool "github" %}, using {% tool "git" %} for version control. Issues and pull requests allow adopters to report problems, request features, and propose changes. External and substantial changes generally pass through pull requests, while smaller maintainer-led updates may be made more directly.

* **Code review:** Review is conversational and maintainer-led rather than governed by a formally documented approval policy. External contributions generally receive feedback before being merged.
* **Build checks:** {% tool "github_actions" %} installs the project dependencies and verifies that the Jekyll site builds successfully. This catches configuration and compilation failures before changes are released. The project also uses workflows for releases, maintenance of country data, and repository statistics.
* **Testing:** The public repository does not document a broader automated unit, integration, visual-regression, or accessibility test suite. A successful build therefore does not guarantee that layouts, responsive behaviour, or navigation remain visually correct.
* **Releases:** Versions are published as Ruby gems through an automated release workflow. Major releases are used for potentially breaking changes, which are explained in release notes.
* **Adopter feedback:** Issues found in adopter sites can lead to changes in the shared theme, allowing a fix or feature developed for one project to benefit the wider community.

Accessibility is assessed through community review using WCAG guidance, W3C and UK government checklists, and online accessibility tools. The project aims to meet WCAG 2.1 AA and states that its documentation site is compliant as far as its maintainers can ascertain, but it has not documented an independent specialist audit.

These practices provide a lightweight mechanism for maintaining shared infrastructure. The main opportunity for improvement is to complement build checks with automated tests for visual changes, links, navigation, structured metadata, and accessibility regressions.

## Developer Community

### Lowering the barrier to adoption through a minimal example repository and task-oriented documentation

The recommended route for a new adopter is the `elixir-toolkit-theme-example` repository. This repository contains a small working site with the configuration, content, data files, and deployment workflow needed to begin using the theme.

Its main purpose is to demonstrate the separation between an adopter’s content and the shared theme. The adopter repository remains relatively small and is not cluttered with copies of layouts, styles, or scripts. Improvements can instead be received by updating the versioned theme dependency.

A typical adoption journey is:

1. Create a repository from the example project.
2. Enable deployment through GitHub Actions or GitHub Pages.
3. Replace the example content and configuration.
4. Configure navigation, branding, contributors, and resources.
5. Pin a theme version and test future upgrades before adopting them.

New content contributors can work mainly in Markdown and YAML. Developers wishing to change the shared components need to understand Jekyll, Liquid, SCSS, JavaScript, and the relationship between the theme and its plugin package.

The main onboarding difficulty is choosing between the available deployment methods. GitHub Pages provides the simplest route but cannot execute the custom tool-tagging plugin. Projects needing the complete feature set must use GitHub Actions or a gem-based deployment.

The example repository and documentation reduce this complexity, but a short architectural overview explaining the theme, plugin, adopter repository, and deployment options together would make the developer on-ramp clearer.

## Tools

### Using a small toolchain for development, packaging, deployment, and archival

The project uses a focused set of tools rather than a complex development platform:

* **{% tool "github" %} and {% tool "git" %}:** Source control, issues, pull requests, documentation, and release management.
* **{% tool "github_actions" %}:** Automated builds, deployment, maintenance workflows, and publication of releases.
* **Ruby, {% tool "bundler" %}, and RubyGems:** Dependency management, local development, packaging, and distribution.
* **Jekyll:** Generation of static HTML websites from Markdown, YAML, and templates.
* **{% tool "docker" %}:** An alternative local development environment for contributors who do not want to manage a Ruby installation.
* **{% tool "zenodo" %}:** Archival of versioned releases and assignment of persistent identifiers.

The theme can be consumed either as a remote GitHub theme or as a Ruby gem. GitHub Pages is the quickest deployment route but has restricted plugin support. {% tool "github_actions" %}, {% tool "gitlab-pages" %}, and other gem-based workflows provide greater control and access to the full feature set.

Adopter sites are encouraged to pin a specific release rather than automatically using the latest version. This makes deployments more reproducible and allows breaking changes to be reviewed and tested before an upgrade.

## FAIR & Open

### Making the software findable, accessible, interoperable, and reusable through open development

The ELIXIR Toolkit Theme is publicly developed and distributed under the MIT licence. Its source, documentation, issue tracker, example implementation, and releases are openly available.

* **Findable:** The software can be found through its GitHub repository, RubyGems package, documentation website, and Zenodo records. It is also referenced in the RDMkit paper and by adopter projects. Version 6.1.0 has a version-specific Zenodo DOI, `10.5281/zenodo.20816600`.
* **Accessible:** Source code and documentation can be accessed without authentication. The generated output is static HTML, CSS, and JavaScript and can be hosted by a range of providers rather than depending on a dedicated service run by the theme maintainers.
* **Interoperable:** The theme uses established formats and web standards, including Markdown, YAML, HTML, CSS, JavaScript, URLs, sitemaps, and schema.org attributes. Structured resource records can include identifiers and links to external ELIXIR services.
* **Reusable:** The MIT licence permits reuse and modification. The remote-theme and Ruby-gem distribution models allow adopters to keep content separate from shared functionality and to receive upstream improvements without maintaining a complete fork.

Open issues and pull requests also make parts of the development process visible to adopters. However, the absence of a documented governance process means that openness of the code does not yet correspond to fully distributed decision-making.

The project targets WCAG 2.1 AA and documents how its community assesses accessibility. This is a development target and community assessment rather than formal certification.

## Documentation

### Helping adopters configure their sites without having to understand the complete theme codebase

Documentation is provided through several complementary entry points:

* **Repository README:** Introduces the theme, its features, dependencies, installation methods, deployment choices, known users, and licence.
* **Documentation website:** Covers navigation, configuration, branding, page mechanics, website sections, tools and resources, metadata, and accessibility.
* **Example repository:** Provides a minimal working implementation that can be copied and adapted.
* **Markdown guidance:** Supports content contributors who do not need to work with templates or application code.

The documentation website is itself built using the theme, giving users a live example of its navigation, layout, metadata, and content features.

Documentation is central to the software’s reuse model. Adopters are expected to configure a shared dependency rather than copy its source, so they need clear explanations of configuration keys, YAML structures, deployment choices, and compatibility changes.

The most useful additions would be a concise architectural overview, clearer migration guidance for major releases, and a single comparison of the functionality supported by GitHub Pages, GitHub Actions, and gem-based deployments.

## Sustainability

### Balancing broad adoption and a low-maintenance architecture against concentrated maintainer responsibility

The theme was initially developed through RDMkit and the ELIXIR CONVERGE project and continues to be maintained through ELIXIR Belgium activities and related collaborations. Its growing adoption provides a continuing source of requirements, testing, and motivation for further development.

Several technical choices support sustainability. Static sites have a relatively low operational burden because they do not require a continuously running application server or database. The use of Jekyll, Git, Markdown, YAML, and standard web technologies also makes the codebase accessible to developers outside the original team.

The separation of adopter content from the shared theme provides an additional benefit. Fixes and improvements can be implemented once and distributed through a versioned release rather than reproduced independently across every site.

The main sustainability risk is organisational rather than technical. Detailed knowledge, release management, and technical direction remain concentrated in one principal maintainer. Although the software is openly licensed and other developers contribute changes and feedback, there is no publicly documented succession process or shared governance model.

Long-term sustainability would benefit from:

* additional maintainers with release permissions;
* documented technical and governance responsibilities;
* participation by major adopters in roadmap discussions;
* clearer migration and compatibility policies;
* broader automated testing;
* a documented continuity and succession plan.

The theme’s wide use creates a strong incentive for its continued maintenance, but also raises the consequences of disruption. Its future therefore depends on converting a broad user community into a broader maintenance and governance community.

## References

The project is shaped by its source repositories, documentation, the RDMkit use case, established web technologies, and relevant accessibility and metadata standards.

* **Main repository:** [ELIXIR-Belgium/elixir-toolkit-theme](https://github.com/ELIXIR-Belgium/elixir-toolkit-theme)
* **Plugin package:** [ELIXIR-Belgium/elixir-toolkit-theme-plugins](https://github.com/ELIXIR-Belgium/elixir-toolkit-theme-plugins)
* **Example repository:** [ELIXIR-Belgium/elixir-toolkit-theme-example](https://github.com/ELIXIR-Belgium/elixir-toolkit-theme-example)
* **Documentation:** [ELIXIR Toolkit Theme documentation](https://elixir-belgium.github.io/elixir-toolkit-theme)
* **Archived release:** Droesbeke, B. et al. (2026). *ELIXIR-Belgium/elixir-toolkit-theme: 6.1.0*. Zenodo. DOI: [10.5281/zenodo.20816600](https://doi.org/10.5281/zenodo.20816600)
* **RDMkit paper:** Alper, P., D'Anna, F., Droesbeke, B., Andrabi, M. et al. (2025). *RDMkit: A research data management toolkit for life sciences*. Patterns, 6(9), 101345. DOI: [10.1016/j.patter.2025.101345](https://doi.org/10.1016/j.patter.2025.101345)
* **Themes considered during development:** [Jekyll Documentation Theme](https://idratherbewriting.com/documentation-theme-jekyll/) and [Just the Docs](https://github.com/just-the-docs/just-the-docs)
* **Core framework:** [Jekyll](https://jekyllrb.com/) and [Bootstrap](https://getbootstrap.com/)
* **Accessibility standard:** [Web Content Accessibility Guidelines 2.1](https://www.w3.org/TR/WCAG21/)
* **Structured metadata:** [Schema.org](https://schema.org/) and [Bioschemas](https://bioschemas.org/)

* Bioschemas:
  https://bioschemas.org

**ELIXIR resources integrated with the theme:**

* bio.tools:
  https://bio.tools
* FAIRsharing:
  https://fairsharing.org
* FAIR Cookbook:
  https://faircookbook.elixir-europe.org
* RDMkit:
  https://rdmkit.elixir-europe.org
* TeSS:
  https://tess.elixir-europe.org
* Data Stewardship Wizard:
  https://ds-wizard.org
