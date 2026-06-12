---
title: "How can I restore grub-efi to my UEFI boot partition?"
date: 2013-11-23
forum: Installation &amp; Upgrades
---

### Post by renato3 on 2013-11-23
I installed Ubuntu 13.10 and then I installed Windows 7, so I lost my grub-efi boot. How can I repair it, so my grub-efi is put in the UEFI boot partition?

ps: the first Ubuntu installation was done using UEFI boot, so grub-efi was already installed.

---

### Post by jansdejager on 2013-11-23
edit your bios to boot /efi/Ubuntu/shimx64.efi. Windows creates an entry automatically which will be at the top of your booting list in bios. If there is no such entry in your bios, then it maybe be that windows has replace the /efi/boot/bootx64.efi which is the default file for bios to boot when in uefi mode. It could also be that you managed to install windows in legacy mode and not efi mode, [which is a big pain to fix]("http://www.insanelymac.com/forum/topic/184349-force-windows-7-install-dvd-to-do-an-efi-boot/?hl=%2Bforce+%2Bwindows+%2Befi").

if you are sure you have correctly installed Ubuntu in efi (files in efi/Ubuntu/*), and windows in efi mode (files in efi/Microsoft/*), then remember to run sudo update-grub when you have edited your bios to boot Ubuntu as default, so that your new windows partition will show up in grub when you boot.

---

### Post by ptrakk on 2013-11-23
if you have a live cd then boot with it.. mount the boot partition 
# sudo mkdir /mnt/boot
# sudo mount /dev/sdXY /mnt/boot

replace X for the letter  and Y for the partition number. use 'sudo blkid' to find this.

install grub back
# sudo grub-install --root-directory=/mnt/boot /dev/sdX

notice there was not a Y at the end of that last line.

---

### Post by oldfred on 2013-11-24
Did you convert your Windows 7 DVD to UEFI? The DVD installs in BIOS with MBR partitioning and will just convert drive to MBR. Then you would not be able to boot Ubuntu in UEFI mode. Both Windows & Ubuntu only boot from MBR(msdos) partitions with BIOS.

If it did convert to BIOS, did it also erase all the Linux partitions? It may have?

Post this:
sudo parted -l

If it did not convert to BIOS/MBR, you should just have Windows & ubuntu entries in UEFI to boot in UEFI mode. Windows would probably be the default but you should just be able to select ubuntu.

or for more detail on your current configuration, post this using live installer.
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

