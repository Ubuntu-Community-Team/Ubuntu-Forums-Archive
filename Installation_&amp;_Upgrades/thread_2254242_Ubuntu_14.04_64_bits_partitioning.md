---
title: "Ubuntu 14.04 64 bits partitioning"
date: 2014-11-25
forum: Installation &amp; Upgrades
---

### Post by mohammed-moumen on 2014-11-25
Hello;
 I have upgraded my ubuntu 12.04 to 14.04 (64bits) and now I want to  create a separate partition in order to install on it a Windows system  but really I don’t know how to do it since I am a beginner on Linux. So I  downloaded Gparted to see my partitions and I got 2 partitions and one  as unknown :
 1st partition : /dev/sda1 which has a file system ext4 and has the  largest size on my laptop (924 GiB, and my hard drive’s size is about  1TB) and has a flag “boot”
2nd partition : /dev/sda2 which has a file system “extended” and a size of 7.89 GiB
3rd partition : /dev/sda5 with a “!” concatenated to its name and a file  system “unknown” and has the same size of 2nd partition.
So, I want at first to resize my partition (the 1st one) and then to  have a standard partition (boot, home and swap) after which I want to  create a separate partition for Windows to install an XP or Win7 on it.
Can you please help me?

---

### Post by yancek on 2014-11-25
sda1 is the system partition with Ubuntu, sda2 is an Extended partition which doesn't contain any data but does have the logical partition (sda5) inside it.  That's the swap partition.

You would save yourself some trouble is you installed whichever windows you are going to use first.  You can resize the first partition (sda1) by using GParted which is on the Ubuntu installation medium.  You can't do it from the running Ubuntu system.  If you already have Ubuntu installed, why do you want to create separate boot, home and swap partitions?  If you are a new user, it will be a lot easier to just leave Ubuntu on one partition as you won't have to worry about filling your boot partition (which happens quite frequently with new users) thus rendering Ubuntu unbootable.

After resizing Ubuntu, you can create a partition for windows.  Make sure you use a primary partition for it as windows will not boot if it doesn't have boot files on a primary partition, unlike Linux.  If you install windows, it will overwrite the boot code for Ubuntu in the master boot record.  You won't be asked or informed but it will happen so you will need to reinstall Grub to the mbr with your Ubuntu install medium.

---

### Post by carl4926 on 2014-11-25
My suggestion is
Backup your files and start again.
Create your partitions 
Eg:
sda1 ntfs for windows
sda2 extended
then create logical partitions in the extended space for ubuntu
personally I use separate partitions for / and /home

then install windows 7 (Not XP! it's not safe)
Update win7 fully before then installing Ubuntu
Use the Something else option in the installer to point to your created partitions

---

### Post by oldfred on 2014-11-25
I also like to have smaller system partitions, but Windows requires twice Linux as minimum. And large data partition(s). If dual booting one data partition should be NTFS so you can more easily share data.

The NTFS partition will have to be primary but also have boot flag for Windows to see it as a partition it can install into, and boot from. 

If you created an encrypted /home then swap also is encrypted and partition tools will not show it correctly. Encrypted data cannot be read.

---

### Post by mohammed-moumen on 2014-12-02
Thank you guys, and sorry for the late!
I wanted to start by resizing my sda1 but I think I don't have privileges even if I run Gparted as Super User! also I noticed someting strange with my partitions using Gparted :
I found another type of partitions which are dev/sdd=> dev/sdd1 has ntfs file system and is about 465GiB and a partition called "unallocated" with "unallocated" file system as well and 2.49MiB!!! I really don't understand if in this sdd I have ntfs file system so I can use It to install on It Windows? how should I proceed?
And the first issue is very annoying thus I can't resize my sda1 partition even if I am runing Gparted as SU!!!
Please need your help with many thanx!

---

### Post by oldfred on 2014-12-02
From terminal in live installer, post this:
sudo parted -l

Are you trying to run from inside your working install?
Or from live installer it still mounts swap (I do not think it mounts encrypted swap). 

If you show little key icons next to partition then it still is mounted & you cannot work on it. You have to unmount first. And you cannot unmount your working partition, so have to use live installer or separte gparted liveCD.

---

### Post by mohammed-moumen on 2014-12-02
> **oldfred said:**
> From terminal in live installer, post this:
sudo parted -l

Are you trying to run from inside your working install?
Or from live installer it still mounts swap (I do not think it mounts encrypted swap). 

If you show little key icons next to partition then it still is mounted & you cannot work on it. You have to unmount first. And you cannot unmount your working partition, so have to use live installer or separte gparted liveCD.

Hello,

Thank you "oldfred" for your help. This what I get after sudo parted -l under my terminal :

mohammed@mohammed-Inspiron-5537:~$ sudo parted -l
[sudo] password for mohammed: 
Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  992GB   992GB   primary   ext4         boot
 2      992GB   1000GB  8471MB  extended
 5      992GB   1000GB  8471MB  logical


Model: TOSHIBA MQ01ABD050 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary  ntfs


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 8471MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  8471MB  8471MB  linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Warning: The driver descriptor says the physical block size is 512 bytes, but
Linux says it is 2048 bytes.
Ignore/Cancel? c                                                          

mohammed@mohammed-Inspiron-5537:~$ 


And yes when I launch Gparted my partitions have little key next to them! That means that I can not work on them as I understood from your saying and that I should get boot CD of Ubuntu (maybe) so I can proceed to this partition?? please explain to me as you explain to a person that is not familiar with Linux so I can understand what I should do and thus It'll be a good help dor me to learn something in linux!

---

### Post by oldfred on 2014-12-02
The sr0 & sr1 errors are just that the CD & DVD are not writeable. So not really an error.

Did you install with an encrypted /home? As then swap is also encrypted and gparted may not show it correctly.
I have not dealt with encrypted partitions and do not know if just the encrypted swap or having encrypted /home inside partition causes added issues.

Info on using gparted. You need to boot live installer. Best to use current Ubuntu live DVD version or download gparted or parted magic liveCD as they will be newer gparted versions.
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


You are showing two drives, is 500GB drive also an internal drive or is it an external drive. If internal I would suggest installing Windows to it.

You have to shrink the sda1 partition and can then create a new sda2. It must be formatted NTFS and have boot flag for Windows to install into it. Normal Windows installs to blank drives use 2 primary partition, one is just a 100MB boot partition so you could encrypt the main Windows install. But the boot partition is not otherwise required, but once installed be sure to have a Windows repair CD or flash drive or know how to get to the repair console with Windows.
Windows will overwrite the MBR with its boot loader and you will need the Ubuntu live installer to reinstall grub to MBR so you can dual boot.
Windows sometimes overwrites partition table incorrectly, so have full backups of all your data in your Ubuntu install.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by mohammed-moumen on 2014-12-03
> **oldfred said:**
> 
Windows will overwrite the MBR with its boot loader and you will need the Ubuntu live installer to reinstall grub to MBR so you can dual boot.


Thank you Oldfred,

It is very helpful what you explained to me, the 500GB is external drive (sorry I've put my external drive on and didn't get any attention to it :D )! So, above is your Quote of the Windows overwriting the MBR (please what is the MBR, I understood that is the boot section is It right? ) : is this overwriting going to happen 100% if, after resizing my partitions and creating an sda2 with boot flag, I try to install Windows? If so, would the live CD of Ubuntu correct this overwriting? Also I resume here the steps that I should do and please be patient with me and correct to me if I am wrong :*

1- live CD of Gparted or Ubuntu to resize my partitions and create an sda2 with boot flag => in this sda 2 I should creat a 100MB small partition for boot section of Windows, and both with NTFS formatting.
2 - installing Windows with live CD on sda2 boot partition
3 - recovering the MBR (boot section ?? ) of Ubuntu with live CD
4- using Grub to make both Ubuntu and Windows bootable.

Are these steps right?

Many thanx!! :)

---

### Post by oldfred on 2014-12-03
I think if you partition in advance, Windows only uses one primary partition. It is when it installs to a blank drive or into unallocated space, then it creates the separate 100MB boot partition. If sda2 that is one partition. If formatted NTFS with the boot flag Windows will install to it, so it must be large enough for all of Windows.

Computers with BIOS and MBR partitioning boot by BIOS loading info on hardware, and jumping to MBR. The MBR is the very first sector of the hard, so not very large. MBR also has info on the 4 primary MBR(msdos) partition and which has boot flag. Windows boot loader in MBR, looks for partition with boot flag or active partition in Windows install, and jumps to that partition to find more boot code.
Grub does not use boot flag, but does put added boot code in the sectors immediately after the MBR. That code tells grub which partition to find the rest of grub.

More detail on boot process. Lots of detail, but just reviewing photos gives a good explanation.
       Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
 [http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

 [http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)

Grub/BIOS boot process:
[http://www.thegeekstuff.com/2011/02/linux-boot-process/](http://www.thegeekstuff.com/2011/02/linux-boot-process/)

Very technical details of MBR. But first paragraph or two cover basics.
[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)

After you install Windows, you use the instructions posted in links above at bottom of post #8 on restoring grub2's boot loader to MBR with Ubuntu live install or other Linux repair disk. Boot-Repair will work or just a couple of commands to mount Ubuntu partition and install grub to drive like sda, not partition like sda1.

---

### Post by carl4926 on 2014-12-03
> [COLOR=#000000]I think if you partition in advance, Windows only uses one primary partition[/COLOR]Correct. I can confirm this

---

