# [dmenu] for [Chrome]

###### [Chrome](#chrome) | [Firefox](#firefox)

> Tab search with [dmenu].

[![Tab search with dmenu](https://img.youtube.com/vi_webp/tgrmss3u2aE/maxresdefault.webp)](https://youtu.be/tgrmss3u2aE)

## Dependencies

- [Rofi] ([dmenu] replacement)
- [Zip] (Zip is used to package the extension)
- [Inkscape] (Inkscape is used to convert SVG to PNG when uploading the extension)

### Extensions

- [Shell] (Chrome API to execute external commands)

## Installation

### Chrome

#### Installing from the Chrome Web Store

https://chrome.google.com/webstore/detail/dmenu/gonendiemfggilnopogmkafgadobkoeh

#### Installing from the source

``` sh
make chrome
```

Open the _Extensions_ page by navigating to `chrome://extensions`, enable _Developer mode_ then _Load unpacked_ to select the extension directory: `target/chrome`.

![Load extension](https://developer.chrome.com/static/images/get_started/load_extension.png)

See the [Getting Started Tutorial] for more information.

### Firefox

``` sh
make firefox
```

- Open `about:config`, change `xpinstall.signatures.required` to `false`.
- Open `about:addons` ❯ _Extensions_, click _Install add-on from file_ and select the package file: `target/firefox/package.zip`.

#### Developing

Open `about:debugging` ❯ _This Firefox_ ❯ _Temporary extensions_, click _Load temporary add-on_ and select the manifest file: `target/firefox/manifest.json`.

[![Load extension](https://img.youtube.com/vi_webp/cer9EUKegG4/maxresdefault.webp)](https://youtu.be/cer9EUKegG4)

See [Firefox – Your first extension] for more information.

## Usage

Press <kbd>Control</kbd> + <kbd>q</kbd> to tab search with [dmenu].

### Cross-extension messaging

``` javascript
const port = chrome.runtime.connect('gonendiemfggilnopogmkafgadobkoeh') // for a Chrome extension
const port = chrome.runtime.connect('dmenu@alexherbo2.github.com') // for a Firefox extension
port.postMessage({ command: 'tab-search' })
```

More examples can be found [here][Create a keyboard interface to the web].

See [Cross-extension messaging] for more details.

## Configuration

### Chrome

Open `chrome://extensions/configureCommands` to configure the keyboard shortcuts.

### Firefox

Open `about:addons` ❯ _Extensions_ and click _Manage extension shortcuts_ in the menu.

![Manage extension shortcuts](https://user-media-prod-cdn.itsre-sumo.mozilla.net/uploads/gallery/images/2019-02-21-18-47-38-921651.png)

## Commands

- `tab-search` (<kbd>Control</kbd> + <kbd>q</kbd>)

[Chrome]: https://google.com/chrome/
[Chrome Web Store]: https://chrome.google.com/webstore

[Firefox]: https://mozilla.org/firefox/
[Firefox Add-ons]: https://addons.mozilla.org

[dmenu]: https://tools.suckless.org/dmenu/
[Rofi]: https://github.com/davatorium/rofi
[Zip]: http://infozip.sourceforge.net/Zip.html
[Inkscape]: https://inkscape.org

[Shell]: https://github.com/alexherbo2/chrome-shell

[Getting Started Tutorial]: https://developer.chrome.com/extensions/getstarted
[Cross-extension messaging]: https://developer.chrome.com/extensions/messaging#external

[Firefox – Your first extension]: https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/Your_first_WebExtension

[Create a keyboard interface to the web]: https://alexherbo2.github.io/blog/chrome/create-a-keyboard-interface-to-the-web/
