---
title: "ubuntu not detected windows 10"
date: 2015-10-21
forum: Installation &amp; Upgrades
---

### Post by terry_gardener on 2015-10-21
i had a problem with manjaro booting after gnome 3.18 upgrade so i removed it and installed ubuntu 15.10 instead since it is only few days to final release. 

the problem i am having is grub2 didn't detect windows 10 and it now just boots straight into ubuntu. 

i have tried sudo os-prober, sudo update-grub, sudo update-grub2.
i have attached the summary output from boot-repair 
[http://paste.ubuntu.com/12885386/]("http://paste.ubuntu.com/12885386/")

---

### Post by yancek on 2015-10-21
You have mixed an MBR install (windows 10 on the first hard drive) with a UEFI install of Ubuntu on the second hard drive.  What you are experiencing is the result of this.  You have EFI files for both Ubuntu and windows but they are on the second drive and your windows install is on the first drive.  One possible solution is to re-install Ubuntu using MBR rather than UEFI and accept the default to install Grub to the MBR of the first disk, /dev/sda.  There are probably other solutions less drastic so you will have to wait for someone with more knowledge on UEFI repairs to come along.

---

### Post by oldfred on 2015-10-21
Since Windows is BIOS boot probably easiest to convert Ubuntu to BIOS boot.
You can do that without reinstalling if you add a tiny 1 or 2MB unformatted partition on sdb anywhere with the bios_grub flag (if gparted) or ef02 code if using gdisk to create partition.
Then use Boot-Repair to totally uninstall grub-efi-amd64 & reinstall grub-pc in BIOS mode. Be sure to install to sdb. 
Then install a Windows boot loader to sda, not for current use, but just to keep sda as a Windows only drive. 
And set BIOS to boot from sdb. 
Grub should offer to boot Windows also. If grub does not work for any reason then in BIOS or one time boot key you can directly boot Windows on sda.

Since you have newer hardware:
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

   UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by terry_gardener on 2015-10-23
thanks for the help

---

