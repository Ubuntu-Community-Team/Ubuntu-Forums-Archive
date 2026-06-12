---
title: "gnome-shell extensions connector not working"
date: 2020-05-12
forum: Installation &amp; Upgrades
---

### Post by curts on 2020-05-12
Despite the package chrome-gnome-shell being installed in 20.04, the gnome-shell extensions connector is not working. It does not install the Chromium extension required to use extensions.gnome.org for installing user extensions. Reviewing the files included in the package, /usr/share/doc/chrome-gnome-shell/README.Debian advises the Chromium browser extension must be manually installed. I installed the 'GNOME Shell integration' browser extension, but i get the following in-browser error when visiting extensions.gnome.org:

```
Although GNOME Shell integration extension is running, native host connector is not detected. Refer documentation for instructions about installing connector.
```

There would appear to be a problem with the connector installed by the package chrome-gnome-shell.

I have not attempted to create my own build of the connector, per wiki.gnome.org (i.e. the documentation link in the above error message):
[https://wiki.gnome.org/Projects/GnomeShellIntegrationForChrome/Installation#Ubuntu_Linux](https://wiki.gnome.org/Projects/GnomeShellIntegrationForChrome/Installation#Ubuntu_Linux)

---

### Post by Dennis N on 2020-05-12
Snap browsers (Chromium and Firefox) cannot use the gnome-shell integration. I imagine it's part of the security design? You can use the standard Firefox (repository version installed with the OS) to install gnome-shell extensions from the gnome extensions web site.

---

### Post by curts on 2020-05-12
Confirmed, connector is working with the OS installed version of Firefox after installing the browser extension.  :D  I would not have guessed this, since the more recent emphasis has been on the Chromium browser integration, hence my query.

This needs to be documented somewhere, like the release notes (hint, hint). I did look there first.

---

