---
title: "xubuntu xfce 64 bit installation in virtualbox"
date: 2014-04-03
forum: Installation &amp; Upgrades
---

### Post by smartcatxxx on 2014-04-03
Hi,

I have installed the XUbuntu 14.04 beta2 in VirtualBox. I made sure I have selected a Ubuntu 64 bit machine in VirtualBox when I have created the new virtual machine. I have downloaded and installed the xubuntu-14.04-beta2-desktop-i386.iso (which is supposed to install either 32 bit or 64 bit OS). However when I execute uname -a from the console it does report:

Linux vbxu14 3.13.0-19-generic #40-Ubuntu SMP Mon Mar 24 02:37:00 UTC 2014 i686 i686 i686 GNU/Linux

i686 indicates that it did install the 32 bit version, not 64 bit.

Does uname -a report the wrong 32 bit vs 64 bit, or I need to do something special, or there is something wrong with the installer, or virtual box?

Any suggestion/help appreciated.

Thanks,

cat

---

### Post by steeldriver on 2014-04-03
The ISO you downloaded is 32-bit - the 64-bit image would be xubuntu-14.04-beta2-desktop-**amd64**.iso (don't be put off by the amd part - it's just historical) 

[http://cdimage.ubuntu.com/xubuntu/releases/14.04/beta-2/xubuntu-14.04-beta2-desktop-amd64.iso](http://cdimage.ubuntu.com/xubuntu/releases/14.04/beta-2/xubuntu-14.04-beta2-desktop-amd64.iso)

---

### Post by su:bhatta on 2014-04-04
i386, is the 32 bit operating system for X86 systems.

Get the AMD64 from the link provided by steeldriver.

In case this issue is resolved, please mark the thread as 'Solved' using the 'Thread Tools' at the top right of this page.

---

### Post by smartcatxxx on 2014-04-04
Thank you steeldriver and bhattabhishek for taking the time to reply. Indeed the amd64.iso did the job. The description and the names of the 2 isos on the xubuntu download page confused me, I got the impression that the amd iso is only for AMD processors, and my computer has an Intel 64 bits processor.

---

