---
title: "New Installation on new SSD"
date: 2018-05-05
forum: Installation &amp; Upgrades
---

### Post by frozenelectronics on 2018-05-05
```
ADATA 64GB USB3.0 thumb drive
Ubuntu Budgie 18.04 (just downloaded today)
Burned with win32diskimager from Win 10, boots into Ubuntu just fine
/dev/sda is a 1TB mechanical drive with windows 10
/dev/sdb is a 120GB SSD
```

Hey everyone. I've tried Googling for this but I am very confused by what is happening. I have installed other Linux distros with UEFI with no issues whatsoever. In the past (on other machines) it would typically share the Windows ESP and there'd be no issues at all. This is an Inspiron laptop - I just today added an SSD by removing the CDROM and using one of those SSD-to-CDROM brackets (which are so cool!). Everything is fine, the drive is detected, I could see the files that were on there before.

So I booted into the Ubuntu installer, went through the setup, then got to the partitioning page. I triple-checked I was in UEFI mode, yet it was still asking for where to put the bootloader. I googled this, found out it was fine, it will just ignore it... so, I created new partitions on the SSD (first time around I made a 500MB /boot out of habit, not sure if that's needed or not), 100GB /, and 8GB swap. Installer got almost all the way through then crashed with the fatal error grub2-uefi was unable to install the bootloader to /dev/sda. Scratched my head a little bit, then tried again, creating a new ESP partition on sdb1 (the new SSD), 100GB /, 8GB swap again. Pointed the "Where to install the bootloader" at /dev/sdb1 (although apparently it ignores this, though it doesn't seem to). Got to the end of the installation, same error "grub2-uefi was unable to install the bootloader to /dev/sdb1". I looked in the little console and it said something like /boot/efi/EFI/somethingsomething is not a directory (or is not accessible). 

So now I'm getting really confused. I am 100% sure I am booted in UEFI mode. First of all, the boot menu (after disabling fast boot and secure boot in the BIOS) actually has two sections, one for legacy boot and one for UEFI boot. I picked the USB ADATA thumb drive in UEFI mode. Second, I get the text selection thing for what to boot into (try or install). Third, the installer can see Windows Boot Manager. And fourth, ls /sys/firmware/efi shows a bunch of items.

Do I even need to create the second ESP partition on the new disk? The UEFI Wiki page for Ubuntu says something like there should only be one ESP partition *per disk*, making me think that because I am installing Ubuntu to a new disk it requires its own ESP partition. I'm reluctant to point the bootloader installation at /dev/sda1 because that is where Windows Boot Manager is currently and I don't want to corrupt it by accident. Also, why does it appear that the bootloader destination is *not* being ignored? That seems very strange to me.

I'm currently still booted into the live session, so I can easily check/do things that are suggested. Thanks so much for the help!

EDIT: Here are the partitions... yes, sda is a mess, Dell has all sorts of partitions and I never bothered messing with them.
[IMG]https://imgur.com/a/kvPg7cW[/IMG][IMG]https://i.imgur.com/3Rcei7E.png[/IMG]
[IMG]https://i.imgur.com/hHtubzB.png[/IMG]

EDIT2: Here is the error in the terminal with the exact above partitions.
[img]https://i.imgur.com/7LXvG8K.png[/img]

---

### Post by ubfan1 on 2018-05-05
Check the file on the /dev/sda1 esp and see if there is an .../EFI/ubuntu directory, with the grubx64.efi and shimx64.efi and grub.cfg files in it (maybe others too).  If they are present, you may want to check the size of .../EFI/Boot/bootx64.efi against shimx64.efi and grubx64.efi to see if it's a copy).  This is the backup bootloader, and may be used for certain conditions (like an external drive, or an error on a boot).  That's the expected grub installtaion location.  Check that /dev/sdb1 is empty. If you want to boot off sdb, you may just copy all the sda1 files to sdb1.  Since your drive is pretty easily removable, you might want to do that.  It would be great if the location is actually used,

---

### Post by frozenelectronics on 2018-05-05
OMG as soon as I started reading your response I remembered I used to have a dual-boot ubuntu installation on this laptop ages ago, meaning somewhere in /dev/sda1 there will indeed already be an /EFI/ubuntu directory. If I delete that directory, and then create partitions on sdb without a new ESP, it should automatically pick up /dev/sda1 and put the EFI there?

---

### Post by ubfan1 on 2018-05-05
I'd have to check out what 18.04 is doing on installs to say anything.  The old ubuntu bootloaders should still work just fine.  Did anything actually get written to sdb?  That would be new behavior.

---

