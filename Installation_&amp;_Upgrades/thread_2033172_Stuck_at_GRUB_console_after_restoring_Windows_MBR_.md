---
title: "Stuck at GRUB console after restoring Windows MBR on dual-boot machine"
date: 2012-07-25
forum: Installation &amp; Upgrades
---

### Post by almikul on 2012-07-25
Hi,

I would like to give you a brief overview of what steps led me to this problem. My work requires me to encrypt a Windows drive with BitLocker that uses TPM. Originally, Linux Grub was installed on the MBR (sda1), so I could boot either in Linux or Windows from the Grub menu. However, BitLocker did not like this setup and refused to encrypt the Windows drive. To solve this problem without re-installing any system, I restored Windows MBR and installed grub on the same partition where the main Linux system resides (sda5). Then I copied the first 512 bytes of sda5 to a file which I put on sda1. Then I used *bcdedit* from the Windows repair disk to create a Linux entry in the Windows boot menu by pointing to this file. 

It seemed that all went well, and Windows could boot without any problem, but when I try to boot into Ubuntu (12.04), I go directly to the grub console (i.e., 'GRUB>'). I tried different method to boot into Ubuntu from grub console, and all of them failed. I do not want to mess with the Windows MBR again as I read that BitLocker could refuse to decrypt the drive. 

My question is how to fix this problem? Preferably by repairing the grub on the Linux partition? I know it is not a clear-cut issue as I must stick with Windows MBR to manage dual-boot. My main concern is if I try any grub repair programs, it could just overwrite Windows MBR with Linux boot loader. I will appreciate any advice and comments! Thank you in advance.

---

### Post by oldfred on 2012-07-25
I know some used to do something similar with grub legacy and Windows XP by using boot.ini to refer to a file.

Part of the issue may be that the grub2 in the MBR use code right after MBR which is core.img.

From one of my drives:
 > => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos14)/boot/grub on this drive.


So bitlocker may overwrite part of the area from the MBR to the first partition. Other DRM software did the same and grub2 wrote code to avoid the sector with the DRM code.

It may just be better to install grub2 to the PBR- partition boot sector. That is not recommended as it converts from finding and using files to hard coded addresses to find the file on the drive. If a major update moves file the it breaks grub2 and you have to reinstall/repair. Then you can use the PBR to boot from.

Grub2 also remembers where to reinstall on major updates. If you had it in the MBR it may still have that setting and you should change it. My standard instructions say to not choose partitions but you are the exception to prove the rule.

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

I think Boot-Repair may reinstall grub2's boot loader to the PBR or you should be able to boot with Supergrub which can bypass grub to load kernel.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
May be better to run the git/beta version of boot script as it has some fixes.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)


Another choice is just to install grub2's boot loader to a CD or USB flash drive and use it to boot your Ubuntu. I have grub2 installed to all my flash drives and manually configure a boot stanza to boot some of my installs.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)
How to make a GRUB_II USB
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
Herman has instructions for grub2 rescue boot CD, USB, or floppy. Also grub legacy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)

---

### Post by darkomano on 2012-07-26
You can use the file (from "/boot/grub/" directory)
- boot.img (GRUB2) 
or
- stage1 (GRUB legacy)
 
Both files are 512 bytes long and contain boot sector code to load Linux/Ubuntu.
 
If Linux/Ubuntu partition was moved/resized you have to reinstall GRUB (either version) first, preferably to partition. 
 
General Windows - Linux/UNIX guide using boot sector code for dual -booting under control of Windows boot manager - [http://www.boyans.net/DualBootWindows7andLinuxOrUnix.html](http://www.boyans.net/DualBootWindows7andLinuxOrUnix.html)
 
Note:
If you encrypt Windows partition you must ensure Windows boot related files are on another partition (active, primary) as boot files cannot be encrypted !
This is one of the reasons a so called "SystemReserved" partition is created when installing Windows 7 on unformated disk.

---

### Post by almikul on 2012-07-26
> **darkomano said:**
> You can use the file (from "/boot/grub/" directory)
- boot.img (GRUB2) 
Yes, it worked! I copied it to the System Reserved partition (sda1) and pointed BCD to it, and it worked. 

Before, I was trying to create a file from the boot sector of my main Linux partition (by doing dd if=/dev/sda5 of=./file bs=512 count=1), and it kept bringing me to the GRUB console. I guess it just did not install GRUB correctly on sda5 then... 

Well, the problem solved. Thank you very much, **darkomano** and **oldfred**.

---

