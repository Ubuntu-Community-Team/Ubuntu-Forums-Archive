---
title: "is it possible to dual boot with ubuntu on msata and windows 8.1 on a standard hdd?"
date: 2015-02-09
forum: Installation &amp; Upgrades
---

### Post by dustin19 on 2015-02-09
sorry if this has been covered, i could not find anything specific to my question in search. anyway, title says (almost) all. i have an acer m5-583p-6423 that i am looking to put an msata in for ubuntu. i also have the mechanical hdd with windows 8.1 that i would rather be left untouched if possible. is there anything in whine-dows i need to change to prevent it from caching to the msata or is that something that is off by default? anything i should watch for during the ubuntu install? i am generally good with hardware, and can get by in linux, but i have never actually tried this, so i figured i would ask so as to avoid borking anything

thanks in advance.

---

### Post by oldfred on 2015-02-09
Unless your UEFI/BIOS has Intel SRT to create caching and even if it does you do not turn it on, Windows will not automatically use another drive.

Is system UEFI or BIOS? You need to be sure to install Ubuntu in the same boot mode as Windows.

Is your system using M.2?
[http://arstechnica.com/gadgets/2015/02/understanding-m-2-the-interface-that-will-speed-up-your-next-ssd/](http://arstechnica.com/gadgets/2015/02/understanding-m-2-the-interface-that-will-speed-up-your-next-ssd/)

Whether system is BIOS or UEFI, you do need to use Something Else and often better to disconnect hard drive, so everything is installed to new drive.
       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

 Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
      
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

If new drive is only Ubuntu, then I also suggest using gpt partitioning. Default is normally MBR(msdos) and Windows only boots from gpt partitioned drives with UEFI, but Ubuntu can boot in either UEFI or BIOS mode if correct supporting partitions are on drive.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by dustin19 on 2015-02-09
hey thanks for responding,
it would appear my laptop does not support intel srt. my system IS however uefi, and i will be sure to install linux in the same mode.
the port is definitely not made for an m.2
i ALWAYS use the something else option ;)
as for gpt vs mbr, i assume i will have to choose gpt since my windows drive is connected to a uefi laptop. please correct me if i am wrong. i will admit i have no experience with msata. just never used one

anywho, what i am gathering is installing ubuntu to the msata w/windows 8.1 on the platter drive should easily work provided i dont do something stoopid. again PLEASE correct me if i am mistaken.
thanks.

---

### Post by oldfred on 2015-02-09
Backup efi partition before install.

I prefer to have each boot loader on its own installs drive. But I installed a second copy of Ubuntu on sdb and it still installed the ubuntu efi folder on the sda drive. I am sure I told it to use sdb. But with efi boot, you can just copy the folders to the other drive. Backup is just in case of issues.

UEFI install will use gpt, but I always partition in advance and just choose partitions with Something Else. If partitioning in advance gparted defaults to MBR, so you have to first change devices, advanced to gpt.

---

