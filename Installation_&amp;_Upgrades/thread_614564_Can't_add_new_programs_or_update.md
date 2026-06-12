---
title: "Can't add new programs or update"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by woolyghost on 2007-11-16
Hi, Ive just installed Gusty Gibbon, everything seems to work ok but whenever I try to add a program from the menu or select to install updates I get an Error.

The packages download ok but then when the try to install I get this: 

E: /var/cache/apt/archives/thunderbird_2.0.0.8~pre071022+nobinonly-0ubuntu0.7.10_i386.deb: unable to open files list file for package `x11proto-render-dev'

In the terminal it says:

(Reading database ... dpkg: error processing /tmp/x11proto-render-dev_0.9.3-2_all.deb (--install):
unable to open files list for package 'x11proto-render-dev': Input/output error

The same thing happens when I try to install any update:

E: /var/cache/apt/archives/smbclient_3.0.26a-1ubuntu2.1_i386.deb: unable to open files list file for package `x11proto-render-dev'

The terminal is the same. It dose not seem to matter what I try to install so I think the problem must be on my system.

---

### Post by climatewarrior on 2007-11-16
Go to System/Administration/Software Sources

here make shure that the following repositories are checked

Canonical supported open source software
Community supported open source software

I put an example in the attahcment

also make shure that the get software from the gutsy cd is unchecked

---

### Post by woolyghost on 2007-11-16
Thank  for your speedy advice, but iv'e done what you said and its no different.

I think the problem might be somthing to do with x11proto-render-dev file. Dose anyone know what this is?

---

### Post by climatewarrior on 2007-11-18
I dont have the slighest idea of what that means. You might want to try to get support for that problem here. [https://answers.launchpad.net/ubuntu](https://answers.launchpad.net/ubuntu)

---

