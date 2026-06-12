---
title: "Dual-boot GRUB Error 22"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by whiterabbit7500 on 2007-09-02
Trying to install Ubuntu on a new SATA HD, and have a dual-boot screen with Windows XP (on a IDE). New SATA drive is unformatted, brand new. It tells me it installed it fine, but when I try to boot, it tells me "Grub error 22". I've looked into trying to reload GRUB, but I guess I'm too much of a n00b for this still. Do I have to pre-format the new drive? how do I do this through the Live CD? PLEASE HELP!

---

### Post by Pumalite on 2007-09-02
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by whiterabbit7500 on 2007-09-02
thanks for the link, lots of good info...but

still cant get it to work right. i downloaded SuperGRUB disk, burned it to CD, tried t boot windows from it...started to work good, but got blue screen of death. good news? no more GRUB error 22...but blue screen of death now! do i have to reinstall windows?

current setup:
HD1: Windows XP Pro (IDE)
HD2: Data Files (IDE)
HD3: Program Files (SATA)
HD4: Linux (SATA)

Ubuntu claims it installed ok, but even when i choose to boot HD4, it says error loading operating system...

someone please help...i need at least windows back and working!!!

---

### Post by Pumalite on 2007-09-02
[http://supergrub.forjamari.linex.org/?section=documentation](http://supergrub.forjamari.linex.org/?section=documentation)

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/721404.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/721404.html)

You can restore Windows MBR with XP CD:
'r' for Recovery>FIXMBR>FIXBOOT
Later you can re-install Grub with this:[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by whiterabbit7500 on 2007-09-02
and i'm looking for?

---

### Post by Pumalite on 2007-09-02
See my editing above.

---

