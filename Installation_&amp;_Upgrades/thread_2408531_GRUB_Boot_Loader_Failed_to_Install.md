---
title: "GRUB Boot Loader Failed to Install"
date: 2018-12-19
forum: Installation &amp; Upgrades
---

### Post by gdawgs47 on 2018-12-19
I'm attempting to install Lubuntu 18.04 LTS on an Aspire one Cloudbook. I've used this computer to distro hop multiple times, and I've heard that this can kill the hard drive if done once too many times. Secure boot is off, and the laptop is on UEFI mode. When I try to install Lubuntu, I get the following error:

The 'grub-efi-amd64-signed' package failedto install into /target/. Without the GRUB boot loader, the installed system will not boot.

My boot-info can be found here: [http://paste.ubuntu.com/p/QpTsyWDFww/](http://paste.ubuntu.com/p/QpTsyWDFww/)

Any help is appreciated!

---

### Post by oldfred on 2018-12-19
With MMC drive, script does not show all the details.

But it looks like you ran Boot-Repair or installed multiple times as you have multiple unknown entries in UEFI.
With all Acer you have to change the unknown to ubuntu or whatever name you want, by using UEFI to enable trust on the grub/shim/ubuntu UEFI boot file.

       Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)

These are all essentially the same, but sometimes one explanation makes more sense than another.
       
 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

### Post by gdawgs47 on 2018-12-19
I'm aware that you have to select the boot file on Acers. However, I don't think that's the problem. Normally, after an install, it will ask whether to reboot the system or continue testing. However, when the error from above appears, the dialog box to reboot does not appear. Instead, it sends a report about the error.

When I try to install the system, I select the option to wipe the hard drive. However, when I go to select a boot file, I get the option to select files from the following directories: antergos_grub (I belive this has caused some issue because I haven't been able to install any distro after attempting to install Antergos), BOOT, Microsoft, and ubuntu. Before this was an issue, only the ubuntu directory was availiable post install since I purged Windows from my computer. 

When I select the grub and shimx boot files from the ubuntu directory, it brings up the GNU GRUB menu with the following:

Minimal BASH-like line editing is supported. for the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completion.

grub> _

---

### Post by oldfred on 2018-12-19
I would not think having syslinux in MBR and PBR (partition boot sector) of the ESP would make any difference. The PBR is not used with UEFI boot, only with BIOS boots.

So then it may be that grub did not fully install to the ESP and you just have left over files.
Does Boot-Repair also give errors on the full reinstall of grub using its advanced mode?

Some have had to run filechecks to repair a FAT32 partition. A few have had so many issues, they had to backup & then delete the FAT32 partition & then recreate it with FAT32 and boot and/or esp flags.

       [http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872](http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872)
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by ubfan1 on 2018-12-20
If you never clean out the old boot entries on the EFI partition, it will fill up eventually.  That will certainly cause an installation failure of another one.

---

