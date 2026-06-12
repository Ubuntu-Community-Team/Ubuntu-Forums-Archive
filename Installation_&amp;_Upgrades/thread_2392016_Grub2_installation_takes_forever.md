---
title: "Grub2 installation takes forever"
date: 2018-05-15
forum: Installation &amp; Upgrades
---

### Post by kleinmuffin on 2018-05-15
Hi,

I have a notebook with FreeDOS on it and wanted to install Ubuntu 18.04 now but unfortunately during the installation process Grub2 will load forever. The last thing that is logged in the console is "start running ordered scripts" but it's not doing anything after it.
At the beginning I thought LVM was the problem but I tried it without now and it's still not working.

Does anyone know this issue?

---

### Post by oldfred on 2018-05-15
UEFI or BIOS install?
Then if UEFI hardware & gpt, do you have the correct supporting partitions. And ESP - efi system partition (FAT32) for UEFI boot or bios_grub for BIOS boot?

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by kleinmuffin on 2018-05-16
The notebook has UEFI.
I'm not really into the partition and installation topic.

Here is the boot-repair pastebin: [https://paste.ubuntu.com/p/c2z6WgjPVt/](https://paste.ubuntu.com/p/c2z6WgjPVt/)

---

### Post by oldfred on 2018-05-16
You have UEFI install using LVM and full drive encryption.
LVM is an advanced volume system that requires more knowledge, but if you need encryption you have to use LVM.
With encryption you also must have a very good backup plan. If errors prevent your from being able to mount and use passphrase, then backup are only recourse. Most other normal repair procedures will not work.

It looks like system should just boot. Make sure UEFI is in UEFI mode, some work better if secure boot is off, which report says it is off.
Make sure you are booting system in UEFI mode. That is separate setting from booting USB flash drive in UEFI boot mode.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)
[https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm)

---

### Post by kleinmuffin on 2018-05-16
If Ubuntu boots it will only show Grubs minimal bash instead of showing the normal Grub interface where you can select the system you want to boot.

Installing doesn't seem to be a problem, thanks for the links. :) 
The installation is still not finishing by itself, so I have to stop the installation while it tries to install grub2. I think that isn't the way it should be.

---

### Post by oldfred on 2018-05-16
You have to let it complete for grub to be correctly installed.

If you manually mount your encrypted partition, Boot-Repair may work. Its just it will not see encrypted partition and needs that to run updates.

---

### Post by kleinmuffin on 2018-05-16
When and how do I have to mount the partition? As I already said, the grub installation won't finish after more than two hours. The encrypted partition is created by the Ubuntu installation but the grub installation is part of it. 

I'm sorry but since I'm not really into this whole topic, a description would be really helpful. Thank you so far for the help

---

### Post by oldfred on 2018-05-16
I do not use LVM, it is more advanced and complex. But required if you really want encryption.
Better for newer users to first learn Linux, and then progress to more advanced configurations. 

I do not know nor use LVM.
But have these in my notes.

[https://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i?rq=1](https://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i?rq=1) 

Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372) 

You do not need resize, but first command are mounting encrypted partition.
How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

---

### Post by rsteinmetz70112 on 2018-05-16
Looking over the pastebin, It looks like your /boot directory is sda2 and unencrypted ext4 file system.
IF you get to the grub> prompt you might be able to start the system using teh grub shell. I use lvm but not encryption.

---

