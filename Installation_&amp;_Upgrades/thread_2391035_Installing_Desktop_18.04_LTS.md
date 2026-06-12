---
title: "Installing Desktop 18.04 LTS"
date: 2018-05-05
forum: Installation &amp; Upgrades
---

### Post by yegnal on 2018-05-05
I have a tower with multiple drives.  It dual boots Windows 10 and Ubuntu 16.xx on separate physical SSD drives.  When I installed 16.xx I needed to choose 'something else' and create my own partitions.  Only created three, swap, root, and home, and I had to choose 'Windows bootloader' from the dropdown asking where to install bootloader as the location to install it.  Everything works fine.

Doing the same while installing Desktop 18.04 LTS causes an error, [B][COLOR=#222222]grub-efi-amd64-signed packagefailed to install into target
[SIZE=4][/SIZE][/COLOR][/B]System does not boot Ubuntu, rather leaves me stranded at a Grub prompt.

Windows 10 boots, Ubuntu 18.xx does not.

Question is, why.  Previous version of Ubuntu installed no problem........   What gives.

I tried adding an EFI partition to the setup, I tried choosing different locations for the bootloader. In all I've tried installing 10 times, at least.  

I re-installed my previous version (16.04 Desktop LTS) with no issue.   

What did the developers change in this latest version, and why fix what wasn't broken.......  & how do I get my $15 back...........?

---

### Post by dino99 on 2018-05-05
Since Bionic, the default is to use a swap file, and the 'manual' partitioning script is fully broken  (at least when several storage devices are found) (plenty reports already lp:#1767703)
So the solution is to dist-upgrade 'manually' by setting 'bionic' instead of 'xenial' inside /etc/apt/sources.list, then 'save' . Then you can update/upgrade as usual (remember to use ppa-purge first if you have third party source(s).

---

### Post by yegnal on 2018-05-06
Am I to understand that 18.04 will never install cleanly and I am only able to upgrade from within 16.04 ?

Why the issue with grub suddenly, it's obviously better implemented in 16.04, why change that... it wasn't broken...

---

### Post by Dennis N on 2018-05-06
To show the current partitions on your drives, please post output of 
```
sudo parted -l 
```
It may reveal a problem you are not aware of.

---

### Post by yegnal on 2018-05-06
Am I missing something..  16.04 has no such issue...  installs perfectly fine...  So why would a latter version crash when installing grub..  This should never happen, makes no sense.  Problem is in development.

---

### Post by yancek on 2018-05-06
I just installed Ubuntu 18.04 to an external drive connected to a laptop with windows and 3 other Linux systems on the internal drive and one other  Linux on the external.  It took 20 minutes and I rebooted to 18.04, no problems whatsoever.  Do you still have 16.04 or did you install 18.0 over it?  It might be best to post more details on your system and the best way to do that is with the boot repair which you can get at the link below.  Select the 2nd option to use the ppa, you can do this from the Ubuntu install usb.  Run it with the Create BootInfo Summary option selected and do NOT try to make repairs.  Post a link to the output here and someone should be able to help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yegnal on 2018-05-07
I'm not unappreciative of the interest shown or the advice being given to my query....

However it's obvious a change was made to the 18.04 installation package creating a problem with grub2.  This issue "**grub-efi-amd64-signed ****packagefailed**** to ****install**** into ****target" **
is easily found in google and forum searches...  I say obvious, "[LEFT][COLOR=#222222][FONT=Verdana]a change was made to the 18.04 installation package[/FONT][/COLOR][/LEFT]" because again; 16.04 has no such issue, and installs perfectly fine.  

I was able to get 18.04 by re-installing 16.04 and forcing an update to 18.04 in apt.

[COLOR=#222222][FONT="Verdana]Model: ATASamsung SSD 850 (scsi)[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Disk /dev/sda:250GB[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Sector size(logical/physical): 512B/512B[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]PartitionTable: gpt[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]DiskFlags: [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana] [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Number Start   End    Size    File system Name                         Flags[/FONT][/COLOR]
[COLOR=#222222][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR][COLOR=#222222][FONT="Verdana]1      1049kB  473MB  472MB  ntfs         Basic data partition         hidden, diag[/FONT][/COLOR][COLOR=#222222][/COLOR]
[COLOR=#222222][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR][COLOR=#222222][FONT="Verdana]2      473MB   578MB  105MB  fat32        EFI system partition         boot, esp[/FONT][/COLOR][COLOR=#222222][/COLOR]
[COLOR=#222222][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR][COLOR=#222222][FONT="Verdana]3      578MB   595MB  16.8MB              Microsoft reservedpartition  msftres[/FONT][/COLOR][COLOR=#222222][/COLOR]
[COLOR=#222222][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR][COLOR=#222222][FONT="Verdana]4      595MB   249GB  248GB  ntfs         Basic data partition         msftdata[/FONT][/COLOR][COLOR=#222222][/COLOR]
[COLOR=#222222][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR][COLOR=#222222][FONT="Verdana]5      249GB   250GB  890MB  ntfs                                      hidden,diag[/FONT][/COLOR][COLOR=#222222][/COLOR]
[COLOR=#222222][FONT="Verdana] [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana] [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Model: ATASanDisk SDSSDHP1 (scsi)[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Disk /dev/sdb:128GB[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Sector size(logical/physical): 512B/512B[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]PartitionTable: gpt[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]DiskFlags: [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana] [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Number Start   End     Size    File system    Name                 Flags[/FONT][/COLOR]
[COLOR=#222222][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR][COLOR=#222222][FONT="Verdana]1      1049kB  538MB   537MB  fat32           EFI System Partition boot, esp[/FONT][/COLOR][COLOR=#222222][/COLOR]
[COLOR=#222222][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR][COLOR=#222222][FONT="Verdana]2      538MB   93.8GB 93.3GB  ext4[/FONT][/COLOR][COLOR=#222222][/COLOR]
[COLOR=#222222][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR][COLOR=#222222][FONT="Verdana]3      93.8GB  128GB  34.2GB  linux-swap(v1)[/FONT][/COLOR][COLOR=#222222][/COLOR]
[COLOR=#222222][FONT="Verdana] [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana] [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Model: ATA WDCWD1003FZEX-0 (scsi)[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Disk /dev/sdc:1000GB[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Sector size(logical/physical): 512B/4096B[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]PartitionTable: msdos[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]DiskFlags: [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana] [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Number Start   End     Size    Type    File system  Flags[/FONT][/COLOR]
[COLOR=#222222][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR][COLOR=#222222][FONT="Verdana]1      32.3kB  1000GB  1000GB primary[/FONT][/COLOR][COLOR=#222222][/COLOR]
[COLOR=#222222][FONT="Verdana] [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana] [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Model: ATA WDCWD1003FZEX-0 (scsi)[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Disk /dev/sdd:1000GB[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Sector size(logical/physical): 512B/4096B[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]PartitionTable: msdos[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]DiskFlags: [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana] [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Number Start   End     Size    Type    File system  Flags[/FONT][/COLOR]
[COLOR=#222222][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR][COLOR=#222222][FONT="Verdana]1      32.3kB  1000GB  1000GB primary[/FONT][/COLOR][COLOR=#222222][/COLOR]
[COLOR=#222222][FONT="Verdana] [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana] [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Model: ATA WDCWD5000AAKS-0 (scsi)[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Disk /dev/sde:500GB[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Sector size(logical/physical): 512B/512B[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]PartitionTable: msdos[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]DiskFlags: [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana] [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Number Start   End    Size   Type    File system  Flags[/FONT][/COLOR]
[COLOR=#222222][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR][COLOR=#222222][FONT="Verdana]1      32.3kB  500GB  500GB primary  ntfs[/FONT][/COLOR][COLOR=#222222][/COLOR]
[COLOR=#222222][FONT="Verdana] [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana] [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Model: ATA WDCWD5000AAKS-0 (scsi)[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Disk /dev/sdf:500GB[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Sector size(logical/physical): 512B/512B[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]PartitionTable: msdos[/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]DiskFlags: [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana] [/FONT][/COLOR]
[COLOR=#222222][FONT="Verdana]Number Start   End    Size   Type    File system  Flags[/FONT][/COLOR]
[COLOR=#222222][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR][COLOR=#222222][FONT="Verdana]1      1049kB  500GB  500GB primary  ntfs[/FONT][/COLOR][COLOR=#222222][/COLOR]

---

### Post by Dennis N on 2018-05-07
Your efi system partition is on sda2. I am wondering if the ubuntu installer might only install the efi grub files to sda1? Seems unlikely to me, but since I always have created an esp on sda1, don't know the answer. We already know it will not install grub to any other drive than sda. Someone here may know  -> With ubuntu installer, can you have the efi partition on sdax where x is not = 1? I would test it, but don't have any system where I could.

---

### Post by oldfred on 2018-05-07
I have seen same issue on grub not installing with all older versions of Ubuntu. Usually then Boot-Repair fixes it with a reinstall.
But there does seem to be a lot more of that issue with 18.04.

I have installed to USB SSD and my sda drive. And installed one of the dailies a few weeks ago to sdb.
And in every case it has overwritten the /EFI/ubuntu folder in the ESP on my sda. And that still is my main working system 16.04. So I backup ESP on sda. 

But every time it did install to ESP on sda without any errors.

If installing to a separate drive best to partition in advance and include an ESP, FAT32 with boot flag. Be sure to use gpt partitioning, not the 35 year old MBR(msdos). But Ubuntu's grub will not install to that even when you tell it to install to sdb and ESP on sdb exists. I just copy sda's ESP to sdb's ESP, but still use grub from sda to boot 18.04 on external or sdb.

If using UEFI, best to have all drives as gpt. 
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by yegnal on 2018-05-08
Again, why does 16.04 install without a hitch ?

---

### Post by oldfred on 2018-05-08
There have been major changes due to Meltdown & Spectre. 
You also have to update UEFI to fully protect from them.

[https://www.phoronix.com/scan.php?page=article&item=ubuntu-1804-6systems&num=1](https://www.phoronix.com/scan.php?page=article&item=ubuntu-1804-6systems&num=1) Ubuntu 18.04 LTS has the Linux 4.15 kernel, GNOME Shell 3.29.1, Mesa 18.0-rc5, GCC 7.3.0, Python 2.7.15rc1, Python 3.6.5, and is mitigated for Meltdown with KPTI while for Spectre V1 it opts for __user pointer sanitization over OSB and for Spectre V2 has full Retpolines.

---

