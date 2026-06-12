---
title: "mount options with grub/kernel?"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by exp(x) on 2007-11-03
I just rebuilt my system, but I'm having a hard time booting up. I got the kernel to load, but I can't mount the root file system and get the following error:
```
mount: Mounting /dev/md1 on /root failed: Invalid argument
```
I can manually mount the file system from the busybox console that comes up, but because I tweaked the log buffer settings, I need to specify a few options. Is there a way to specify these mount options in grub's menu.lst, or is there some other way to let the kernel know? I've spent some time searching google and looking at the grub manual, but I can't figure it out.

---

### Post by exp(x) on 2007-11-03
I was searching google some more and discovered the rootflags parameter. This solved my problem.

---

