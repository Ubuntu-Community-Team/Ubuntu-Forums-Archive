---
title: "Running UNR from USB with other .iso's"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by dj_bridges on 2010-03-29
I have a 4 Gb USB stick on which I have a few different distros and flavours etc (see end for how I made the disk). There is a generic boot and gfxmenu folder to give the boot options. For each distro / flavour I then copy the OS files from the .iso and add the relevent lines to menu.lst in boot. This system normally works perfectly. I tried to add UNR to the list (for a netbook I have), but failed, perhaps because I copied the wrong files across:

From the UNR.iso I copied:
A) casper/filesystem.squashfs and renamed UNR.sqfs
B) isolinux folder and renamed UNR
C) casper/initrd.lz and casper/vmlinuz to UNR folder on stick
D) Adding these lines to the boot/grub/menu.lst:
title Ubuntu Netbook Remix
kernel (hd0,0)/UNR/vmlinuz livecd=UNR fromusb vga=788
initrd (hd0,0)/UNR/initrd.lz

Unfortunately I get dropped to an ash shell after the system complains that it 'Gave up waiting for a root device'

Anyone got any ideas how to resolve this issue. I would really like to have UNR on the stick along with the other linux flavours so I can show people with netbooks its potential.


Full Instructions for multiple liveUSB:

1) Format the USB drive with ext3 without any partitions
2) Copy the OS files from a liveCD or mount the image and extract the isolinux dir and livecd.sqfs to the USB
3) Creat 2 folders- USB:/boot and USB:/gfxmenu
4) Copy /boot/grub/ folder from a running linux install into the USB:/boot folder
5) Copy /usr/share/gfxboot/themes/pclinuxos/boot/message to USB:/gfxmenu
6) Modify USB:/boot/grub/menu.lst to:

timeout 10 color black/cyan yellow/cyan
gfxmenu (hd0,0)/gfxmenu/message
default 0

title LinuxInstall
kernel (hd0,0)/isolinux/vmlinuz fromusb vga=788 
initrd (hd0,0)/isolinux/initrd.gz

7) Install GRUB to MBR of USB:

[user@localhost]$grub
grub>find /boot/grub/menu.lst
grub>root (hd2,0)
grub>setup (hd2)
grub>halt       

8) If you want multiple boot images then repeat step 2 for each (assign each pair a unique name) and then add relevent stanzas to menu.lst:

title Ubuntu
kernel (hd0,0)/Ubuntu/vmlinuz livecd=Ubuntu fromusb vga=788 
initrd (hd0,0)/Ubuntu/initrd.gz

---

### Post by dj_bridges on 2010-03-30
Ok so after a lot of digging, I finally realised that UNR uses Grub2 and not Grub1. What I am therefore asking is:

Does anyone know how to boot a Grub2 based iso from a Grub1 menu?
Can I convert a Grub2 based iso into a Grub1 based iso?

---

