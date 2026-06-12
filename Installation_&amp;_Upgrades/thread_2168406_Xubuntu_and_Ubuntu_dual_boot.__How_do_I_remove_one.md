---
title: "Xubuntu and Ubuntu dual boot.  How do I remove one of them?"
date: 2013-08-17
forum: Installation &amp; Upgrades
---

### Post by markMDW on 2013-08-17
Hi, a while back I had installed Ubuntu 12.04 on a Compaq laptop that had Xubuntu installed (before that Windows Vista was on it)  It now boots to Grub, where I can select the Kernel to use.  For a long time I thought I had erased the Xubuntu installation, but occasionally I somehow boot into it.  Actually, on this particular laptop, the Hardware works better with the Xubuntu installation, but I can't figure out how to choose between the two systems, when I want to boot into Xubuntu.  

How do I select Xubuntu from Grub, when each time I intentionally try to find it in Grub, it loads up Ubuntu anyway?

Or, how can I just delete the Ubuntu installation and use Xubuntu only?  Thanks in advance!

---

### Post by oldfred on 2013-08-17
Do you really have one install with both Ubuntu and Kubuntu as choices on the login screen? The logo right and above password has the choices of gui to use.

If you have two installs:
Basically boot into Xubuntu and install its grub2 boot loader to the MBR. Then delete Ubuntu partition and run grub update to remove the Ubuntu entries from the menu. Make sure you backup any data you may have in the Ubuntu install first.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

If not sure post link to BootInfo report.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by markMDW on 2013-08-18
Thanks for the reply!  I don't actually have Xubuntu and Ubuntu as individual choices on the login screen... just the standard Grub bootup of kernel choices.  However, when I've switched to bootup to another kernel option, and then rebooted, I have definitely gotten back into Xubuntu several times.  Each time it booted into Xubuntu was a complete surprise.  Whenever I try to select a long ago kernel, hoping to somehow get back into Xubuntu, it doesn't work.  I have no idea what the exact sequence is that causes Xubuntu to boot, but its always after selecting some other past kernel option.

I'm going to be trying out your commandlines... Thanks!

---

