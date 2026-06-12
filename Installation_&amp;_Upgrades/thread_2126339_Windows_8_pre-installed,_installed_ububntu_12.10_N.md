---
title: "Windows 8 pre-installed, installed ububntu 12.10 No GRUB menu PLEASE HELP !"
date: 2013-03-16
forum: Installation &amp; Upgrades
---

### Post by pyi1024 on 2013-03-16
Just got a new laptop, made some partitions, installed ubuntu while in uefi mode.

Now when I boot, there is no grub menu, and I go straight to ubuntu.

I installed boot-repair, and the url for the report is [http://paste.ubuntu.com/5620209/](http://paste.ubuntu.com/5620209/)

I want to be able to boot into windows. PLEASE HELP !!

---

### Post by oldfred on 2013-03-16
Do you have secure boot on in UEFI? Some only boot Windows with it on, others only with it off.

You installed Ubuntu in BIOS/legacy/CSM mode not UEFI mode. But Boot-Repair converted your install to UEFI mode and added correct UEFI boot entries. 

Does this boot from grub menu?
 menuentry "Windows UEFI bkpbootmgfw.efi" {

      
 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
It looks like HP has a lot of vendor utility type boot files in the efi partition, so Boot-Repair found all of them and created menu items. But ignore the one's from os-prober as those will not work.

the flash drive you have installed, does not look like it has any of the new tools to boot UEFI type systems. You have to be booting in UEFI mode for Windows & now Ubuntu to work correctly.

      
 Other HPs that have worked. UEFI should be similar.
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

 HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

---

