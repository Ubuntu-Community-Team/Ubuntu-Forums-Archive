---
title: "reset Master Boot Record"
date: 2006-03-06
forum: Installation &amp; Upgrades
---

### Post by SVFUSiON on 2006-03-06
how can I reset my MBR?
Thanks, svfusion.

---

### Post by evilgold on 2006-03-06
Every OS should have a utility to reinstall the boot loader on its install CD. I've never done it with ubuntu before, but if you navigate the installation menu and jus skip to the install grub/lilo part, that should work.

I think you might also be able to run "grub-install /dev/hda" from a live cd aslo, which might be easier

---

### Post by freedomforme on 2006-03-06
shouldnt need to "reset" it. What ya doin anyway?

---

### Post by SVFUSiON on 2006-03-06
Lilo is installed somewhere and I can not find where it is so maby it is in my MBR?

---

### Post by evilgold on 2006-03-06
[QUOTE=SVFUSiON]Lilo is installed somewhere and I can not find where it is so maby it is in my MBR?[/QUOTE]

Yes lilo would be on your MBR. you can reinstall it using an ubuntu cd....what exactly are you trying to accomplish? is lilo not working correctly?

---

### Post by aysiu on 2006-03-06
As far as I know, Ubuntu doesn't use Lilo, but here are some instructions for how to restore Grub to the MBR:
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

