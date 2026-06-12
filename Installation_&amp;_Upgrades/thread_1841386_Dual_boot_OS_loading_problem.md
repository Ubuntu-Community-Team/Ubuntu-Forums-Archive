---
title: "Dual boot OS loading problem"
date: 2011-09-09
forum: Installation &amp; Upgrades
---

### Post by aceraspire on 2011-09-09
Hi all, I have a problem with my Acer Aspire 721 and hoping someone would be able to help.
This isn't EXACTLY a Linux issue, although I wonder if anyone with a similar set up has had a similar problem.

The system has been partitioned and running dual boot windows 7 and Kubuntu Natty without a problem for the last month.
Last night I ran a system update which caused windows 7 to crash on boot up from then on. :  I have run the Acer eRecovery to revert windows to factory defaults.

Now when I try to run windows I get:
error: no such device : B408884908880D14
error: no such disk.

Kubuntu still runs perfectly fine, I can even access the windows partition while in kubuntu and see that the files all seem to be there. 
I guess it has something to do with the GRUB? However, I'm certainly not the most tech-savvy, so if anyone can suggest anything to try I would be really grateful.

Thanks

---

### Post by YesWeCan on 2011-09-09
B408884908880D14 is a hexadecimal Windows file system identifier.
The error is that the boot loader can't find it. So if you are using Grub 2 then boot Natty and run
[COLOR="DarkSlateBlue"]sudo update-grub[/COLOR]
which rescans your disks for OSs and their UUIDs and updates your boot menu.

---

