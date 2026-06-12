---
title: "Unable to dual Ubuntu with Windows 8 Grub not installing"
date: 2015-12-13
forum: Installation &amp; Upgrades
---

### Post by eMshsWE on 2015-12-13
Hello,

I have a Dell Inspiron 15 5000 series laptop with 4GB RAM, 64 bit laptop which has Windows 8 installed on it. I am trying to dual boot Ubuntu 14.04 alongside, but it refuses to install. I followed the instructions given on this webpage [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html) . During installation of Ubuntu 14.04 I am getting this error when grub is being installed.

The grub-efi-amd64-signed package failed to install into /target/. Without the GRUB bootloader, the installed system will not boot.

Multiple attempts of installation of Ubuntu 14.04 gives the same error.

Could someone please help me out?

---

### Post by LostFarmer on 2015-12-13
On my 2 Asus laptops to get grub to install without error, I had to connect to the net.  I did not have download updates checked.  This was for Ubuntu, Mint and Pinguy but do not remember the version.

---

### Post by oldfred on 2015-12-13
Is your system UEFI or BIOS?
If Windows is UEFI, you need to install Ubuntu in UEFI boot mode. 
And how you boot install media is how it installs.

Post this from terminal in live installer:
       sudo parted /dev/sda unit s print

---

### Post by eMshsWE on 2015-12-30
Hello,

My Windows is UEFI. So I need to boot up the live USB in UEFI Boot mode.

I am attachng the output of the command that you had asked for :

```

ubuntu@ubuntu:~$  sudo parted /dev/sda unit s print 
Model: ATA ST500LT012-1DG14 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start       End         Size        File system  Name                          Flags
 1      2048s       1026047s    1024000s    fat32        EFI system partition          boot
 2      1026048s    1107967s    81920s      fat32        Basic data partition          hidden
 3      1107968s    1370111s    262144s                  Microsoft reserved partition  msftres
 4      1370112s    2906111s    1536000s    ntfs         Basic data partition          hidden, diag
 5      2906112s    147740671s  144834560s  ntfs         Basic data partition          msftdata
 6      263942144s  612102143s  348160000s  ntfs         Basic data partition          msftdata
 7      612102144s  960260095s  348157952s  ntfs         Basic data partition          msftdata
 8      960262144s  976771119s  16508976s   ntfs         Microsoft recovery partition  hidden, diag


```

Does this help you out?

---

### Post by oldfred on 2015-12-30
If you try to reinstall grub using Boot-Repairs's advanced options and full uninstall/reinstall of grub, do you get same error?

You may just need to run Windows' chkdsk on the ESP - efi system partition. In Windows you have to mount it first.
Or you can run dosfsck or fsck.vfat from Ubuntu live installer.
 sudo fsck.vfat -t -a /dev/sda1
man dosfsck

Then run reinstall of grub again.


Be sure you have booted in UEFI boot mode, not CSM/BIOS.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by LostFarmer on 2015-12-31
You show no linux partitions, only NTFS.  Are you installing linux on  a NTFS partition ?   If you are, I am not sure it that will work, but 'oldfred' will.

---

### Post by oldfred on 2015-12-31
You can have data in NTFS, and ESP - efi system partition must be FAT32 with boot flag, but all Linux system partitions must be Linux formats.

---

### Post by eMshsWE on 2016-01-02
Hello,

I am attaching a snapshot of my Hard Disk s Disk Managemnt,

I wish to install Ubuntu on the unallocated space of 55.41 GB.

But the problem is that C drive after shrinkage is 69.06 GB and thanks to the huge number of applications that came installed in Windows 8, only 14.3 GB is free.

I am running out of space on C drive, So I will not be able to install additional software in C drive like Games etc.

Could anyone advise me on which drive to install Ubuntu such that there is enough space on my C drive?

Or is it possible to expand C drive and grab space from other volumes ?

I had another doubt. I am downloading Windows 10 now and plan to upgrade my PC from Windows 8 to Windows 10. Is it then possible to dual boot it with Ubuntu 14.04 ?

---

### Post by oldfred on 2016-01-03
While I like to have separate NTFS partition for data, you show two. And then have made main install or c: drive smallish. If planning on upgrading and installing more apps, I would combine one of your two other NTFS partititions back into the main install. NTFS works best if it has 30% free space or you need lots of unused space in the c: partition.

Backup you system before moving partitions around. And best to use Windows own partitioning tools for Windows NTFS partitions and use gparted for Linux partitioning editing.

---

