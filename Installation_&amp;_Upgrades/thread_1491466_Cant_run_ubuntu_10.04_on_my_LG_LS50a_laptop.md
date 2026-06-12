---
title: "Cant run ubuntu 10.04 on my LG LS50a laptop"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by whitefish10 on 2010-05-23
Hi guys, I have a an old laptop (LG LS50a) that I use to install Linux distributions to test them, I did install fedora 11, 12 etc. But when ever I want to install any ubuntu version 9.1 or 10.04 on this machine it give me a blank screen (that is after I select from the menu to install ubuntu). I figure out that the display driver may not be present on the disk, so I install ubuntu using the alternative media disk but again I cant pass to see the GUI desktop.


Please help me guys, as I am out of options.

---

### Post by davidmohammed on 2010-05-23
please can you confirm your graphics card - ati?

see this [thread]("http://ubuntuforums.org/showpost.php?p=9345983&postcount=8") - does it help?

---

### Post by spcwingo on 2010-05-23
You could give the alternate install CD a try:

[http://www.ubuntulinux.org/getubuntu/downloadmirrors#alternate]("http://www.ubuntulinux.org/getubuntu/downloadmirrors#alternate")

---

### Post by whitefish10 on 2010-05-24
The graphic card that I have is from Intel, sorry I didn't mention it before.

> **spcwingo said:**
> You could give the alternate install CD a try:

[http://www.ubuntulinux.org/getubuntu/downloadmirrors#alternate](http://www.ubuntulinux.org/getubuntu/downloadmirrors#alternate)

I mentioned before also that I did the installation using the alternative disk, but I cant see the gnome gui after booting.

---

### Post by davidmohammed on 2010-05-24
... have you tried the tricks described in this [thread]("http://ubuntuforums.org/showthread.php?t=1488699")?

try i915.modeset=1 if you got a i8xxx type intel graphics  or i915.modeset=0 if you have got a i9xxx type intel graphics in your grub boot setting.

---

### Post by sidkapoor on 2010-09-13
has this problem been solved at all? if it has could someone tell me how. I am having the exact same problem.

Thanks

---

