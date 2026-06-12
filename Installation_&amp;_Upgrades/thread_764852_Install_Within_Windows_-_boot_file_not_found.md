---
title: "Install Within Windows - boot file not found"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by blug on 2008-04-24
Hi guys.

I get a "file not found" error after installing ubuntu "within windows".

After installation, I get the boot option of 
-Windows XP
-ubuntu

Selecting any ubuntu option in GRUB, I get 
Error 15: File not found.
press any key to continue which goes back to the boot menu.


I have a C: (Pri) and F: hard drives. I chose to install ubuntu on the F: drive. Wubi installer defaulted to F: since it was the only one with 4GB free.

Windows installtion went fine.
Booting into ubuntu and rest of the installation went fine.
File not found after post-installation reboot.

Everything else looks fine.
I have root.disk and swap.disk in my F:\ubuntu\disks and I have 
a wubildr and wubildr.mbr on my C:\

boot.ini contains the following:
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
c:\wubildr.mbr="Ubuntu"

Anyone got any ideas?

---

### Post by blug on 2008-04-25
I had some help on other threads.

GRUB pointed to hd0 in stead of hd1.

Read this thread for details:
[http://ubuntuforums.org/showthread.php?p=4788466#post4788466](http://ubuntuforums.org/showthread.php?p=4788466#post4788466)

---

