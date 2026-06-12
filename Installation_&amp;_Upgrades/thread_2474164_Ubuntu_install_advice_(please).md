---
title: "Ubuntu install advice (please)"
date: 2022-04-22
forum: Installation &amp; Upgrades
---

### Post by kite005 on 2022-04-22
I have a laptop with win 10 install on the SSD drive. I have an external SSD drive in an enclosure with Ubuntu 20.04 installed on it connecting through the C port. I downloaded the 22.04 Ubuntu install downloaded with the existing Ubuntu 20.04 system onto the external drive. I'm assuming I can just run the install from the download folder and just follow the prompts to creat new partition(s) on the external drive and install and have the two versions of Ubuntu on that drive. I am asking if that sounds correct/reasonable or am I way off in what I'm thinking andoff my rocker?

---

### Post by guiverc on 2022-04-22
Also asked at [https://askubuntu.com/questions/1403923/ubuntu-22-04-install](https://askubuntu.com/questions/1403923/ubuntu-22-04-install)

---

### Post by yancek on 2022-04-23
You can boot the 22.04 iso from Grub on 20.04 but as stated in your other thread, it is not  simple process and you have to create the boot entry manually.
You would also have to create unallocated space or your partitions for 22.04 in advance of the install.
The windows and 20.04 installs are probably EFI.  You need to verify that.  You also need to know on which drive the Ubuntu EFI files are.  In any case, if both Ubuntu 20.04 and 22.04 are EFI, the 22.04 install of Grub will likely overwrite the EFI boot files of 20.04.  That could be a problem for you if you decide you do not want 22.04.

So it is possible but I would not advise doing it unless you are very familiar with partitioning and Grub.

---

### Post by grahammechanical on 2022-04-23
> I'm assuming I can just run the install from the download folder and  just follow the prompts to creat new partition(s) on the external drive  and install and have the two versions of Ubuntu on that drive.

Running Ubuntu 20.04 in the external drive will mount that drive (put it in use). We cannot do anything to a mounted drive. We create/delete/resize/move partitions using GParted running in a Ubuntu Live session. As you need to run Ubuntu from a live session to create those partitions then you should use the same live session to install Ubuntu into the partitions you have created. Or choose the Install Alongside option. The installer will then divide the drive as it see fits.

Some would recommend disconnecting the Windows drive. Otherwise the Ubuntu installer will put it Grub bootloader files on the Windows drive. It is best that the installer put the Grub boot files in an EFI partition on the Ubuntu drive.

Regards

---

