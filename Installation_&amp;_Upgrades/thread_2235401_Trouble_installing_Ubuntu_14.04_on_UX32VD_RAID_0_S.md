---
title: "Trouble installing Ubuntu 14.04 on UX32VD RAID 0 SSD Array."
date: 2014-07-20
forum: Installation &amp; Upgrades
---

### Post by cfmwarren on 2014-07-20
Hello,

I've been trying to install ubuntu on my laptop, an ASUS UX32VD with 128gb SSDs in RAID 0 for a while now. While the install completes successfully, the bootloader seems to not install, since a reboot doesn't boot into Ubuntu and there is no Grub prompt. My guess is that Grub doesn't know how to deal with my array.

When looked at, the raid array shows up under /dev/mapper/ with all the partitions. When Gparted or parted is used to look at the array, they crash with an error concerning a corrupt GPT header. Without any way to install Grub, I don't see how I can use the installed OS. One thing to keep in mind is that I'm trying to duo boot with Windows 7, and that the platform is UEFI with Secure Boot disabled. I've tried other flavors of Linux, even going so far as to build a Gentoo install for the system, but the bootloader problem remains. 


Any help would be appreciated, as the Ubuntu installer seems to not be able to deal with my system alone. 
Thanks.

---

### Post by oldfred on 2014-07-21
With 12.04 they had the alternative installer that included RAID & LVM installs. Desktop installer would not install to RAID nor LVM. Also server installer can use RAID or LVM.
With 12.10 they discontinued the alternative installer and said later they would add LVM & RAID to the desktop. I now see LVM as an option but it does not look like the desktop installer supports RAID yet.
There also seems to be discussion on merging RAID drivers dmraid and mdadm. Now you have to know which driver to install to get grub to correctly install and to mount partitions.

       if RAID
For RAID reinstall from live-CD/DVD/USB
sudo apt-get install mdadm
[http://ubuntuforums.org/showthread.php?t=2022679](http://ubuntuforums.org/showthread.php?t=2022679)

 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
User who installed fakeRAID
How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)

"fakeRaid" with nVidia, note p1 is partition, without p1 is root of RAID volume
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

---

