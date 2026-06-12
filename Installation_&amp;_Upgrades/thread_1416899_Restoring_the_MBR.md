---
title: "Restoring the MBR"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by pokeyThePenguin on 2010-02-26
I installed Ubuntu onto an external hard drive hooked up to my laptop. The MBR was overwritten, so now my laptop can only boot when I boot from the external.

I have Ubuntu (and only Ubuntu) on my laptop, and that's where all my precious things are. I have absolutely nothing of importance on my external right now.

In order to restore the MBR on my laptop, do I have to boot from a LiveCD and somehow do it that way? What are the steps for restoring the MBR?

I'm running Karmic Koala on a 32-bit Toshiba laptop.

---

### Post by oldfred on 2010-02-26
You can use the liveCD.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

But if with the external installed you can boot into your install you just have to reinstall grub from there. I am assuming grub2, ask if not.

reinstall from working system - first find Ununtu drive: 
sudo fdisk -l 
if it's "/dev/sda"  then just run: 
sudo grub-install /dev/sda 
If that returns any errors run: 
sudo grub-install --recheck /dev/sda 
Then: 
sudo update-grub

---

