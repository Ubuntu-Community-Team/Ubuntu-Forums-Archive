---
title: "grub-  not able to reinstall"
date: 2012-03-07
forum: Installation &amp; Upgrades
---

### Post by olddave1 on 2012-03-07
Hi,

My boot drive no longer boots, on 11.10 Xubuntu. Yesterday I got a message and using boot-repair allowed me to reinstall grub and boot fine. This morning I got a different message, something about not being able to read a file (long time since then trying to fix things, so cannot remember the exact message). So tried boot-repair from Alternate CD boot, this time it complained that I had a package manager of some sort running, when I did not, so could not use it. So tried to put grub on my 2 SSD setup according to this [http://www.ocztechnologyforum.com/forum/showthread.php?82648-software-RAID-LVM-TRIM-support-on-Linux](http://www.ocztechnologyforum.com/forum/showthread.php?82648-software-RAID-LVM-TRIM-support-on-Linux). The result was a purple screen and nothing beyond that. See [http://paste.ubuntu.com/872772](http://paste.ubuntu.com/872772) Ideally I'd like this to work, but have never been able to get Ubuntu installed on it.

So tried grub-install to the original spinning disk on /dev/sdc, using "sudo grub-install --root-directory=/mnt/dev/sdc" and I get the message "rm: cannot remove `/mnt/boot/grub/load.cfg': Read-only file system
/usr/bin/grub-mkimage: error: cannot open /mnt/boot/grub/core.img"

Seem stuck now. Ideas? 

Thx.

David

---

### Post by oldfred on 2012-03-07
I do not know RAID, but it looks like all your grub installs are looking to boot from md0 or from an install inside the RAID.

Your install in sdc1 looks like it is not part of the RAID set so you should use liveCD to reinstall grub to sdc.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sdc1 and want grub2's bootloader in drive sdc's MBR:
#Find linux partition, change sdc1 if not correct:
sudo fdisk -l
#confirm that linux is sdc1
sudo mount /dev/sdc1 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sdc

# If no errors on previous commands reboot into working system and run this, In BIOS choose to boot sdc:
sudo update-grub

---

### Post by olddave1 on 2012-03-07
Hi,

There are 2 completely separate disk setups I can boot from. The SSD with md0 and a LVM on sda and sdb and an older spinning hdd on sdc. I'd like to get the SSDs setup to boot from, but have never managed it. Ubuntu did not support installation onto those SSDs as they are setup, which is for optimal performance (small raid1 for /boot and LVM striped for speed).  Now that it looks like my SDC hdd is failing I need to get these working. 

I just now managed to get the sdc to boot with a restart and another try using boot-repair. After boot it fixed some disk errors. So ignore sdc for the moment, all it is is a store for my current home dir which I will copy to the LVM on the SSDs as soon as I can boot from the SSD.

And yes seem no one knows much about getting Ubuntu to boot from RAID1...

Thx.

David

---

### Post by oldfred on 2012-03-07
All I really know is the standard desktop does not have the extra RAID and LVM drivers. You need to use the alternative installer which is text based. It works the same, but instead of gui stuff they include extra drivers.

Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm

Raid install of Lucid:
[http://ubuntuforums.org/showthread.php?t=1458699](http://ubuntuforums.org/showthread.php?t=1458699)
[http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04-p3](http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04-p3)

RAID add kpartx to LiveCD or use alternative text installer
[http://ubuntuforums.org/showthread.php?t=1811353](http://ubuntuforums.org/showthread.php?t=1811353)

---

### Post by darkod on 2012-03-07
Your raid1 software raid is created with sda2 and sdb2, but if you look in the results for sda2 it says EFI System partition and for sdb2 Data partition.

Shouldn't it be the same? Looks like the raid1 is not created correctly. If that is true the whole SSD setup can't worj because it depends on the /boot partition to be outside the LVM.

Another thing to note is using EFI boot. Is there any particular reason for this? Can you go for the much simpler standard BIOS boot?

I have seen that link from the OCZ forum here earlier, and also it didn't work. Not sure if there is some flaw in it, or you just have to be careful and more experienced to apply it correctly.

If you are new to linux first creating the partitions (raid, lvm) and then installing onto existing partitions might be overwhelming.

In every case, I would drop the EFI boot if possible.

If you have no important data on the SSD install, you can try a new install, we can give you some instructions to try.

---

