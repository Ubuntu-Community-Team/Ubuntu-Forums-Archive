---
title: "Can't upgrade from 18.04 to 18.10"
date: 2018-10-22
forum: Installation &amp; Upgrades
---

### Post by farukdgn on 2018-10-22
[FONT=arial]When I try to execute *do-release-upgrade*, this error shows up: > Failed to connect to [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release). Check your Internet connection or proxy settings I can connect to this address from Chrome.[/FONT]

Ubuntu: 18.04.1[FONT=monospace]
[/FONT][FONT=arial]Kernel: [/FONT][FONT=monospace][FONT=arial][COLOR=#000000]4.15.0-36-generic
Python: 3.6.6
[/COLOR][/FONT]
[/FONT]

---

### Post by dino99 on 2018-10-22
you can also manually update /etc/apt/sources.list to point to cosmic instaed of bionic; then update, upgrade.

---

### Post by farukdgn on 2018-10-24
I didn't know what to change in sources.list (and I heard you should disable third party sources) and there wasn't a documentation about it.

I found a workaround and posted here: [https://askubuntu.com/a/1086496/403301](https://askubuntu.com/a/1086496/403301)

---

