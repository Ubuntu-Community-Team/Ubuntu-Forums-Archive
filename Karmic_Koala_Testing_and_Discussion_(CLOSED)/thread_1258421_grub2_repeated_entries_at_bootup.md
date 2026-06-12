---
title: "grub2 repeated entries at bootup"
date: 2009-09-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cornflake000 on 2009-09-05
I have a pretty good handle on the old grub.  I've been running multiple operating systems and testing them for years without a hitch.  Usually I have 4 or 5 running on 1 machine. I decided to go ahead with grub2 but now my boot menu shows 2 operating systems that don't exist anymore on partitions that also don't exist.  It also shows 6 repeated entries for one jaunty64 installation and 6 entries for one karmic installation.  Then it shows the same jaunty64 installation and again the same karmic installation just worded differently. 

Hmmm. If that happened in the old grub I'd just check the usual menu.lst etc. etc.  and knock a few things around.  But of course you don't do that now.  The only reference to any os's are in the "untouchable" boot/grub/grub.cfg but no other references are found in the /etc/grub.d files.  Updating grub2 only refreshes the same thing.

Anyone have a handle on this?  How can I adjust the menu that I "mustn't" edit?  Sorry... this is a little weird to me.

thanks

---

### Post by dino99 on 2009-09-05
hi,
i never had this issue. Have you 1 grub2 for all your distro or 1 for each ?
I suppose you have upgraded your old grub-legacy to this new grub-pc named grub2 (actual 1,97 beta1): have you followed the process to validate the 1st install ? (that definitevely drop menu.list)

anyway, run these command:
- sudo apt-get os-prober
- sudo apt-get update-grub2
- sudo apt-get mkconfig

best read: [https://wiki.edubuntu.org/Grub2](https://wiki.edubuntu.org/Grub2)
                [http://gastly.iblogger.org/how-to-install-grub2-on-ubuntu-jaunty/](http://gastly.iblogger.org/how-to-install-grub2-on-ubuntu-jaunty/)
                [https://wiki.ubuntu.com/KernelTeam/Grub2Testing](https://wiki.ubuntu.com/KernelTeam/Grub2Testing)

---

