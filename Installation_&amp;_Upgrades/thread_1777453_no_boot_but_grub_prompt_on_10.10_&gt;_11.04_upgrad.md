---
title: "no boot but grub prompt on 10.10 &gt; 11.04 upgrade"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by theoneness on 2011-06-07
Hello all,
I'm running Ubuntu within VMWare on a Macbook. I followed these steps [https://help.ubuntu.com/community/NattyUpgrades#Network Upgrade for Ubuntu Desktops (Recommended)]("https://help.ubuntu.com/community/NattyUpgrades#Network Upgrade for Ubuntu Desktops (Recommended)") to upgrade form 10.04 to 11.04, which actually upgraded to 10.10 first, and then a graphical upgrade brought me to the 11.04 upgrade, but then i ran into the problem where a grub> prompt appears when i start up the machine... nothing else happens.
I found this thread ([http://ubuntuforums.org/showthread.php?t=1391670]("http://ubuntuforums.org/showthread.php?t=1391670")) which seemed similar to my problem, but the suggestions didn't work.

```
grub> ls
(hd0) (hd0,5) (hd0,1) (fd0)

grub> boot
error: no loaded kernel.

grub> linux
error: no kernel specified.
```

that's what I see. any way to resolve this without having to download the CD and start from scratch? It's grub 1.98, if that's important to know. Thanks for any help.

---

### Post by mörgæs on 2011-06-08
You could try this:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

