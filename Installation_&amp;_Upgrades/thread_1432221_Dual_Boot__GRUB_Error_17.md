---
title: "Dual Boot : GRUB Error 17"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by mccarun on 2010-03-17
Hi all,

I had ubuntu in my dell laptop along with windows vista. Few days I faced serious problem with Ubuntu so I tried removing Ubuntu as I wanted to install the latest version of it. The way I removed Ubuntu is by simply formatting the partitions (using partition software from Windows Vista). The formatting was successful. When I tried to restart my system I can't able to load windows vista and I'm getting the following screen.


GRUB loading stage 1.5

GRUB loading, please wait..
Error 17

Can you guys provide me a way to fix this issue. I dont want to loose any information on my hard disk as I have really important materials in it. Also I don't have my windows vista recovery disk handy with me right now which aggrevates the problem for me.

Thanks for the help in advance.

---

### Post by oldfred on 2010-03-17
Part of grub is in the MBR where the computer first goes to boot and then it is linked into the partition with the Ubuntu install. When you deleted the Ubuntu install the MBR boot has no place to go.

You need to install a windows boot loader into the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by tom4everitt on 2010-03-17
When you removed your ubuntu partition you also removed the main part of grub, the boot loader. 

So to get it working again all you need to do is install (some version of) ubuntu.

---

### Post by tom4everitt on 2010-03-17
> **oldfred said:**
> Part of grub is in the MBR where the computer first goes to boot and then it is linked into the partition with the Ubuntu install. When you deleted the Ubuntu install the MBR boot has no place to go.

You need to install a windows boot loader into the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)


I think you missed that the OP wants to install the latest ubuntu on his hard drive, hence no need to install the windows boot loader again. The boot loader of the new ubuntu will be sufficient.

---

### Post by mccarun on 2010-03-18
Thanks Guys. I followed the link in the first response and it fixed  my problem.

Now I'm downloading Ubuntu 9.10 and planning to install it tonight.

---

