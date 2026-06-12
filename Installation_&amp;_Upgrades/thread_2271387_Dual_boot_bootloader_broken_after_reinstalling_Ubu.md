---
title: "Dual boot bootloader broken after reinstalling Ubuntu"
date: 2015-03-29
forum: Installation &amp; Upgrades
---

### Post by blacktemplar2 on 2015-03-29
Hello guys,

I have a Lenovo S205 on which I had until now a dual boot of Windows 7 and Ubuntu 13.04 and it worked very well with the GRUB2 bootloader. Yesterday I tried to upgrade my Ubuntu Version to 14.10 and during the upgrade process my Laptop froze. After manually shutting down the Laptop the Ubuntu System was broken and I decided to replace it with Lubuntu 14.10. Therefore I formatted all partitions used for Ubuntu and installed Lubuntu on them.

The Problem now is that something is broken with the bootloader. When I start the Laptop it doesn't load any bootloader and RESTARTS directly after showing the page where I can hit F2 to get to the BIOS settings. I already tried a lots of stuff suggested here in the Forum and elsewhere but nothing helped. Boot-Repair wrote that the repair was successfull but it didn't solve the problem, here is the link: [http://paste.ubuntu.com/10704158/](http://paste.ubuntu.com/10704158/)

I turned off UEFI boot in the BIOS, if that is an important information.

I hope you guys can help me I would really like to avoid reinstalling Windows.

---

### Post by oldfred on 2015-03-30
It looks like it should boot.

Part of issue could be that your flash drive is promoted to sda, you your install is on sdb when using flash drive. 
But the drive you boot from in BIOS is always hd0.

In grub you have these commands:
set root='[COLOR=#ff0000]hd1[/COLOR],msdos9'
search --no-floppy --fs-uuid --set=root --hint-bios=[COLOR=#ff0000]hd1,msdos9[/COLOR] --hint-efi=[COLOR=#ff0000]hd1[/COLOR],msdos9 --hint-baremetal=[COLOR=#ff0000]ahci1,msdos9[/COLOR]  108f7b61-c340-4526-a3d1-ce450dd5a181


The search by UUID is supposed to override an incorrect drive and UUID is correct, so it should boot.

But I might try using shift key to get to grub menu and edit all hd1 to hd0 and if any sdb1 entries.
And then see if that one boot stanza will boot. 

If you then can boot remove flash drive and run this and it will update all grub entries.
sudo update-grub

Another choice may be SuperGrub as it ignores your grub, finds kernels and creates its own grub boot.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

