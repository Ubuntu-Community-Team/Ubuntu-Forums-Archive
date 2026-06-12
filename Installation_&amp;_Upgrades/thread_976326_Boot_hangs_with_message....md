---
title: "Boot hangs with message..."
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by stevetc on 2008-11-09
"cannot find root".

I have installed Ubuntu 8.10 64bit Desktop-Version on a double Xeon Server with a Apaptec Scsi-Controler and it seems that the scsi-controller (aic79xx) makes some trouble.

I started from the live-cd and everything worked fine even the installation.
The boot messages show that he finds my hd like sda1 sda2... and sdb1 ...
But after a while the boot process stops and says "cannot find root". 

Sorry for no more detailed information, because the server is located in my office and I can only give you more detailed information tomorrow.

Is there someone out there, who knows how to fix this boot-problem?

There are some postings in the web, but none really gave me an idea how to fix the problem.

P.S. There is a Suse 9 Version running without problems, not thinking about the long boot process but it works.

---

### Post by stevetc on 2008-11-11
I solved my problem simply adding 'rootdelay=130' in grub config, exactly at the end of the kernel parameter (/boot/grub/menu.lst)

---

