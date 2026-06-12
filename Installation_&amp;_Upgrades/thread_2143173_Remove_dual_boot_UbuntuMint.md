---
title: "Remove dual boot Ubuntu/Mint"
date: 2013-05-08
forum: Installation &amp; Upgrades
---

### Post by thebobbit on 2013-05-08
Hi Guys,

I installed Ubuntu 12.04 on my old lenovo thinkpad a little while ago, just to have a tinker but had Mint recommended to me by a friend (each to their own, I suppose). So I installed Mint 14 as a second OS alongside my Ubuntu and now using Mint's grub at boot. Long story short, for now, I get along better with Ubuntu than I do Mint and would like to reclaim the space that Mint is hogging. Question:

Can I:

1. Use gparted to just resize my Ubuntu partition to take over the entire disk again, wiping Mint.
2. Boot into Ubuntu and reinstall Ubuntu's grub
3. Be happy

Or is it a little more complicated?

Cheers in advance

---

### Post by Irihapeti on 2013-05-08
If Mint's is managing things at the moment, you need to install Grub in Ubuntu _before_ you remove Mint. Otherwise, when you go to bootup, Grub will be looking for the Mint files that you've removed, and you'll get the dreaded "grub-rescue>" prompt.

Probably the easiest way to do this is with Boot-Repair [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) If you have any problems with it, there are several forum members who can help you.

---

### Post by oldfred on 2013-05-08
+1 on Boot-Repair.

It also just released a new CD,
       LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

 but you can install it into your current Ubuntu or Mint.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

But if you can boot into Ubuntu you can from it, just install grub to MBR.
      
 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

---

