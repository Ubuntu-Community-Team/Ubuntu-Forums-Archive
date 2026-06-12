---
title: "Lubuntu chrome browser install"
date: 2020-01-18
forum: Installation &amp; Upgrades
---

### Post by cam17 on 2020-01-18
Is there a chrome browser installation through discovery ? I do not see any browser for Lubuntu but it exists for Ubuntu.

---

### Post by guiverc on 2020-01-18
This question reminds me of [https://discourse.lubuntu.me/t/chrome-browser-in-discover/700/](https://discourse.lubuntu.me/t/chrome-browser-in-discover/700/)

You haven't given your release details, but [https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=chromium-browser](https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=chromium-browser) shows the chromium-browser is available for all supported releases in the 'universe' repository ([https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)) which is enabled by default in Lubuntu.

I opened `discover` on my Lubuntu, and see a list of nine (9) browsers available in `discover`  (internet->Web Browsers).  From 19.10 on, `chromium-browser` is provided as a snap package, though it can be installed as a deb package too (which will cause the snap to be installed).

Google chrome is not open source, so does not appear by default in any Ubuntu. The google repository must be manually added to your system before the google packages appear, eg. I must have added it to my system sometime, as 

```
guiverc@d960-ubu2:/de2900/lubuntu_64$   apt-cache search chrom |grep browser
browser-plugin-freshplayer-pepperflash - PPAPI-host NPAPI-plugin adapter for pepperflash
pepperflashplugin-nonfree - Pepper Flash Player - browser plugin
chrome-gnome-shell - GNOME Shell extensions integration for web browsers
chromium-browser - Transitional package - chromium-browser -> chromium snap
chromium-browser-l10n - Transitional package - chromium-browser-l10n -> chromium snap
epiphany-browser - Intuitive GNOME web browser
gnome-shell-extension-gsconnect-browsers - Browser support of KDE Connect implementation for GNOME Shell
plasma-browser-integration - Chromium, Google Chrome, Firefox integration for Plasma
webext-browserpass - web extension for the password manager pass
google-chrome-beta - The web browser from Google
google-chrome-stable - The web browser from Google
google-chrome-unstable - The web browser from Google
```

has it show. If you used `muon` package manager (installed by default in modern Lubuntu using LXQt) it'll show the packages as shown in my `apt-cache search` (for my release & my added sources anyway).

Discover uses a smaller moderated list of what's available in `muon` (which lists all packages).

---

### Post by cam17 on 2020-01-23
Thank you.

---

