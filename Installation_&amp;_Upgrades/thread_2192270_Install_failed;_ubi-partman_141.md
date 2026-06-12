---
title: "Install failed; ubi-partman 141"
date: 2013-12-07
forum: Installation &amp; Upgrades
---

### Post by foo3 on 2013-12-07
Hello,
I'm trying to install Ubuntu 12.04 via the live CD on an external 3TB drive with GPT currently formatted with NTFS. From the GUI installer, I double clicked on /dev/sdc2 which is the ntfs partition, selected EXT4, check format and set / as the mount point. This produced an error "Ubi-partman failed with exit code 141..."(see attached for full). I've seen the bug report regarding this, but it doesn't seem to apply as this disk doesn't already have Ubuntu on it ... as per the bug 945027 on launchpad "Impact: Installation fails if there are two operating systems on disk with one of them being Ubuntu"

I've attached screen shots of the installer incase that helps. Thanks in advance.

[ATTACH=CONFIG]248401[/ATTACH][ATTACH=CONFIG]248402[/ATTACH][ATTACH=CONFIG]248403[/ATTACH]

---

### Post by heir4c on 2013-12-07
What happen if you use gParted to format the partition in ext4 before you start the installer?

---

