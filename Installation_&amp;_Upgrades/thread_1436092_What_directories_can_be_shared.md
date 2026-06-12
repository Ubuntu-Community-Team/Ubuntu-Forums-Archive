---
title: "What directories can be shared?"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by goseph on 2010-03-22
Hi everyone!

I have a shared /home between windows, Ubuntu and a couple of alternative Gnu/Linux installs.

Are there any other directories that can safely/easily share a partition?

Can I have my installed programs available to me in any distro if, for example, I share lib and usr and etc ?

Thanks!

---

### Post by oldfred on 2010-03-22
You should only share data directories with other systems. Each system may write settings that are not compatible with another system. You cannot share /home with windows.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

