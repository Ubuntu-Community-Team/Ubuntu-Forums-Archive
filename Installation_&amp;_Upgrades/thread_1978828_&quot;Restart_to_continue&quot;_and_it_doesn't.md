---
title: "&quot;Restart to continue&quot; and it doesn't"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by ptr2mtr on 2012-05-12
Hi! 

I'm trying to install ubuntu 12.04 on my HP 635 laptop. 

First I tried using a USB flash drive. I chose to install, connected to my wifi and then to install inside Windows 7 and I had to "restart to continue", it restarted and the start screen with try ubuntu live/install ubuntu appeared again. 

I tried to burn a CD and install in that way, and when I press "restart to continue" it ejects the CD-tray and tells me to remove installation media, shut the tray and press enter. When I remove the CD, shut the trey and press enter it boots into windows.

Does anyone know what I'm doing wrong here? Thanks in advance!

---

### Post by jadtech on 2012-05-12
you have to pull the USB flash drive out  before you reboot :) 

it is bootable and will boot first every time if it is in place take aLL DISK OUT OF THE CD/DVD DRIVE AND ALL USB STICKS OUT OF THE USB PORTS ..

just to be sure though know when you choose to install inside windows you are not doing a full install   this is ubuntu install as a windows program it all works  about the same but is met to be temprary just to try it out in the end you will end up making new partitions and  doing the install if you like it and want  a full time linux  ..

---

### Post by ptr2mtr on 2012-05-12
> **jadtech said:**
> you have to pull the USB flash drive out  before you reboot :) 

it is bootable and will boot first every time if it is in place take aLL DISK OUT OF THE CD/DVD DRIVE AND ALL USB STICKS OUT OF THE USB PORTS ..

Yes, I guess that was the problem when I tried with the USB (it didn't say anything about removing it, though). 

Now when I try with the CD, I remove it before I press enter (and thereby rebooting). But then the BIOS-boot-order is: 1) CD (not in tray) 2) Hard disk (boots into windows for some reason?). 

So. No USB or CD in place when rebooting, but the installtion still doesn't continue.

---

### Post by darkod on 2012-05-12
The installation inside windows is specific because it depends on interaction with windows too. I guess some configuration that needs to kick in before windows and continue the install is not doing its job.

You can try running the wubi.exe as administrator in windows, that might help if it's permissions issue.

Other than that, I have no idea. I always recommend full dual boot install instead of wubi, but the choice is yours.

---

### Post by ptr2mtr on 2012-05-12
> **darkod said:**
> The installation inside windows is specific because it depends on interaction with windows too. I guess some configuration that needs to kick in before windows and continue the install is not doing its job.

You can try running the wubi.exe as administrator in windows, that might help if it's permissions issue.

Other than that, I have no idea. I always recommend full dual boot install instead of wubi, but the choice is yours.

Hm... I'm not trying to install wubi? I read about it and saw that some people had objections against it, so I rejected it. When booting with the CD I get three choices for installing: install inside Windows 7 (chose at startup), Erase everything and install or making the partitions myself. I'm choosing the first one. Is that wubi? And if so: How do I install "full dual boot"? Only by making the partitions by myself?

---

### Post by darkod on 2012-05-12
Inside windows sounds like wubi.

You have to be careful with HP machines. These days they are shipping them with all 4 primary partitions used. That is why the ubuntu installer is not offering "along side windows" option because it can't create a fifth and sixth partitions.

For a true dual boot, usually people delete the HP_TOOLS partition and then the ubuntu installer can offer the along side option.

But note that this will only allow creating new partition, it will not provide much space for ubuntu because that partition is very small.

For space, you can shrink the win7 partition using windows Disk Management. Restart win7 few times after that, in case it wants to do any checks. Do NOT create any partition for ubuntu from windows.

You can also consider making a set of recovery DVDs and in that case you can delete the recovery partition too and use its space.

Once you have deleted at least one partition, and have sufficient unpartitioned space (depending how much you want to allocate to ubuntu), you can start the install.

---

