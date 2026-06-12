---
title: "Installing gnome-shell extensions in 20.04?"
date: 2020-05-09
forum: Installation &amp; Upgrades
---

### Post by curts on 2020-05-09
In 18.04, the "correct" way to install gnome-shell extensions was to use the Ubuntu Software app. Currently, no extensions are listed in Ubuntu Software (at least that I can find after numerous search attempts). In the 18.04 Ubuntu Software app there was a dedicated section for extensions.

By installing Synaptic, I was able to find a handful of gnome-shell-extension-* packages that install at the OS level, of which I have installed three favorites. But there are several other extensions I like to use that have traditionally installed at the user level, e.g. QuickLaunch.

For 20.04, is the plan to expand the Ubuntu Software app soon to include gnome-shell extensions, or are we reverting back to the web interface ([https://extensions.gnome.org/](https://extensions.gnome.org/)) for user installed extensions?

---

### Post by Dennis N on 2020-05-09
If you open the new Extensions application for managing extensions, the directions for installing are to use the extensions web site (see attached notice). Once installed, you can manage from the Extensions application (including removal).

Note: This now creates a problem if you use the Firefox snap package. It cannot install extensions using the website (as far as I can tell) because it cannot detect the "native host connector" (chrome-gnome shell). The old work-around for this was to use Ubuntu Software.

---

### Post by curts on 2020-05-09
Thanks for that. I had not clicked on the "i" info button to reveal that message. Not very intuitive.

---

