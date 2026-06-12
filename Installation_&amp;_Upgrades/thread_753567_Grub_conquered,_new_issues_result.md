---
title: "Grub conquered, new issues result"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by ikedaman on 2008-04-12
After two days, I now have two of my three operating systems working, the details of how can be seen here: [http://ubuntuforums.org/showthread.php?t=753269]("http://ubuntuforums.org/showthread.php?t=753269").  Windows and Ubuntu are up and running now that GRUB is set up.  64 Studio, my other operating system is close but not quite cooperating.  Grub can find it, but before it can load all the way, I get the penguin and this is down at the bottom of the list:

```
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

BusyBox v1.1.3 (Debian 1:1.1.3-4) Built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh: can't access tty; job control turned off
(initramfs)
```

---

