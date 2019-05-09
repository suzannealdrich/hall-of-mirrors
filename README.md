# Hall of Mirrors

> JavaScript Image Gallery for [After Dark]. Hall of Mirrors adds a responsive image gallery using [PhotoSwipe](http://photoswipe.com).

[![Latest NPM version](https://img.shields.io/npm/v/hall-of-mirrors.svg?style=flat-square)](https://www.npmjs.com/package/hall-of-mirrors)
[![NPM downloads per month](https://img.shields.io/npm/dm/hall-of-mirrors.svg?style=flat-square)](https://www.npmjs.com/package/hall-of-mirrors)
[![Minimum After Dark version](https://img.shields.io/badge/dynamic/json.svg?url=https://codeberg.org/vhs/hall-of-mirrors/raw/branch/master/package.json&label=after%20dark&query=$..['after-dark']&colorB=000000&style=flat-square&longCache=false&maxAge=86400)](https://codeberg.org/vhs/after-dark/)
[![WTFPL licensed](https://img.shields.io/npm/l/hall-of-mirrors.svg?style=flat-square&longCache=true)](https://codeberg.org/vhs/hall-of-mirrors/src/branch/master/COPYING)

## Demo

<video controls>
  <source src="https://vhs.keybase.pub/after-dark-hall-of-mirrors-demo.mp4" type="video/mp4">
  <p>Your browser doesn't support HTML5 video. Here is a <a href="https://vhs.keybase.pub/after-dark-hall-of-mirrors-demo.mp4">link to the video</a> instead. Ref: <a href="https://discourse.gitea.io/t/embedding-videos-in-readmes/494">embedding-videos-in-readmes</a></p>
</video>

## Setup

None required, unless you're hosting your site root from a path including a `/` such as `domain.example/blog/`. If so, update the [url data types](https://devdocs.io/css/url) in `default-skin.css` to include the full path. Use the included `bin/urlize` script to facilitate this change.

## Installation

1. Copy the contents of this repository into a directory called `themes/hall-of-mirrors` under the root of your After Dark site.
2. Add `hall-of-mirrors` as a [theme component](https://gohugo.io/themes/theme-components/) to your After Dark site `config.toml`, e.g.

    ```toml
    theme = [
      "hall-of-mirrors",
      "after-dark"
    ]
    ```

3. Add and specify settings for the module in your After Dark site config, e.g.

    ```toml
    [params.modules.hall_of_mirrors]
      enabled = true # Required in version 0.x.x
    ```

4. Create a [Leaf Bundle] for your images and content.
5. [Configure](#configuration) the content to reference the images.
6. Build and deploy your After Dark site.

## Configuration

To display a gallery add the [Page Resources] you wish to display to your [Leaf Bundle] and configure your front matter as shown.

### Minimal

Display a gallery for all JPEG images in the page bundle:

```toml
[[resources]]
  src = "**.jpg" # Display any jpeg image in the leaf bundle
  name = "gallery" # Name must include the word 'gallery'
```

Display a gallery for images in a specific bundle subdirectory:

```toml
[[resources]]
  src = "images/gallery/**.jpg" # Restrict images to a folder
  name = "Image gallery" # Provide a more friendly gallery name
```

### Extended

Add captions and enhance SEO by configuring individual resources:

```toml
[[resources]]
  src = "**/ray-hennessy-763310-unsplash.jpg"
  [resources.params]
    thumb_size = "750x" # Adjust size of thumbnail image
  [resources.params.meta]
    creator = "Ray Hennessy"
    description = "This is a long description. It is shown instead of the title and is intended to provide more information."

[[resources]]
  src = "**sprat**" # Glob for image with 'sprat' in the filename
  title = "Diverse succulents around a rock"
  [resources.params]
    hide_credits = true # Display title but not creator
  [resources.params.meta]
    creator = "Annie Spratt" # Maps to schema structured data

[[resources]]
  src = "**/blake-richard-verdoorn-20063-unsplash.jpg"
  title = "Bridge over a green waterfall"
  [resources.params]
    hide_credits = true
    thumb_size = "350x"
  [resources.params.meta]
    creator = "Blake Richard Verdoorn"
    keywords = ["nature", "waterfall", "bridge"]

[[resources]]
  src = "images/gallery/**.jpg"
  name = "Nature gallery"
  [resources.params.meta]
    genre = "digital" # Set genre meta for all gallery images
```

This should get you started. Expect some breaking changes as the development is finalized.

## Contributing

Please squash commits and use [Convention Commit](https://www.conventionalcommits.org/) messages. Run `npm run commit` after installing NPM dev dependencies for help creating conventional commit messages.k

## Rights

Copyright (C) 2018, 2019 by VHS <0xc000007b@tutanota.com>

Permission to use, copy, modify, and/or distribute this software for any purpose with or without fee is hereby granted.

The text of the above license is included in the file COPYING in the source.

[After Dark]: https://codeberg.org/vhs/after-dark/
[Leaf Bundle]: https://gohugo.io/content-management/page-bundles/#leaf-bundles
[Page Resources]: https://gohugo.io/content-management/page-resources/
