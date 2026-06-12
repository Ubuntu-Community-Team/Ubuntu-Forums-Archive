---
title: "Ubuntu 14.04 Installer not recognizing my Volumes/partitions"
date: 2014-11-18
forum: Installation &amp; Upgrades
---

### Post by Ashok_Nedumaran on 2014-11-18
I use a HP EliteBook 8570w which comes with a preinstalled Windows 7. Installed 8.1 over it and deleted the old windows file using disk clean up. It had four volumes, namely - System, Primary, Recovery and HP Tools. I deleted Recovery, HP tools and shrink-ed Primary volume. When I tried to install Ubuntu, the installer is not showing any partition/recognize any volumes. However, when I ran Gparted in Ubuntu live revision, partitions are available. Also, I don't get any option screen - like "Install along with Windows",.. "Something else” etc.


Can you anyone help me out? Thanks.

---

### Post by grahammechanical on 2014-11-18
Did you create a partition out of the unallocated space that came about through shrinking what you are calling the Primary volume?

---

### Post by Ashok_Nedumaran on 2014-11-19
I initially tried both as unallocated and as a new partition. Both the instance, I am not able see the partitions.

---

### Post by oldfred on 2014-11-19
Post this from live installer's terminal and/or screenshot from gparted. Attach screenshot with paperclip icon in advanced editor.

sudo parted -l

Did you leave Windows 8 fast boot on, or its always hibernated state? That must be off, even if installing in BIOS Mode not UEFI boot mode.

---

### Post by Ashok_Nedumaran on 2014-11-20
Hi oldfred,

I did turn off fast boot and hibernation state.

I have added a screen shot of Gparted and Output from the terminal

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000BPKT-6 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  316MB  315MB  primary  ntfs         boot
 2      316MB   500GB  500GB  primary  ntfs


Error: /dev/sdb: unrecognised disk label                                  

Model: Kingston DataTraveler G2 (scsi)
Disk /dev/sdc: 2007MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  2007MB  2003MB  primary  fat32        boot, lba


ubuntu@ubuntu:~$ 

Screen Shot

[ATTACH=CONFIG]258085[/ATTACH]

Thank you

---

### Post by oldfred on 2014-11-20
You have a BIOS based install using MBR(msdos) partitioning. 
You only have used 2 of the 4 allowed primary partitions, so you can create the extended partition and have as many logical partitions as you may want inside the one extended.

Use Windows to shrink the NTFS partition. Do not shrink too much as NTFS need about 30% free space to run well. At 10% free you just about do not have room to run a defrag. Check that fast boot is still off as Windows likes to reset to its defaults especially after maintenance.

Use Windows own disk tools to shrink the NTFS partition but not to create any new partition. Since gparted shows the Windows partition, I would then use it to create the new partitions and then use Something Else to choose which partition is / (root), which is /home. If swap created in advance it will auto find it.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

Since only one drive the default install to the MBR of sda will be correct for the grub boot loader.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
for MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]15-25 GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

