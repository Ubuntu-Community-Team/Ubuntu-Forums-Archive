---
title: "New HDD and dual boot"
date: 2013-02-08
forum: Installation &amp; Upgrades
---

### Post by jefe9 on 2013-02-08
I have just got a 2nd HDD ( 1TB Seagate) and want to add Ubuntu to boot from that 2nd hard Drive.
 
The C: drive has Windows Vista running ... so it will be a dual boot system.
 
I have a Ubuntu installation CD which has previously worked for dual boot with Windows Vista, and Ubuntu being installed on a 2nd external hard drive (that disk broke - hence the new disk. - this original external Hard disk had been a boot disk from another PC )
 
But this install of Ubuntu seems to work, but just wont boot afterwards.
 
I have partitioned the new drive with Windows Disk Management; setting up the primary partition as active.
But I cannot find a way to make this partition a boot partition ... and I think this must be the cause of the failure to boot.
Does anyone know how to do this? ( I tried bcdboot , but couldnt find the bcdboot program.)
 
Also, when installing Ubuntu ... the Ubuntu installer just does not see the Windows NTFS partitions ... Ubuntu claims to see only 125GB of space, whereas it is a 1TB disk and Windows disk manager sees 934GB of space ... peculiar ..
 
Any advice appreciated
 
Jefe 
NB ...

---

### Post by oldfred on 2013-02-09
You cannot create partitions with Windows for Ubuntu to install into. You may want part of the new drive to be NTFS for shared data. But Ubuntu will only install to Linux formatted partitions and Windows does not create those.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    - 250 MB efi FAT32  (for UEFI boot or future use for UEFI)
    - 1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
    
You do have to use Something else or manual install so you have the option on where to install grub. And you want grub2's boot loader in the MBR of the new drive. Otherwise it will default to sda.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

