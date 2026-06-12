---
title: "Dell D400, dual boot"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by jerryd2 on 2014-04-18
Ubuntu forum,
 Dell D400 Windows XP Home 32 bit

 I have repartitioned my ssd and am trying to install
 Ubuntu 12.04 since my notebook doesn't support PAE.

 The install goes well until I get an error message that
 says "Choose a different device to install the bootloader"

 I click the radio button to select a different device and
 select /dev/sda then click continue.  The installation seems
 to finish and then asks to restart.  I click on restart and
 nothing happens.  If I power down and restart the bios
 doesn't see the ubuntu partition.

 I've read what I could find on the net but nothing tells
 me exactly what I'm doing wrong.

 Any suggestions?
Jerryd2

---

### Post by jerryd2 on 2014-04-18
I see a lot of reads but no replies.  There must be someone who can tell me what to try.
Jerryd2

---

### Post by TechAndNews on 2014-04-18
Hi Jerry: It seems you want to Dual-Boot an Old WindowsXP Laptop. When you run the Ubuntu CD/DVD, and click "install," you will see a few options. 1. Replace WindowsXP with Ubuntu. 2. install Ubuntu along-side WindowsXP. 3. Something Else. Choose Option 2. If that is not available, you have to Manually Create the Partition. Keep in mind Windows is currently using the entire HardDrive as NTFS (NT File System). Ubuntu Linux will need to use ext4 File System. For Linux, you need "3" Partitions: 1. / (root directory where the Linux Operating System goes), 2. swap (twice the size of the RAM installed on the Laptop - example 1GB RAM, swap will be 2GB), 3. the rest of the File Storage space (for your Home folder). --So, you are basically splitting (Partitioning) a HardDrive from One Partition to Two (Partition A for Windows, Partition B for Linux); even though I mentioned "3" Partitions just for Linux. It's just the way it has to be setup. AS FAR AS THE BOOTLOADER: it must be installed onto the Laptop's HardDrive, in the root directory. Sometimes, during a Linux install, I have a USB Plugged-in. And you have to click the "radio button" to choose the Default Laptop HardDrive. And the Bootloader has to go on there, at the Beginning of the drive. This is called GRUB, and it enables your Laptop to have a 15 second splash-screen that Lists the Linux Kernel, Linux Recovery, Memory-Test, and WindowsXP. You just down arrow to your preferred OS, and hit Enter to Boot into it. --If nothing is selected in GRUB, it will Automatically Boot into the First OS Listed -- in this case Ubuntu Linux 12.04. Good Luck, and Enjoy Linux.

---

### Post by grahammechanical on 2014-04-18
There is something that I do not understand. If this Dell D400 has a CPU that does not support PAE, then it should not be possible to install Ubuntu 12.04 on it as Ubuntu requires a CPU that has the Physical Address Extensions (PAE) capability. Perhaps it is Xubuntu 12.04 or Lubuntu 12.04 that you are installing? It makes a difference to our understanding of what the problem actually is.

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

Regards.

---

### Post by ibjsb4 on 2014-04-18
and this

[http://ubuntuforums.org/showthread.php?t=2151890](http://ubuntuforums.org/showthread.php?t=2151890)

---

### Post by jerryd2 on 2014-04-18
Lubuntu forum,

 Here's the iso I'm using lubuntu-12.04-desktop-i386.iso
 I tried 12.04.4 and got the no PAE support message.

 I'm still stuck with this install.

 Here's my partition table:

/dev/sda
/dev/sda1  NTFS  WINDOWS     18.00  GiB
/dev/sda2  ext4  LINUX        4.88  GiB
/dev/sda3  ext4  LINUX swap   1.95  GiB
/dev/sda4  fat32 FAT32 shar   4.91  GiB
/dev/sdb
/devsdb1
free space

 I don't know why there as any sdb or free space?

 I select /dev/sda2 as ext4 and mount it on /
 I select /dev/sda3 as ext4 swap space and don't mount it at all.
 I select /dev/sda4 as fat32 and mount in on dos

 I want /dev/sda4 to be availavel to both operating systems
 and the only options for mount are dos and windows so I
 picked dos.

 When Lubuntu is nearly installed I get the error message saying:
 Choose a different device to install the Bootloader on:

 I click ok and then click on the radio button to chose a
 different device.  I select /dev/sda.

 The install finishes instantly and says restart but it never
 restarts.  Windows boots alright and the /dev/sda4 shows up as
 drive E but I never get the option of booting to Lubuntu.

 What am I missing/doing wrong ??

Jerryd2

---

### Post by steeldriver on 2014-04-19
are you sure you are selecting **device** /dev/sda not partition /dev/sda**1** for the grub bootloader install? iirc the interface isn't particularly clear at that point, I've accidentally done that myself in the past

---

