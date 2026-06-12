---
title: "Dual-boot Ubuntu and Windows 8.1 with Raid 0 SSD setup can't get working (Asus UX301)"
date: 2014-07-08
forum: Installation &amp; Upgrades
---

### Post by excetara2 on 2014-07-08
I have been trying for days now to get this working. I have an Asus UX301LA with two 256GB drives in raid 0.

No matter what I try I can't install the bootloader anywhere. Any partition I try it always says that it fails. I know ubuntu installed correctly I just can't boot into it.

Any help would be much appreciated.

---

### Post by Gordonbp531 on 2014-07-08
You need to install Grub on the EFI partition.
Run up the Live CD (or USB), and use the Disks utility to tell you which partition is the EFI one.

---

### Post by excetara2 on 2014-07-09
I finally got it working but only if I break the raid0 array and install with UEFI/gpt with both Ubuntu and WIndows 8.1.

How do I force it to install to the EFI partition or do it manually?

Clearly it works and I have no problem installing Ubuntu with the Raid arrays I just can't get the Grub to install on the EFI partition. I know which partition it is so that isn't the problem.

Any help would be much appreciated.

---

### Post by oldfred on 2014-07-09
The desktop installer does not have all the correct RAID software yet. It is in server install, but that is not a live installer. And it used to be in the Alternative installer, but that has been discontinued.

You should be able to use live installer and add Boot-Repair. It will automatically install RAID drivers (you may have to say yes), and then should reinstall grub correctly.

You should also be able to manually add RAID drivers, mount RAID partition(s), efi, /boot, / (root) if they apply and install grub to the root of RAID not MBR of hard drive.

       How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)


 [http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

      
 For RAID reinstall from live-CD/DVD/USB
sudo apt-get install mdadm
[http://ubuntuforums.org/showthread.php?t=2022679](http://ubuntuforums.org/showthread.php?t=2022679)
"fakeRaid" with nVidia, note p1 is partition, without p1 is root of RAID volume
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

---

