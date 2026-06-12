---
title: "Fail to install ubuntu 7.10 on an adaptec HostRaid array"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by StevenSolid on 2008-01-12
Hi,everyone.

I try to install ubuntu on an IBM IntelliStation Z pro, there are two scsi hds in the machine, and there is an adaptec hostraid array controller on the board , it is an fakeraid array.

I have make an RAID0 array and have an Windows XP installed.

And now I want to install ubuntu 7.10 on the fakeraid array without remove the XP.

I found this article "[My Ubuntu (7.10) Installation]("http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation")" , and I follow the article to install ubuntu.

Everything seems fine before I type the "shutdown -r now" command.

But after the computer is rebooted , ubuntu can't not recognise the raid array, it seems that the dmraid didn't work, ubuntu still sees two hds.

Did anyone konw how to deal with this problem?

I have tried Fedora 8, it is quite easy to install Fedora 8 on my computer,no need to install other software to support the raid array, but still I want to try ubuntu.

Can someone tell me what to do?

Or is it ubuntu 8.04 support fakeraid like fedora do?

Thank you very much!

---

### Post by Pumalite on 2008-01-12
Boot your Live CD and post:
sudo fdisk -lu

---

