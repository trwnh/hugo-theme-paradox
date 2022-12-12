# hugo-theme-paradox

Paradox is a theme for Hugo intended documentation sites.

## Features and recommendations

### config.toml

general config settings you might want to use

```toml
baseURL = 'https://docs.pixelfed.org/'
languageCode = 'en-us'
title = 'Pixelfed Documentation'
theme = 'paradox'
defaultContentLanguage = 'en'
enableGitInfo = true

disableKinds = ["taxonomy"]
ignoreErrors = ["error-disable-taxonomy"]

[languages]
[languages.en]
contentDir = 'content/en'
languageName = 'English'
weight = 1

[frontmatter]
lastmod = ["lastmod", ":git", "date", "publishDate"]

[markup.tableOfContents]
ordered = true

[markup.goldmark.renderer]
unsafe = true

[markup.highlight]
codeFences = true
lineNumbersInTable = false
tabWidth = 3
noClasses = false
```

To get search working:

```toml
[outputs]
home = ["HTML", "RSS", "JSON"]
page = ["HTML"]
```

Theme-specific features and parameters:

```toml
[params]
icon = "https://avatars0.githubusercontent.com/u/38410642?s=200&amp;v=4"
title = "Pixelfed documentation"  # sets the header title separately from metadata (may be removed in the future? idk if the top-level title should always be the same)
forge = "github" # github, gitea
# forgeUrl = "https://git.trwnh.com"  # if set to gitea
repo = "pixelfed/docs"  # the path to the repo
branch = "main"  # the branch to use for edits
autonumbering = true  # global default for whether to autonumber section headings (can also be used on a per-page level via frontmatter params)
# borders = true  # whether to use borders to separate the layout
```

main menu (goes in header for now)

```toml
[menu]
[[menu.main]]
identifier = 'pixelfed'
name = 'pixelfed.org'
url = 'https://pixelfed.org'
weight = 10
pre = '<img src="https://avatars0.githubusercontent.com/u/38410642?s=200&amp;v=4" height="24">'

[[menu.main]]
identifier = 'github'
name = 'pixelfed/docs'
url = 'https://github.com/pixelfed/docs'
weight = 20
pre = '<svg style="background:white; border: 1px solid white; border-radius: 100rem;" height="1.5rem" viewBox="0 0 1024 1024" fill="none" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" clip-rule="evenodd" d="M8 0C3.58 0 0 3.58 0 8C0 11.54 2.29 14.53 5.47 15.59C5.87 15.66 6.02 15.42 6.02 15.21C6.02 15.02 6.01 14.39 6.01 13.72C4 14.09 3.48 13.23 3.32 12.78C3.23 12.55 2.84 11.84 2.5 11.65C2.22 11.5 1.82 11.13 2.49 11.12C3.12 11.11 3.57 11.7 3.72 11.94C4.44 13.15 5.59 12.81 6.05 12.6C6.12 12.08 6.33 11.73 6.56 11.53C4.78 11.33 2.92 10.64 2.92 7.58C2.92 6.71 3.23 5.99 3.74 5.43C3.66 5.23 3.38 4.41 3.82 3.31C3.82 3.31 4.49 3.1 6.02 4.13C6.66 3.95 7.34 3.86 8.02 3.86C8.7 3.86 9.38 3.95 10.02 4.13C11.55 3.09 12.22 3.31 12.22 3.31C12.66 4.41 12.38 5.23 12.3 5.43C12.81 5.99 13.12 6.7 13.12 7.58C13.12 10.65 11.25 11.33 9.47 11.53C9.76 11.78 10.01 12.26 10.01 13.01C10.01 14.08 10 14.94 10 15.21C10 15.42 10.15 15.67 10.55 15.59C13.71 14.53 16 11.53 16 8C16 3.58 12.42 0 8 0Z" transform="scale(64)" fill="#1B1F23"/></svg>'
```

you can also put a simple/short menu in the footer (currently intended for attribution info)

```toml
[[menu.footer]]
identifier = "copyright"
name = "CC BY-SA 4.0"
url = "https://creativecommons.org/licenses/by-sa/4.0/"
weight = 10
pre = '<span style="color: var(--ui-text-bold)"><i class="fa fa-cc-cc"></i><i class="fa fa-cc-by"></i><i class="fa fa-cc-sa"></i></span>'
```

next to the footer menu there is a social menu intended for icon links

```toml
[[menu.social]]
identifier = "mastodon"
pre = '<svg height="1em" viewbox="0 0 75 79" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M73.84 17.49C72.696 9.002 65.3 2.312 56.53 1.016 55.05.797 49.444 0 36.458 0h-.097c-12.99 0-15.776.797-17.256 1.016-8.525 1.26-16.311 7.271-18.2 15.86-.909 4.23-1.006 8.919-.837 13.22.24 6.17.288 12.327.848 18.47a86.879 86.879 0 0 0 2.022 12.115c1.795 7.361 9.064 13.487 16.185 15.986a43.41 43.41 0 0 0 23.68 1.25 34.565 34.565 0 0 0 2.562-.701c1.91-.607 4.147-1.285 5.792-2.477a.187.187 0 0 0 .076-.144v-5.953a.175.175 0 0 0-.216-.17 65.637 65.637 0 0 1-15.367 1.796c-8.906 0-11.301-4.226-11.987-5.985a18.554 18.554 0 0 1-1.042-4.718.171.171 0 0 1 .136-.178.173.173 0 0 1 .08.002 64.383 64.383 0 0 0 15.115 1.795c1.225 0 2.446 0 3.67-.032 5.121-.144 10.52-.406 15.558-1.39.125-.025.251-.047.359-.079 7.947-1.526 15.51-6.316 16.279-18.445.029-.477.1-5.002.1-5.497.004-1.684.543-11.946-.079-18.251Z" fill="url(#a)"/><path d="M61.248 27.026v21.088h-8.356V27.648c0-4.31-1.796-6.507-5.448-6.507-4.015 0-6.026 2.6-6.026 7.735v11.202H33.11V28.875c0-5.134-2.014-7.734-6.03-7.734-3.63 0-5.444 2.198-5.444 6.507v20.466h-8.353V27.026c0-4.308 1.1-7.731 3.3-10.269 2.27-2.531 5.247-3.831 8.942-3.831 4.278 0 7.51 1.644 9.665 4.93l2.079 3.49 2.083-3.49c2.154-3.286 5.386-4.93 9.657-4.93 3.691 0 6.668 1.3 8.945 3.831 2.198 2.535 3.296 5.958 3.293 10.27Z" fill="#fff"/><defs><linearGradient id="a" x1="37.069" y1="0" x2="37.069" y2="79" gradientUnits="userSpaceOnUse"><stop stop-color="#6364FF"/><stop offset="1" stop-color="#563ACC"/></linearGradient></defs></svg>'
url = "https://mastodon.social/@pixelfed"
weight = 10

[[menu.social]]
identifier = "pixelfed"
pre = '<img src="https://avatars0.githubusercontent.com/u/38410642?s=200&amp;v=4" height=16>'
url = "https://pixelfed.social/pixelfed"
weight = 15

[[menu.social]]
identifier = "twitter"
pre = '<svg xmlns="http://www.w3.org/2000/svg" xml:space="preserve" viewBox="0 0 248 204" height="1em"><path fill="#1d9bf0" d="M221.95 51.29c.15 2.17.15 4.34.15 6.53 0 66.73-50.8 143.69-143.69 143.69v-.04c-27.44.04-54.31-7.82-77.41-22.64 3.99.48 8 .72 12.02.73 22.74.02 44.83-7.61 62.72-21.66-21.61-.41-40.56-14.5-47.18-35.07a50.338 50.338 0 0 0 22.8-.87C27.8 117.2 10.85 96.5 10.85 72.46v-.64a50.18 50.18 0 0 0 22.92 6.32C11.58 63.31 4.74 33.79 18.14 10.71a143.333 143.333 0 0 0 104.08 52.76 50.532 50.532 0 0 1 14.61-48.25c20.34-19.12 52.33-18.14 71.45 2.19 11.31-2.23 22.15-6.38 32.07-12.26a50.69 50.69 0 0 1-22.2 27.93c10.01-1.18 19.79-3.86 29-7.95a102.594 102.594 0 0 1-25.2 26.16z"/></svg>'
url = "https://twitter.com/pixelfed"
weight = 20

[[menu.social]]
identifier = "github"
pre = '<svg style="background:white; border: 1px solid white; border-radius: 100rem;" height="1em" viewBox="0 0 1024 1024" fill="none" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" clip-rule="evenodd" d="M8 0C3.58 0 0 3.58 0 8C0 11.54 2.29 14.53 5.47 15.59C5.87 15.66 6.02 15.42 6.02 15.21C6.02 15.02 6.01 14.39 6.01 13.72C4 14.09 3.48 13.23 3.32 12.78C3.23 12.55 2.84 11.84 2.5 11.65C2.22 11.5 1.82 11.13 2.49 11.12C3.12 11.11 3.57 11.7 3.72 11.94C4.44 13.15 5.59 12.81 6.05 12.6C6.12 12.08 6.33 11.73 6.56 11.53C4.78 11.33 2.92 10.64 2.92 7.58C2.92 6.71 3.23 5.99 3.74 5.43C3.66 5.23 3.38 4.41 3.82 3.31C3.82 3.31 4.49 3.1 6.02 4.13C6.66 3.95 7.34 3.86 8.02 3.86C8.7 3.86 9.38 3.95 10.02 4.13C11.55 3.09 12.22 3.31 12.22 3.31C12.66 4.41 12.38 5.23 12.3 5.43C12.81 5.99 13.12 6.7 13.12 7.58C13.12 10.65 11.25 11.33 9.47 11.53C9.76 11.78 10.01 12.26 10.01 13.01C10.01 14.08 10 14.94 10 15.21C10 15.42 10.15 15.67 10.55 15.59C13.71 14.53 16 11.53 16 8C16 3.58 12.42 0 8 0Z" transform="scale(64)" fill="#1B1F23"/></svg>'
url = "https://github.com/pixelfed/pixelfed"
weight = 30
```

### frontmatter

anything put in the docs menu will be available as in the big beefy menu section (which becomes a sidebar when the page is wide enough)

```toml
title = "Generic installation guide"
summary = "How to set up everything you need to run your own Pixelfed instance."
weight = 20
[menu]
[menu.docs]
identifier = "admin/installation"
parent = "admin"
```