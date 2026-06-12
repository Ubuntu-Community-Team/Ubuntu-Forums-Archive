---
title: "Software updater doesn't start up"
date: 2014-07-04
forum: Installation &amp; Upgrades
---

### Post by Krabun on 2014-07-04
Message:

Failed to load the package list

W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages), E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_i18n_Translation-en%%5fUS, E:The package lists or status file could not be parsed or opened.

On th forum I found this advice:
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade


But it didn't work. Someone else a suggestion?

---

### Post by Bucky Ball on 2014-07-04
The Spotify repository appears to be down. There are a number of support requests regarding it.

Go Software Updater>Settings button in bottom left corner>Other Software, and untick the Spotify repo. Update as per normal.

Try adding the Spotify repo in twenty four hours.

---

### Post by Krabun on 2014-07-04
Thanks for the quick answer. Everything's all right now.

---

