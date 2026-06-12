---
title: "After trying to install Ubuntu alongside Win 7, I cannot boot any OS?"
date: 2014-10-13
forum: Installation &amp; Upgrades
---

### Post by boyan2 on 2014-10-13
I'm presenting my problem as detailed as possible, and I'd appreciate it a million if you bear with me throughout the entire story. :)

So I wanted to install Ubuntu alongside my Windows 7. I downloaded it, put it on a flash drive and began with the installation. I didn't create a separate partition just for the Ubuntu (I didn't think it was necessary). I have 2 hard drives, 1TB each. On the first one I have two partitions (C and D), and on the second one I have just one (E). Anyways, when I had to install Ubuntu I had to create 4 logical partitions. And I did so. One for the boot (500mb), one for swap (8GB), one for home (15GB) and a general one (\) (18GB). *this might not be the exact values, but I don't think it matters much at this point* (N.B. At first, Ubuntu didn't detect any hard drives and partitions, and I had to create a "New Partition Table". After that, some free space appeared (about 1 TB). Anyways, I couldn't see the different partitions where I've installed my Windows 7.) So I decided to proceed with the installation, but I never got to a loading screen of actually installing any software. I thought it was terminated for some reason. I decided to try again, but this time creating a separate partition only for the Linux.  So I restarted my computer in order to create a new partition, but it simply froze at "Loading Operation System..." as if there was no OS at all installed on the HDD. I tried a lot of stuff in my BIOS, starting at safe mode and whatnot, but it didn't fix the issue. I even tried to install Ubuntu again, but I only got some errors when booting from the flash drive. Anyways, I came to the conclusion that the only way to fix this is to reinstall my Windows. So I inserted the Windows installation DVD, started the installation, and got to the point of choosing where to install Windows. So here is the biggest bummer! There is a list of a total of 10 different partitions (Disk 0 Partition from 1 to 4 + some unallocated space; and Disk 1 Partition from 1 to 4 + some unallocated space). The two disks are absolutely identical, meaning Disk 0 Partition 1 is the same size as Disk 1 Partition 1, and so on... I also noticed that each of these four partitions is about the size of each of the four partitions I created during Ubuntu installation (one is about 500MB, one is 7.5GB, one is 15, and one is 18). 

Bottom line, I have NO IDEA how that happened, since there was no installation process and no loading time, which I guess is required for the creation of  new partitions. Plus, why the F**K do I have only two identical disks, and I cannot see C, D and E partitions??? Have I lost all of my information just like that? How do I fix this ****?? I simply want to reinstall my Windows and run Ubuntu under a Virtual Box, I don't mind. However, I'm afraid that whatever I contemplate at this point, would be beyond my knowledge and therefore threatening my data (if its not entirely lost already...). I have to fix my PC as soon as possible, and I'd really appreciate any help on your side! :) Thanks a lot in advance! :)

---

### Post by ajgreeny on 2014-10-13
Gosh, that was difficult to read.  Long, continuous, stream-of conciousness paragraphs are not easy to follow.

However, it may help us  to have a lot more info from you.
What hardware do you have?
Boot to a live ubuntu DVD or USB and run the command ```
sudo fdisk -l
``` to show us exactly what partitions you have now after your attempts to install.

It may also be useful for you to go to Boot-Repair in my signature and run the boot-info-script that provides, but at this stage do not run the boot-repair option, if it gives you one, just post back here the link for the output it gives you.

---

### Post by oldfred on 2014-10-13
In addition to ajgreeny's suggestions, if you did not fully backup your data, stop trying to create partitions. Most suggest that you make image backup of drives and only then work on image.
You may be able to restore partitions, but after several attempted and aborted installs, we need lots of detail.

I think the summary report from Boot_Repair will give us the detail.

While using Something Else to install can work, some suggest disconnecting other drives when installing. And Windows always wants to install to a primary NTFS formatted partition with the boot flag or a empty drive. And with multiple drives may want to install the hidden in Windows 100MB boot partition to which ever drive is set as boot in BIOS.

Also if a newer system, you may have UEFI and BIOS issues. Post link to summary report so we know.

I had an issue with Boot-Repair install yesterday with 14.04. They changed the path so the command to change from trusty did not work.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Note error in above:
fred@trusy-ar:~$ sudo sed 's/trusty/saucy/g' -i /etc/apt/sources.list.d/yannubuntu[COLOR=#ff0000]-ubuntu[/COLOR]-boot-repair-trusty.list
sed: can't read /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-trusty.list: No such file or directory

This worked as now the -ubuntu does not seem to be in the ppa:
fred@trusy-ar:~$ sudo sed 's/trusty/saucy/g' -i /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list

---

### Post by grahammechanical on 2014-10-13
> [COLOR=#000000]and I had to create a "New Partition Table". [/COLOR]

Why did you do that? 

> [COLOR=#252525][FONT=sans-serif]The MBR consists of 512 or more [bytes]("http://en.wikipedia.org/wiki/Byte") located in the first [sector]("http://en.wikipedia.org/wiki/Disk_sector") of the drive.[/FONT][/COLOR]
[COLOR=#252525][FONT=sans-serif]It may contain one or more of:[/FONT][/COLOR]

[LIST]
[*]A [partition table]("http://en.wikipedia.org/wiki/Partition_table") describing the partitions of a storage device.
[/LIST]


[http://en.wikipedia.org/wiki/Master_boot_record#PT](http://en.wikipedia.org/wiki/Master_boot_record#PT)

By creating a new partition table you removed the values in the existing partition table and now the machine does not know where the operating system is. Windows that is. Did you really create a new partition table?

Oh, by the way, Ubuntu will install into just two partitions - one for the OS and one for swap. Give the installer enough space to install and it will create those two partitions and install Ubuntu in them. That is the easy way.

Some of us choose to have three partitions - one for the OS, one for /home and one for swap. Then if we need to re-install Ubuntu our user settings and data are safe. So, long as we do not format that /home partition.

Others choose to have one partition for the OS, one for swap and to keep all data on a separate third partition. And our data is safe from a re-installation but not our user settings.

Still others think we need a boot partition. Well maybe we do if we are using Windows 8. But otherwise it is not necessary. I do not have one and I have several installs of Ubuntu on two hard disks. Imagine how complicated life would be for me if I needed a /boot partition for each installation. The down side to having a separate boot partition is that it can get filled up as updated Linux kernels are installed during an update of the OS. If the boot partition becomes full then we need to create space in that partition for the system to continue receiving updates. So, a separate boot partition makes life a bit more complicated.

Regards.

---

### Post by boyan2 on 2014-10-14
So I put the disk repair on a flash drive and ran it. Here's the link it gave me after running the tests: [paste.ubuntu.com/8558739]("http://paste.ubuntu.com/8558739")

---

### Post by oldfred on 2014-10-14
You have jmicron RAID? That is hard ware based RAID.

I do not know RAID as there are so many different type.

Desktop installer does not support RAID. With 12.04 they had an alternative installer for both RAID & LVM. But with 13.04 they discontinued alternative installer and said use server installer or install 12.04 and upgrade. They said eventually they would have those features in the desktop installer. I do see LVM in desktop install now, but not RAID yet.

With RAID standard partition tools may not work, you need to use partition tools designed to work with RAID.

---

