---
title: "Grub is broken"
date: 2015-06-06
forum: Installation &amp; Upgrades
---

### Post by gustav-ekner on 2015-06-06
[FONT=arial]Hi,[/FONT][FONT=arial]
[/FONT]
[FONT=arial]Hi have had Windows 7 and Ubuntu 15.04 installed on my computer for some time now. It worked perfectly with dual-booting. But today I installed a third OS (Linux Mint) on my HDD (Ubuntu and windows are on my SSD), but now Windows isn't showing up anymore in GRUB when I boot, Only Linux Mint and Ubuntu.[/FONT][FONT=arial]
[/FONT]
[FONT=arial]I tried to repair it with the boot repair tool, but It got errors, and it didn't help. The program helped me with creating this log file: [http://paste2.org/EvOygPen](http://paste2.org/EvOygPen)[/FONT][FONT=arial]
[/FONT]
[FONT=arial]Any help would be appreciated.[/FONT]

---

### Post by oldfred on 2015-06-06
Have you tried?
sudo update-grub

I do not not see errors, but usually reasons for grub not finding Windows is that it is hibernated or needs chkdsk. You do show EasyBCD's very old grub4dos file /grldr in both NTFS partitions. That may also confuse things.

I would also install Mint's version of grub to sdb. You can use advanced mode in Boot-Repair and choose an operating system and drive to install into.

But not sure if Mint is the same as Ubuntu as Ubuntu's grub remembers where you originally installed and on major update will reinstall into that location.

Boot into Mint:
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by gustav-ekner on 2015-06-06
> [COLOR=#000000]Have you tried?[/COLOR]
[COLOR=#000000]sudo update-grub[/COLOR]

Thank you very much, that worked! Now I feel like an idiot because it was so simple, stupid that I didn't to that in the beginning. But when I googled after a solution I didn't find that.

---

