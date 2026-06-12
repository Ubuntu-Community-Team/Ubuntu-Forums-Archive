---
title: "Unkown filesystem - Grub Boot issues"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by sepiashots on 2013-04-29
I tried to upgrade from 12.04 to 12.10 and that failed when the upgrade lost unity, and all attempts to recover it failed, so I thought I'd just re-install. The machine has 3 drives. 1Gb (data, mounted but not as part of the primary system), 500Gb, mounted as root, and a 750Gb as Home.

I built as as I have done many times before. HOWEVER, I have a new motherboard, so EFI, with lots of options in the BIOS, which mean naff all to me, and now I can't get Ubuntu to install, I've tried many times, I've tried changes the various compatibility parameters, I've set-up a EFI FAT32 205MB boot area, etc, etc.

I've tried going into GRUB rescue and checking the data, but the insmod normal fails as it can't find insmod...

I've followed the use of the GUI boot-repair, and run it. Again this has failed. 

I realise I'm not providing technical data, but having followed every thread I can find I have no idea what to try or what data to post now.

Thankyou for any help / advice.

---

### Post by oldfred on 2013-04-29
With UEFI you have to first decide if you want BIOS or CSM boot or UEFI boot. 
Then if UEFI you have to repartition to gpt with a efi partition first. Or if BIOS you can format with either MBR(msdos) or gpt as Ubuntu will boot to BIOS with either.
If dual booting with Windows, you have to have gpt partitiong if in UEFI mode or have to have msdos partitioning if booting in BIOS mode.
I have had Windows XP in a MBR drive and Ubuntu in a gpt drive that dual booted without issue.

What is current partitioning, what way do you want to boot, do you have backups to totally reformat if you want to change?

       sudo parted /dev/sda unit s print

 sudo parted /dev/sdb unit s print

---

