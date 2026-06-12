---
title: "Unetbootin &quot;Unable to find a medium containing a live file system&quot;"
date: 2013-05-27
forum: Installation &amp; Upgrades
---

### Post by scottbomb on 2013-05-27
I downloaded the daily test ISO image for Saucy and used Unetbootin to create a bootable USB stick. I do this fairly regularly with no problem. Today all of a sudden, it won't work. I get this error after rebooting:

```
BusyBox v1.20.2 (Ubuntu 1:1.20.0-8ubuntu1) built in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) Unable to find a medium containing a live file system
```

I've googled this and there are some old, outdated threads where people seem to have "fixed" it with no real solution. In one case, someone had a corrupt file. I checked the MD5 and it's good. In another case, someone removed the drive and re-inserted it when the screen showed the Xubuntu splash but that didn't work for me.  I formatted the thumb drive to FAT32 and tried again. Still no dice. The machine is an IBM Thinkpad T60, 32 bit.

---

### Post by TenPlus1 on 2013-05-28
I had the same error and formatted the flash drive and tried again without creating a persistence file and it worked...

---

