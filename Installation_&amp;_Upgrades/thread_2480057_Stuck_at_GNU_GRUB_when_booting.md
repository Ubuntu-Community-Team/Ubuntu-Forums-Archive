---
title: "Stuck at GNU GRUB when booting"
date: 2022-10-17
forum: Installation &amp; Upgrades
---

### Post by jmchappell on 2022-10-17
I had installed Ubuntu on a partition of one SSD, Then I deleted that partition and formatted it with Windows. Then I installed Ubuntu on a different SSD.
Now when I start my computer sometimes (seems to be when I last booted into Windows) I get stuck on a command line that looks like

GNU GRUB
Minimal BASH-like line editing is supported...

grub> _

If I type exit I'm able to boot into Ubuntu or Windows, but how do I stop having the GNU GRUB show up?

I tried running boot-repair and got this output:
[https://paste.ubuntu.com/p/4DT2NGcKYr/](https://paste.ubuntu.com/p/4DT2NGcKYr/)

---

### Post by tea for one on 2022-10-18
A couple of suggestions:-

Line 95 - SecureBoot enabled
Disable secure boot in the UEFI settings

Line 246 - GRUB_TIMEOUT_STYLE=hidden
Change hidden to menu and then update grub.

Are you comfortable/familiar with editing Grub?

---

### Post by grahammechanical on 2022-10-18
Grub will give us this message if it cannot find the boot files at /boot/grub

> GNU GRUB
Minimal BASH-like line editing is supported...

grub> _

I am assuming that this is a UEFI motherboard with an EFI system partition for the boot files of both Windows and Ubuntu. You deleted the Ubuntu partition but the Ubuntu Grub boot files are still in the EFI system partition which you are booting from. Grub is looking for configuration file in /boot/grub in a partition that no longer exists.

How are you able to load into Ubuntu? Is there an EFI System partition on this second drive with Ubuntu on? If you can load Ubuntu run this command:

```
sudo update-grub
```

Does the printout show that Grub has detected Windows? If it does, then enter the UEFI settings utility and make the Ubuntu drive the boot priority. You may then get a Grub boot menu that lets you choose either Ubuntu or  Windows.

Regards

---

### Post by jmchappell on 2022-10-21
tea for one, I am not familiar with editing grub, I'm a novice.

grahammechanical, I ran ```
sudo update-grub
``` and got the following:
```
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-50-generic
Found initrd image: /boot/initrd.img-5.15.0-50-generic
Found linux image: /boot/vmlinuz-5.15.0-43-generic
Found initrd image: /boot/initrd.img-5.15.0-43-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
```

So it looks like Windows was found, but in the UEFI boot order section of my BIOS setup, I see "OS Boot Manager" is first. If I press enter it shows Ubuntu and Windows Boot Manager, but both on the same drive - neither of which is the drive that Ubuntu is installed on now.

---

### Post by yancek on 2022-10-22
How many drives do you have?  Boot repair shows one 500GB SSD and 2 other 1TB drives with windows on partition 3 (nvme0n1p3) of the SSD and Ubuntu on partition 2 (sda2) of the second drive.  Beginning at line 65, you can see that Grub was apparently installed incorrectly to an ntfs partition on sdb1.  Grub should never be installed on an ntfs partition.  I'm not sure how that happened, user error?

Did you accept the defaults for installing Grub when you reinstalled it?  It should have installed to the EFI partition on the first drive and beginning at line 9 of boot repair, you see all the correct files for an EFI boot of both windows and Ubuntu.  Those may be the files from the previous install. You have a vfat filesystem on sda1 which is the drive which shows Ubuntu installed on sda2.  sda1 does not appear to contain any EFI files.  Did you try to install the boot files to this partition (sda1)?

If you have more than 3 drives the 4th isn't showing for some reason.  When you go into your BIOS firmware setting and highlight OS Boot Manager, is Ubuntu at the top or is windows at the top?  If windows is the first entry, highlight it and hit the F5 key to move it down.  If Ubuntu is at the top, there is some other problem

---

