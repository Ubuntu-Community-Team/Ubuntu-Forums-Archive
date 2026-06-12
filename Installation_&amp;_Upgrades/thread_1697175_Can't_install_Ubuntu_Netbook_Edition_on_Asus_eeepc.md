---
title: "Can't install Ubuntu Netbook Edition on Asus eeepc 1001PX"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by hakelm on 2011-02-28
I have problems installing Ubuntu Netbook Edition (ubuntu-10.10-netbook-i386.iso)on Asus eeepc 1001PX.
 
My casper.log contains:
Begin: Running /scripts/casper-premount ... done.
done.
stdin: error 0
mount: mounting /dev/loop0 on //filesystem.squashfs failed: Invalid argument
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

I have tried both Universal-USB-Installer-1.8.3.3.exe and the Ubuntu start up disk creator to prepare my USB-stick.
I have earlier installed the Ubuntu desktop 10.10 on the same machine with the same method without problems.

Any advice is appreciated.
Håkan

---

### Post by Quackers on 2011-02-28
Welcome to UF :-)
Have you checked the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out ok, boot from the usb again and at the first purple screen (the one with the purple man icon at the bottom) press any key. Then choose your language and on the next screen choose the option to check the cd for errors (it doesn't matter that you are using a usb stick). If it finds any errors the usb image is no good and must be made again.

---

### Post by hakelm on 2011-02-28
Thanks, Quackers, for your prompt reply.
My md5sum is in order and my iso file installs without a glitch in vmware. I can, however, not find any means for checking the installation media on the first screen, only a memory test utility. Is there any other way to check my USB-stick (I have only one of this size), or is it possible to use an USB-hard drive or a SD-memory?
Håkan
Ps I have access to a current Ubuntu 10.10 desktop and a Windows 7.

---

### Post by ismisepaul on 2011-08-25
Hi, I was having a similar problem. My USB drive was partitioned into two, CDFS(U3 sandisk) and FAT32. I resolved the problem by deleting the CDFS on the USB drive. 

The tool I used was this: [http://u3-tool.sourceforge.net/](http://u3-tool.sourceforge.net/)

Hope that helps

---

### Post by hakelm on 2011-08-25
Thanks a lot. I did, however, install the regular Ubuntu desktop and that works nicely,
but I will anyway test your solution.
By the way, what are the advantages of the Netbook Edition compared to the normal Ubuntu disttribution?
Håkan

---

### Post by meeples on 2011-08-25
> **hakelm said:**
> Thanks a lot. I did, however, install the regular Ubuntu desktop and that works nicely,
but I will anyway test your solution.
By the way, what are the advantages of the Netbook Edition compared to the normal Ubuntu disttribution?
Håkan

Ubuntu actually no longer has a Netbook Edition, Ubuntu is now suitable for desktop, laptop & netbooks.
So just install regular Ubuntu or upgrade your 10.10 install :)

---

### Post by meeples on 2011-08-25
i see that you were actually wanting to install 10.10, that's my bad.

netbook edition 10.10 as far as i remember has the initial version of the Unity interface, which makes much better use of small screens and is much more user friendly, upgrading to 11.04 would give you the more mature version of Unity, which is now the default interface for all of Ubuntu, hence why there is no more Netbook Edition...

---

