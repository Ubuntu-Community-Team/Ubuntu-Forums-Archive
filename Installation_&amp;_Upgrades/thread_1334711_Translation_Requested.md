---
title: "Translation Requested"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by archp2009 on 2009-11-22
Hello,

Sorry for being long-winded.

I used to have 8 operating systems (4 Linux, 4 Windows) on 5 drives - 4 SATA, 1 IDE.  Now thanks partly to a failed attempt of Grub to overwrite my MBR I have lost access to all my operatings systems.  No that's a lie. I just regained access to one of the Windows by using fixmbr from the XP cd, and I can also re-access two other Windows installation via BIOS. Needless to say I'm way past the point of frustration.  I was just in the process of reinstalling Ubuntu 9.04 and Mint 7 trying to recover at least part of the 8-system bootloader that I used to have.  The last 3 attempts to reinstall Mint resulted in Grub 17 errors all 3 times.  Now I was just about to attempt to reinstall Ubuntu to see if that would work better.  Reinstalling is the only way I know to restore Grub without driving myself nuts with deciphering complex codes. Now I'm trying to reinstall Ubuntu 9.04 (not 9.10 with Grub2) on my first drive (SATA) along with Windows XP.  I select manual partitioning and after getting half wsy through I get this:

You are going to format the following partitions

Partition #3 of SCSI3 (0,0,0)  sda ext3
Partition #4 of SCSI4 (0,0,0)  sdb swap
Partition #5 of SCSI5 (0,0,0)  sdc swap
Partition #7 of SCSI6 (0,1,0)  sde swap

Would someone please translate this list into English. I would be forever grateful. Why is Ubuntu automatically creating 3 (three) swap partitions?  Actually, I didn't manually create either one. I just created the single 20gb main / ext3 partition and left around 8 gigs of free space for the rest.  Then I checked to see if it would proceed and it was willing to. The thing I'm worried about, though, is whether all this formatting is going to extend out of the single partition I started with and into other partitions on other disks or partitions containing other operating systems and/or data and, if so, what I should do about it. Thanks in advance for any comments or suggestions.

---

### Post by presence1960 on 2009-11-22
> **archp2009 said:**
> Hello,

Sorry for being long-winded.

I used to have 8 operating systems (4 Linux, 4 Windows) on 5 drives - 4 SATA, 1 IDE.  Now thanks partly to a failed attempt of Grub to overwrite my MBR I have lost access to all my operatings systems.  No that's a lie. I just regained access to one of the Windows by using fixmbr from the XP cd, and I can also re-access two other Windows installation via BIOS. Needless to say I'm way past the point of frustration.  I was just in the process of reinstalling Ubuntu 9.04 and Mint 7 trying to recover at least part of the 8-system bootloader that I used to have.  The last 3 attempts to reinstall Mint resulted in Grub 17 errors all 3 times.  Now I was just about to attempt to reinstall Ubuntu to see if that would work better.  Reinstalling is the only way I know to restore Grub without driving myself nuts with deciphering complex codes. Now I'm trying to reinstall Ubuntu 9.04 (not 9.10 with Grub2) on my first drive (SATA) along with Windows XP.  I select manual partitioning and after getting half wsy through I get this:

You are going to format the following partitions

Partition #3 of SCSI3 (0,0,0)  sda ext3
Partition #4 of SCSI4 (0,0,0)  sdb swap
Partition #5 of SCSI5 (0,0,0)  sdc swap
Partition #7 of SCSI6 (0,1,0)  sde swap

Would someone please translate this list into English. I would be forever grateful. Why is Ubuntu automatically creating 3 (three) swap partitions?  Actually, I didn't manually create either one. I just created the single 20gb main / ext3 partition and left around 8 gigs of free space for the rest.  Then I checked to see if it would proceed and it was willing to. The thing I'm worried about, though, is whether all this formatting is going to extend out of the single partition I started with and into other partitions on other disks or partitions containing other operating systems and/or data and, if so, what I should do about it. Thanks in advance for any comments or suggestions.

you have 3 swap partitions. get rid of 2 of them before proceeding with the install. When you install additional Linux OSs there is no need to create another swap partition, the installer will recognize the one you already have and configure the Linux OS you are installing to use the existing swap partition.

---

### Post by HeadHunter00 on 2009-11-22
> **archp2009 said:**
> Hello,

Sorry for being long-winded.

I used to have 8 operating systems (4 Linux, 4 Windows) on 5 drives - 4 SATA, 1 IDE.  Now thanks partly to a failed attempt of Grub to overwrite my MBR I have lost access to all my operatings systems.  No that's a lie. I just regained access to one of the Windows by using fixmbr from the XP cd, and I can also re-access two other Windows installation via BIOS. Needless to say I'm way past the point of frustration.  I was just in the process of reinstalling Ubuntu 9.04 and Mint 7 trying to recover at least part of the 8-system bootloader that I used to have.  The last 3 attempts to reinstall Mint resulted in Grub 17 errors all 3 times.  Now I was just about to attempt to reinstall Ubuntu to see if that would work better.  Reinstalling is the only way I know to restore Grub without driving myself nuts with deciphering complex codes. Now I'm trying to reinstall Ubuntu 9.04 (not 9.10 with Grub2) on my first drive (SATA) along with Windows XP.  I select manual partitioning and after getting half wsy through I get this:

You are going to format the following partitions

Partition #3 of SCSI3 (0,0,0)  sda ext3
Partition #4 of SCSI4 (0,0,0)  sdb swap
Partition #5 of SCSI5 (0,0,0)  sdc swap
Partition #7 of SCSI6 (0,1,0)  sde swap

Would someone please translate this list into English. I would be forever grateful. Why is Ubuntu automatically creating 3 (three) swap partitions?  Actually, I didn't manually create either one. I just created the single 20gb main / ext3 partition and left around 8 gigs of free space for the rest.  Then I checked to see if it would proceed and it was willing to. The thing I'm worried about, though, is whether all this formatting is going to extend out of the single partition I started with and into other partitions on other disks or partitions containing other operating systems and/or data and, if so, what I should do about it. Thanks in advance for any comments or suggestions.

partition 4, 5 and 6 are swap, meaning they hold temporary data and are only used when ram is filled up. Partition 3 is just a normal linux ext3 filesystem and is used by linux OSes the same way ntfs filesystems are used by windows. Thats pretty much all that I know about.

---

### Post by HeadHunter00 on 2009-11-22
By the way, you only need one swap.

---

### Post by archp2009 on 2009-11-23
Thanks very much for the replies. 
HeadHunter00: I understood that much.
Presence1960: When you say, "you have 3 swap partitions. get rid of 2 of them before proceeding," how exactly do I go about that?  When I click "back" I don't see the three partitions.  I just see the single main partition I created and a second partition marked free space.  When you say, "When you install additional Linux OSs there is no need to create another swap partition, the installer will recognize the one you already have and configure the Linux OS you are installing to use the existing swap partition," is that why there are three swaps appearing.  Are these the swaps on the other drives for the other Linux OS's that I can't presently access? Being that there are 3 swap partitions lying around on different drives, should I just use all the available space on the partition I am using for the ext3 operating system? Am I good to go with whatever Ubuntu chooses to do?  How much can I trust it to only format what it should format, i.e. not to format any data/files that I don't want deleted?  Thanks in advance for any further clarification.

---

### Post by presence1960 on 2009-11-23
> **archp2009 said:**
> Thanks very much for the replies. 
HeadHunter00: I understood that much.
Presence1960: When you say, "you have 3 swap partitions. get rid of 2 of them before proceeding," how exactly do I go about that?  When I click "back" I don't see the three partitions.  I just see the single main partition I created and a second partition marked free space.  When you say, "When you install additional Linux OSs there is no need to create another swap partition, the installer will recognize the one you already have and configure the Linux OS you are installing to use the existing swap partition," is that why there are three swaps appearing.  Are these the swaps on the other drives for the other Linux OS's that I can't presently access? Being that there are 3 swap partitions lying around on different drives, should I just use all the available space on the partition I am using for the ext3 operating system? Am I good to go with whatever Ubuntu chooses to do?  How much can I trust it to only format what it should format, i.e. not to format any data/files that I don't want deleted?  Thanks in advance for any further clarification.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by archp2009 on 2009-11-24
File was too large to attach and too many images to paste.

---

### Post by archp2009 on 2009-11-24
============================ Boot Info Summary: ==============================
  => Windows is installed in the MBR of /dev/sda  => Windows is installed in the MBR of /dev/sdb  => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive      in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.  => Windows is installed in the MBR of /dev/sdd  => Grub0.97 is installed in the MBR of /dev/sde and looks on the same drive      in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.  sda1: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:  Windows XP     Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr                         /NTDETECT.COM  sda2: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:     sda3: _________________________________________________________________________      File system:       Extended Partition     Boot sector type:  -     Boot sector info:    sda5: _________________________________________________________________________      File system:       swap     Boot sector type:  -     Boot sector info:    sda4: _________________________________________________________________________      File system:       ext3     Boot sector type:  -     Boot sector info:       Operating System:  Ubuntu 9.04     Boot files/dirs:   /boot/grub/menu.lst /etc/fstab  sdb1: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows XP     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:  Windows XP     Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM  sdb2: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:     sdb3: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:     sdb4: _________________________________________________________________________      File system:       Extended Partition     Boot sector type:  -     Boot sector info:    sdb5: _________________________________________________________________________      File system:       swap     Boot sector type:  -     Boot sector info:    sdb6: _________________________________________________________________________      File system:       ext3     Boot sector type:  Grub     Boot sector info:  Grub0.97 is installed in the boot sector of sdb6 and                         looks at sector 1366053992 of the same hard drive for                         the stage2 file. A stage2 file is at this location on                         /dev/sdb. Stage2 looks on partition #6 for                         /boot/grub/menu.lst.     Operating System:  Welcome to openSUSE 11.1 -                         Kernel ().     Boot files/dirs:   /boot/grub/menu.lst /etc/fstab  s

---

### Post by archp2009 on 2009-11-24
sdb7: _________________________________________________________________________      File system:       ext3     Boot sector type:  -     Boot sector info:       Operating System:       Boot files/dirs:     sdc1: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:     sdc2: _________________________________________________________________________      File system:       Extended Partition     Boot sector type:  -     Boot sector info:    sdc5: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows XP     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:     sdc6: _________________________________________________________________________      File system:       ext3     Boot sector type:  Grub     Boot sector info:  Grub0.97 is installed in the boot sector of sdc6 and                         looks at sector 159663839 of the same hard drive for                         the stage2 file. A stage2 file is at this location on                         /dev/sdc. Stage2 looks on partition #6 for                         /boot/grub/menu.lst.     Operating System:  Mandriva Linux release 2009.1                         (Official) for i586 Kernel 2.6.29.6-desktop586-1mnb on                         a Dual-processor i686 /     Boot files/dirs:   /boot/grub/menu.lst /etc/fstab  sdc7: _________________________________________________________________________      File system:       swap     Boot sector type:  Unknown     Boot sector info:

---

### Post by archp2009 on 2009-11-24
sdc8: _________________________________________________________________________      File system:       ext3     Boot sector type:  -     Boot sector info:       Operating System:       Boot files/dirs:     sdc3: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows XP     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:     sdd1: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows XP     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:  Windows Vista     Boot files/dirs:   /Windows/System32/winload.exe  sdd2: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:  Windows Vista     Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr  sdd3: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:     sdd4: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:     sde1: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:  Windows Vista     Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

---

### Post by archp2009 on 2009-11-24
sde2: _________________________________________________________________________      File system:       Extended Partition     Boot sector type:  -     Boot sector info:    sde5: _________________________________________________________________________      File system:       swap     Boot sector type:  -     Boot sector info:    sde3: _________________________________________________________________________      File system:       ext3     Boot sector type:  -     Boot sector info:       Operating System:  Ubuntu 9.04     Boot files/dirs:   /boot/grub/menu.lst /etc/fstab  sde4: _________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:       Operating System:       Boot files/dirs:     =========================== Drive/Partition Info: =============================  Drive: sda ___________________ _____________________________________________________  Disk /dev/sda: 320.0 GB, 320072933376 bytes 255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors Units = sectors of 1 * 512 = 512 bytes Disk identifier: 0x07510751  Partition  Boot         Start           End          Size  Id System  /dev/sda1    *             63   564,202,799   564,202,737   7 HPFS/NTFS /dev/sda2         564,202,800   564,283,124        80,325   7 HPFS/NTFS /dev/sda3         564,283,125   579,914,369    15,631,245   5 Extended /dev/sda5         564,283,188   579,914,369    15,631,182  82 Linux swap / Solaris /dev/sda4         579,914,370   618,984,449    39,070,080  83 Linux   Drive: sdb ___________________ _____________________________________________________  Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes 255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors Units = sectors of 1 * 512 = 512 bytes Disk identifier: 0x09490dc5  Partition  Boot         Start           End          Size  Id System  /dev/sdb1    *          2,048    40,962,047    40,960,000   7 HPFS/NTFS /dev/sdb2          40,962,048 1,064,962,047 1,024,000,000   7 HPFS/NTFS /dev/sdb3       1,418,299,392 1,953,525,119   535,225,728   7 HPFS/NTFS /dev/sdb4       1,331,202,048 1,418,299,391    87,097,344   5 Extended /dev/sdb5       1,331,202,096 1,335,396,383     4,194,288  82 Linux swap / Solaris /dev/sdb6       1,335,396,432 1,377,339,455    41,943,024  83 Linux /dev/sdb7       1,377,339,504 1,418,299,391    40,959,888  83 Linux

---

### Post by archp2009 on 2009-11-24
Drive: sdc ___________________ _____________________________________________________  Disk /dev/sdc: 640.1 GB, 640135028736 bytes 255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors Units = sectors of 1 * 512 = 512 bytes Disk identifier: 0x500b9b3f  Partition  Boot         Start           End          Size  Id System  /dev/sdc1    *             63    15,856,154    15,856,092   7 HPFS/NTFS /dev/sdc2          15,856,155   269,458,244   253,602,090   5 Extended /dev/sdc5          15,872,220   159,236,279   143,364,060   7 HPFS/NTFS /dev/sdc6         159,236,343   184,426,199    25,189,857  83 Linux /dev/sdc7         184,426,263   192,603,284     8,177,022  82 Linux swap / Solaris /dev/sdc8         192,603,348   269,458,244    76,854,897  83 Linux /dev/sdc3         269,458,308 1,250,258,813   980,800,506   7 HPFS/NTFS   Drive: sdd ___________________ _____________________________________________________  Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes 255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors Units = sectors of 1 * 512 = 512 bytes Disk identifier: 0x5d7d47e1  Partition  Boot         Start           End          Size  Id System  /dev/sdd1               2,048    63,326,207    63,324,160   7 HPFS/NTFS /dev/sdd2    *     63,328,230   107,105,354    43,777,125   7 HPFS/NTFS /dev/sdd3         107,105,355   778,202,616   671,097,262   7 HPFS/NTFS /dev/sdd4         778,204,665 1,953,520,064 1,175,315,400   7 HPFS/NTFS   Drive: sde ___________________ _____________________________________________________  Disk /dev/sde: 80.0 GB, 80026361856 bytes 255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors Units = sectors of 1 * 512 = 512 bytes Disk identifier: 0xba1a5abd  Partition  Boot         Start           End          Size  Id System  /dev/sde1    *             63   125,576,374   125,576,312   7 HPFS/NTFS /dev/sde2         125,580,105   133,387,694     7,807,590   5 Extended /dev/sde5         125,580,168   133,387,694     7,807,527  82 Linux swap / Solaris /dev/sde3         133,387,695   152,922,734    19,535,040  83 Linux /dev/sde4         152,922,735   156,296,384     3,373,650  83 Linux   blkid -c /dev/null: ____________________________________________________________  /dev/loop0: TYPE="squashfs"  /dev/sda1: UUID="0628CBA728CB9459" LABEL="XP32" TYPE="ntfs"  /dev/sda2: UUID="4E208D54208D43C5" TYPE="ntfs"  /dev/sda4: UUID="666c26ba-0fe2-4938-87bf-469783bf146e" SEC_TYPE="ext2" TYPE="ext3"  /dev/sda5: UUID="9d97498c-e003-46d4-b24a-70bd5c3bdd3a" TYPE="swap"  /dev/sdb1: UUID="823E2AB43E2AA161" LABEL="XP64" TYPE="ntfs"  /dev/sdb2: UUID="2D7EEE6F1366209C" LABEL="Server" TYPE="ntfs"  /dev/sdb3: UUID="24FE8453501D67B0" TYPE="ntfs"  /dev/sdb5: UUID="f7be76b7-60cc-4e9c-8a1c-3b164ca92d4a" TYPE="swap"  /dev/sdb6: UUID="1fd70a14-a507-40aa-9c59-046c25cda355" SEC_TYPE="ext2" TYPE="ext3"  /dev/sdb7: UUID="fb4fbc01-2e95-481f-bfc0-9fd9c5a96df9" SEC_TYPE="ext2" TYPE="ext3"  /dev/sdc1: UUID="4DEC9064196B76C6" TYPE="ntfs"  /dev/sdc3: UUID="901C34721C345606" LABEL="Vol_MOVIES" TYPE="ntfs"  /dev/sdc5: UUID="44E130AFA8CEA628" LABEL="Vol_F-Movies2" TYPE="ntfs"  /dev/sdc6: UUID="15a961f4-90a9-4905-b392-20fff44da061" SEC_TYPE="ext2" TYPE="ext3"  /dev/sdc7: UUID="dd58cd60-4923-494f-80d9-73525b53675d" TYPE="swap"  /dev/sdc8: UUID="92bdb8b9-1de1-46ca-899d-0f7c66b299fe" SEC_TYPE="ext2" TYPE="ext3"  /dev/sdd1: UUID="1680E14B80E13243" LABEL="VistaEtern32" TYPE="ntfs"  /dev/sdd2: UUID="10D2399DD239884C" LABEL="Win7" TYPE="ntfs"  /dev/sdd3: UUID="226AA1626AA13407" LABEL="Backups" TYPE="ntfs"  /dev/sdd4: UUID="5A0C57E40C57BA29" LABEL="Vol_movies3" TYPE="ntfs"  /dev/sde1: UUID="88285A6A285A56F2" LABEL="VistaEtern64" TYPE="ntfs"  /dev/sde3: UUID="0ee4a80f-0df5-4e24-9c57-bbbbce82806b" SEC_TYPE="ext2" TYPE="ext3"  /dev/sde4: UUID="a1d44f32-88d0-4e6f-874e-901ccdab2133" TYPE="ext4"  /dev/sde5: UUID="c964ca19-6737-4815-85f8-db7c687c46b4" TYPE="swap"

---

### Post by archp2009 on 2009-11-24
=============================== "mount" output: ===============================  proc on /proc type proc (rw) sysfs on /sys type sysfs (rw) tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755) tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755) tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755) varrun on /var/run type tmpfs (rw,nosuid,mode=0755) varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777) udev on /dev type tmpfs (rw,mode=0755) tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev) devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620) rootfs on / type rootfs (rw) /dev/sr0 on /cdrom type iso9660 (ro,noatime) /dev/loop0 on /rofs type squashfs (ro,noatime) fusectl on /sys/fs/fuse/connections type fusectl (rw) tmpfs on /tmp type tmpfs (rw,nosuid,nodev) binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)   ================================ sda1/boot.ini: ================================  [boot loader] ;timeout=3 default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS [operating systems] multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect ;C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons  =========================== sda4/boot/grub/menu.lst: ===========================  # menu.lst - See: grub(8), info grub, update-grub(8) #            grub-install(8), grub-floppy(8), #            grub-md5-crypt, /usr/share/doc/grub #            and /usr/share/doc/grub-doc/.  ## default num # Set the default entry to the entry number NUM. Numbering starts from 0, and # the entry number 0 is the default if the command is not used. # # You can specify 'saved' instead of a number. In this case, the default entry # is the entry saved with the command 'savedefault'. # WARNING: If you are using dmraid do not use 'savedefault' or your # array will desync and will not let you boot your system. default		1  ## timeout sec # Set a timeout, in SEC seconds, before automatically booting the default entry # (normally the first entry defined). timeout		5  ## hiddenmenu # Hides the menu by default (press ESC to see the menu) #hiddenmenu  # Pretty colours  color cyan/blue white/blue  ## password ['--md5'] passwd # If used in the first section of a menu file, disable all interactive editing # control (menu entry editor and command-line)  and entries protected by the # command 'lock' # e.g. password topsecret #      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/ # password topsecret  # # examples # # title		Windows 95/98/NT/2000 # root		(hd0,0) # makeactive # chainloader	+1 # # title		Linux # root		(hd0,1) # kernel	/vmlinuz root=/dev/hda2 ro #  # # Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST  ### BEGIN AUTOMAGIC KERNELS LIST ## lines between the AUTOMAGIC KERNELS LIST markers will be modified ## by the debian update-grub script except for the default options below  ## DO NOT UNCOMMENT THEM, Just edit them to your needs  ## ## Start Default Options ## ## default kernel options ## default kernel options for automagic boot options ## If you want special options for specific kernels use kopt_x_y_z ## where x.y.z is kernel version. Minor versions can be omitted. ## e.g. kopt=root=/dev/hda1 ro ##      kopt_2_6_8=root=/dev/hdc1 ro ##      kopt_2_6_8_2_686=root=/dev/hdc2 ro # kopt=root=UUID=666c26ba-0fe2-4938-87bf-469783bf146e ro  ## default grub root device ## e.g. groot=(hd0,0) # groot=666c26ba-0fe2-4938-87bf-469783bf146e  ## should update-grub create alternative automagic boot options ## e.g. alternative=true ##      alternative=false # alternative=true  ## should update-grub lock alternative automagic boot options ## e.g. lockalternative=true ##      lockalternative=false # lockalternative=false  ## additional options to use with the default boot option, but not with the ## alternatives ## e.g. defoptions=vga=791 resume=/dev/hda5 # defoptions=quiet splash  ## should update-grub lock old automagic boot options ## e.g. lockold=false ##      lockold=true # lockold=false  ## Xen hypervisor options to use with the default Xen boot option # xenhopt=  ## Xen Linux kernel options to use with the default Xen boot option # xenkopt=console=tty0  ## altoption boot targets option ## multiple altoptions lines are allowed ## e.g. altoptions=(extra menu suffix) extra boot options ##      altoptions=(recovery) single # altoptions=(recovery mode) single  ## controls how many kernels should be put into the menu.lst ## only counts the first occurence of a kernel, not the ## alternative kernel options ## e.g. howmany=all ##      howmany=7 # howmany=all  ## specify if running in Xen domU or have grub detect automatically ## update-grub will ignore non-xen kernels when running in domU and vice versa ## e.g. indomU=detect ##      indomU=true ##      indomU=false # indomU=detect  ## should update-grub create memtest86 boot option ## e.g. memtest86=true ##      memtest86=false # memtest86=true  ## should update-grub adjust the value of the default booted system ## can be true or false # updatedefaultentry=false  ## should update-grub add savedefault to the default options ## can be true or false # savedefault=false  ## ## End Default Options ##

---

### Post by archp2009 on 2009-11-24
# This is a divider, added to separate the menu items below from the Debian # ones. title		Windows operating systems: root   # This entry automatically added by the Debian installer for a non-linux OS # on /dev/sda1 title		Microsoft Windows XP Professional (32-bit) rootnoverify	(hd0,0) savedefault makeactive chainloader	+1   # This entry automatically added by the Debian installer for a non-linux OS # on /dev/sdb1 title		Microsoft Windows XP Professional (64-bit) rootnoverify	(hd1,0) savedefault makeactive map		(hd0) (hd1) map		(hd1) (hd0) chainloader	+1   # This entry automatically added by the Debian installer for a non-linux OS # on /dev/sde1 title        Microsoft Windows Vista (64-bit) rootnoverify    (hd4,0) savedefault makeactive map        (hd0) (hd4) map        (hd4) (hd0) chainloader    +1    # This is a divider, added to separate the menu items below from the Debian # ones. title		Linux operating systems: root   title		Ubuntu 9.04, kernel 2.6.28-16-generic uuid		666c26ba-0fe2-4938-87bf-469783bf146e kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=666c26ba-0fe2-4938-87bf-469783bf146e ro quiet splash  initrd		/boot/initrd.img-2.6.28-16-generic quiet  ## title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode) ## uuid		666c26ba-0fe2-4938-87bf-469783bf146e ## kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=666c26ba-0fe2-4938-87bf-469783bf146e ro  single ## initrd		/boot/initrd.img-2.6.28-16-generic  ## title		Ubuntu 9.04, kernel 2.6.28-11-generic ## uuid		666c26ba-0fe2-4938-87bf-469783bf146e ## kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=666c26ba-0fe2-4938-87bf-469783bf146e ro quiet splash  ## initrd		/boot/initrd.img-2.6.28-11-generic ## quiet  ## title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) ## uuid		666c26ba-0fe2-4938-87bf-469783bf146e ## kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=666c26ba-0fe2-4938-87bf-469783bf146e ro  single ## initrd		/boot/initrd.img-2.6.28-11-generic  ## title		Ubuntu 9.04, memtest86+ ## uuid		666c26ba-0fe2-4938-87bf-469783bf146e ## kernel		/boot/memtest86+.bin ## quiet   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdb6. title		openSUSE 11.1 - 2.6.27.37-0.1 (on /dev/sdb6) root		(hd1,5) kernel		/boot/vmlinuz-2.6.27.37-0.1-default root=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part6 resume=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part5 splash=silent showopts vga=0x317  initrd		/boot/initrd-2.6.27.37-0.1-default savedefault boot   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdb6. # title		Failsafe -- openSUSE 11.1 - 2.6.27.37-0.1 (on /dev/sdb6) # root		(hd1,5) # kernel		/boot/vmlinuz-2.6.27.37-0.1-default root=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part6 showopts ide=nodma apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317  # initrd		/boot/initrd-2.6.27.37-0.1-default # savedefault # boot   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdc6. # title		linux (on /dev/sdc6) # root		(hd2,5) # kernel		/boot/vmlinuz BOOT_IMAGE=linux root=UUID=15a961f4-90a9-4905-b392-20fff44da061  resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788  # initrd		(hd2,5)/boot/initrd.img # savedefault # boot

---

### Post by archp2009 on 2009-11-24
# This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdc6. # title		linux-nonfb (on /dev/sdc6) # root		(hd2,5) # kernel		/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d  # initrd		(hd2,5)/boot/initrd.img # savedefault # boot   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdc6. # title		failsafe (on /dev/sdc6) # root		(hd2,5) # kernel		/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=15a961f4-90a9-4905-b392-20fff44da061 failsafe  # initrd		(hd2,5)/boot/initrd.img # savedefault # boot   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdc6. # title		desktop586 2.6.29.1-4mnb (on /dev/sdc6) # root		(hd2,5) # kernel		/boot/vmlinuz-2.6.29.1-desktop586-4mnb BOOT_IMAGE=desktop586_2.6.29.1-4mnb  root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788  # initrd		(hd2,5)/boot/initrd-2.6.29.1-desktop586-4mnb.img # savedefault # boot   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdb7. # title		desktop586 2.6.29.6-1mnb (on /dev/sdc6) # root		(hd2,5) # kernel		/boot/vmlinuz-2.6.29.6-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.29.6-1mnb root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788  # initrd		(hd2,5)/boot/initrd-2.6.29.6-desktop586-1mnb.img # savedefault # boot   # This entry automatically added by the Debian installer for a non-linux OS # on /dev/sdd2 # title		Please use BIOS to change boot drive to 4M for Vista or Windows 7 # rootnoverify	(hd3,1) # savedefault # makeactive # map		(hd0) (hd3) # map		(hd3) (hd0) # chainloader	+1   # This entry automatically added by the Debian installer for a non-linux OS # on /dev/sde1 # title		Windows Vista (loader) # rootnoverify	(hd4,0) # savedefault # makeactive # map		(hd0) (hd4) # map		(hd4) (hd0) # chainloader	+1    # title Mandriva grub # root (hd2,5) # chainloader +1  # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdb7. title        Linux Mandriva One i586 KDE4(on /dev/sdb7) root        (hd1,6) kernel        /boot/vmlinuz BOOT_IMAGE=linux  root=UUID=15a961f4-90a9-4905-b392-20fff44da061  resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788 initrd (hd1,6)/boot/initrd.img savedefault boot   # This entry automatically added by the Debian installer for an existing   Mandriva installation on /dev/sdc6. #  title        Mandriva-nonfb (on /dev/sdc6) #  root        (hd2,5) #  kernel        /boot/vmlinuz BOOT_IMAGE=linux-nonfb  root=UUID=15a961f4-90a9-4905-b392-20fff44da061   resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d #  initrd        (hd2,5)/boot/initrd.img #  savedefault #  boot   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdc6. #  title        Mandriva failsafe (on /dev/sdc6) #  root        (hd2,5) #  kernel        /boot/vmlinuz BOOT_IMAGE=failsafe  root=UUID=15a961f4-90a9-4905-b392-20fff44da061 failsafe #  initrd        (hd2,5)/boot/initrd.img #  savedefault #  boot   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdc6. # title        Mandriva desktop586 2.6.29.1-4mnb (on /dev/sdc6) # root        (hd2,5) # kernel    /boot/vmlinuz-2.6.29.1-desktop586-4mnb  BOOT_IMAGE=desktop586_2.6.29.1-4mnb  root=UUID=15a961f4-90a9-4905-b392-20fff44da061 # resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788 # initrd        (hd2,5)/boot/initrd-2.6.29.1-desktop586-4mnb.img # savedefault # boot

---

### Post by archp2009 on 2009-11-24
# This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdc6. # title        Mandriva desktop586 2.6.29.6-1mnb (on /dev/sdc6) # root        (hd2,5) # kernel    /boot/vmlinuz-2.6.29.6-desktop586-1mnb  BOOT_IMAGE=desktop586_2.6.29.6-1mnb  root=UUID=15a961f4-90a9-4905-b392-20fff44da061 # resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788 # initrd        (hd2,5)/boot/initrd-2.6.29.6-desktop586-1mnb.img # savedefault # boot        # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sde5. title		Linux Mint 7 Gloria x64 (on /dev/sde5) root		(hd4,4) kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sde5 ro quiet splash  initrd		/boot/initrd.img-2.6.28-11-generic savedefault boot  ### END DEBIAN AUTOMAGIC KERNELS LIST   =============================== sda4/etc/fstab: ===============================  # /etc/fstab: static file system information. # # Use 'vol_id --uuid' to print the universally unique identifier for a # device; this may be used with UUID= as a more robust way to name devices # that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    defaults        0       0 # / was on /dev/sda4 during installation UUID=666c26ba-0fe2-4938-87bf-469783bf146e /               ext3    relatime,errors=remount-ro 0       1 # swap was on /dev/sda5 during installation UUID=9d97498c-e003-46d4-b24a-70bd5c3bdd3a none            swap    sw              0       0 # swap was on /dev/sdb5 during installation UUID=f7be76b7-60cc-4e9c-8a1c-3b164ca92d4a none            swap    sw              0       0 # swap was on /dev/sdc7 during installation UUID=dd58cd60-4923-494f-80d9-73525b53675d none            swap    sw              0       0 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0  =================== sda4: Location of files loaded by Grub: ===================    298.4GB: boot/grub/menu.lst  298.4GB: boot/grub/stage2  297.8GB: boot/initrd.img-2.6.28-11-generic  297.8GB: boot/initrd.img-2.6.28-16-generic  297.7GB: boot/vmlinuz-2.6.28-11-generic  297.8GB: boot/vmlinuz-2.6.28-16-generic  297.8GB: initrd.img  297.8GB: initrd.img.old  297.8GB: vmlinuz  297.7GB: vmlinuz.old  ================================ sdb1/boot.ini: ================================  [boot loader] timeout=20 default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS [operating systems] multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect  =========================== sdb6/boot/grub/menu.lst: ===========================  # Modified by YaST2. Last modification on Sun Nov  8 21:22:52 NST 2009 default 0 timeout 8 gfxmenu (hd0,5)/boot/message ##YaST - activate  ###Don't change this comment - YaST2 identifier: Original name: linux### title openSUSE 11.1 - 2.6.27.37-0.1     root (hd0,5)     kernel /boot/vmlinuz-2.6.27.37-0.1-default root=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part6 resume=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part5 splash=silent showopts vga=0x317     initrd /boot/initrd-2.6.27.37-0.1-default  ###Don't change this comment - YaST2 identifier: Original name: failsafe### title Failsafe -- openSUSE 11.1 - 2.6.27.37-0.1     root (hd0,5)     kernel /boot/vmlinuz-2.6.27.37-0.1-default root=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part6 showopts ide=nodma apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317     initrd /boot/initrd-2.6.27.37-0.1-default  ###Don't change this comment - YaST2 identifier: Original name: windows 1### title windows 1     rootnoverify (hd0,0)     chainloader +1  ###Don't change this comment - YaST2 identifier: Original name: windows 2### title windows 2     rootnoverify (hd0,1)     chainloader +1  ###Don't change this comment - YaST2 identifier: Original name: windows 3### title windows 3     rootnoverify (hd0,2)     chainloader +1  ###Don't change this comment - YaST2 identifier: Original name: floppy### title Floppy     rootnoverify (fd0)     chainloader +1

---

### Post by archp2009 on 2009-11-24
=============================== sdb6/etc/fstab: ===============================  /dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part5 swap                 swap       defaults              0 0 /dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part6 /                    ext3       acl,user_xattr        1 1 /dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part1 /windows/C           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0 /dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part2 /windows/D           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0 /dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part3 /windows/E           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0 proc                 /proc                proc       defaults              0 0 sysfs                /sys                 sysfs      noauto                0 0 debugfs              /sys/kernel/debug    debugfs    noauto                0 0 devpts               /dev/pts             devpts     mode=0620,gid=5       0 0  =================== sdb6: Location of files loaded by Grub: ===================    699.4GB: boot/grub/menu.lst  699.3GB: boot/grub/stage2  699.3GB: boot/initrd  699.3GB: boot/initrd-2.6.27.37-0.1-default  699.3GB: boot/vmlinuz  699.3GB: boot/vmlinuz-2.6.27.37-0.1-default  =========================== sdc6/boot/grub/menu.lst: ===========================  timeout 5 color black/cyan yellow/cyan gfxmenu (h2,5)/boot/gfxmenu default 0  title linux kernel (hd2,5)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788 initrd (hd2,5)/boot/initrd.img  title linux-nonfb kernel (hd2,5)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d initrd (hd2,5)/boot/initrd.img  title failsafe kernel (hd2,5)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=15a961f4-90a9-4905-b392-20fff44da061 failsafe initrd (hd2,5)/boot/initrd.img  title desktop586 2.6.29.1-4mnb kernel (hd2,5)/boot/vmlinuz-2.6.29.1-desktop586-4mnb BOOT_IMAGE=desktop586_2.6.29.1-4mnb root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788 initrd (hd2,5)/boot/initrd-2.6.29.1-desktop586-4mnb.img  title desktop586 2.6.29.6-1mnb kernel (hd2,5)/boot/vmlinuz-2.6.29.6-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.29.6-1mnb root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788 initrd (hd2,5)/boot/initrd-2.6.29.6-desktop586-1mnb.img  =============================== sdc6/etc/fstab: ===============================  # Entry for /dev/sda6 : UUID=15a961f4-90a9-4905-b392-20fff44da061 / ext3 defaults 1 1 # Entry for /dev/sda8 : UUID=92bdb8b9-1de1-46ca-899d-0f7c66b299fe /home ext3 defaults 1 2 none /proc proc defaults 0 0 # Entry for /dev/sda7 : UUID=dd58cd60-4923-494f-80d9-73525b53675d swap swap defaults 0 0  =================== sdc6: Location of files loaded by Grub: ===================     81.6GB: boot/grub/menu.lst   81.7GB: boot/grub/stage2   81.6GB: boot/initrd-2.6.29.1-desktop586-4mnb.img   81.7GB: boot/initrd-2.6.29.6-desktop586-1mnb.img   81.7GB: boot/initrd.img   81.7GB: boot/vmlinuz   81.6GB: boot/vmlinuz-2.6.29.1-desktop586-4mnb   81.7GB: boot/vmlinuz-2.6.29.6-desktop586-1mnb   81.7GB: boot/vmlinuz-2.6.29.6-desktop586-2mnb   81.7GB: boot/vmlinuz-desktop586  =========================== sde3/boot/grub/menu.lst: ===========================  # menu.lst - See: grub(8), info grub, update-grub(8) #            grub-install(8), grub-floppy(8), #            grub-md5-crypt, /usr/share/doc/grub #            and /usr/share/doc/grub-legacy-doc/.  ## default num # Set the default entry to the entry number NUM. Numbering starts from 0, and # the entry number 0 is the default if the command is not used. # # You can specify 'saved' instead of a number. In this case, the default entry # is the entry saved with the command 'savedefault'. # WARNING: If you are using dmraid do not change this entry to 'saved' or your # array will desync and will not let you boot your system. default		0  ## Graphical boot menu location gfxmenu=/boot/gfxmenu/linuxmint.message  ## timeout sec # Set a timeout, in SEC seconds, before automatically booting the default entry # (normally the first entry defined). timeout		10  # Pretty colours color cyan/blue white/blue  ## password ['--md5'] passwd # If used in the first section of a menu file, disable all interactive editing # control (menu entry editor and command-line)  and entries protected by the # command 'lock' # e.g. password topsecret #      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/ # password topsecret  # # examples # # title		Windows 95/98/NT/2000 # root		(hd0,0) # makeactive # chainloader	+1 # # title		Linux # root		(hd0,1) # kernel	/vmlinuz root=/dev/hda2 ro #  # # Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST  ### BEGIN AUTOMAGIC KERNELS LIST ## lines between the AUTOMAGIC KERNELS LIST markers will be modified ## by the debian update-grub script except for the default options below  ## DO NOT UNCOMMENT THEM, Just edit them to your needs  ## ## Start Default Options ## ## default kernel options ## default kernel options for automagic boot options ## If you want special options for specific kernels use kopt_x_y_z ## where x.y.z is kernel version. Minor versions can be omitted. ## e.g. kopt=root=/dev/hda1 ro ##      kopt_2_6_8=root=/dev/hdc1 ro ##      kopt_2_6_8_2_686=root=/dev/hdc2 ro # kopt=root=/dev/sde3 ro  ## default grub root device ## e.g. groot=(hd0,0) # groot=(hd4,2)  ## should update-grub create alternative automagic boot options ## e.g. alternative=true ##      alternative=false # alternative=true  ## should update-grub lock alternative automagic boot options ## e.g. lockalternative=true ##      lockalternative=false # lockalternative=false  ## additional options to use with the default boot option, but not with the ## alternatives ## e.g. defoptions=vga=791 resume=/dev/hda5 # defoptions=quiet splash  ## should update-grub lock old automagic boot options ## e.g. lockold=false ##      lockold=true # lockold=false  ## Xen hypervisor options to use with the default Xen boot option # xenhopt=  ## Xen Linux kernel options to use with the default Xen boot option # xenkopt=console=tty0  ## altoption boot targets option ## multiple altoptions lines are allowed ## e.g. altoptions=(extra menu suffix) extra boot options ##      altoptions=(single-user) single # altoptions=(recovery mode) single  ## controls how many kernels should be put into the menu.lst ## only counts the first occurence of a kernel, not the ## alternative kernel options ## e.g. howmany=all ##      howmany=7 # howmany=all  ## specify if running in Xen domU or have grub detect automatically ## update-grub will ignore non-xen kernels when running in domU and vice versa ## e.g. indomU=detect ##      indomU=true ##      indomU=false # indomU=detect  ## should update-grub create memtest86 boot option ## e.g. memtest86=true ##      memtest86=false # memtest86=true  ## should update-grub adjust the value of the default booted system ## can be true or false # updatedefaultentry=false  ## should update-grub add savedefault to the default options ## can be true or false # savedefault=false  ## ## End Default Options ##

---

### Post by archp2009 on 2009-11-24
title		Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic root		(hd4,2) kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sde3 ro quiet splash  initrd		/boot/initrd.img-2.6.28-11-generic quiet  title		Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic (recovery mode) root		(hd4,2) kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sde3 ro single initrd		/boot/initrd.img-2.6.28-11-generic  title		Linux Mint 7 Gloria x64, memtest86+ root		(hd4,2) kernel		/boot/memtest86+.bin quiet  ### END DEBIAN AUTOMAGIC KERNELS LIST  # This is a divider, added to separate the menu items below from the Debian # ones. title		Other operating systems: root   # This entry automatically added by the Debian installer for a non-linux OS # on /dev/sda1 title		Windows Vista (loader) rootnoverify	(hd0,0) savedefault makeactive chainloader	+1   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sda4. title		Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sda4) root		(hd0,3) kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=666c26ba-0fe2-4938-87bf-469783bf146e ro quiet splash  initrd		/boot/initrd.img-2.6.28-16-generic savedefault boot   # This entry automatically added by the Debian installer for a non-linux OS # on /dev/sdb1 title		Microsoft Windows XP Professional rootnoverify	(hd1,0) savedefault makeactive map		(hd0) (hd1) map		(hd1) (hd0) chainloader	+1   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdb6. title		openSUSE 11.1 - 2.6.27.37-0.1 (on /dev/sdb6) root		(hd1,5) kernel		/boot/vmlinuz-2.6.27.37-0.1-default root=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part6 resume=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part5 splash=silent showopts vga=0x317  initrd		/boot/initrd-2.6.27.37-0.1-default savedefault boot   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdb6. title		Failsafe -- openSUSE 11.1 - 2.6.27.37-0.1 (on /dev/sdb6) root		(hd1,5) kernel		/boot/vmlinuz-2.6.27.37-0.1-default root=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part6 showopts ide=nodma apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317  initrd		/boot/initrd-2.6.27.37-0.1-default savedefault boot   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdc6. title		linux (on /dev/sdc6) root		(hd2,5) kernel		/boot/vmlinuz BOOT_IMAGE=linux root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788  initrd		(hd2,5)/boot/initrd.img savedefault boot   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdc6. title		linux-nonfb (on /dev/sdc6) root		(hd2,5) kernel		/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d  initrd		(hd2,5)/boot/initrd.img savedefault boot   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdc6. title		failsafe (on /dev/sdc6) root		(hd2,5) kernel		/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=15a961f4-90a9-4905-b392-20fff44da061 failsafe  initrd		(hd2,5)/boot/initrd.img savedefault boot

---

### Post by archp2009 on 2009-11-24
title		Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic root		(hd4,2) kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sde3 ro quiet splash  initrd		/boot/initrd.img-2.6.28-11-generic quiet  title		Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic (recovery mode) root		(hd4,2) kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sde3 ro single initrd		/boot/initrd.img-2.6.28-11-generic  title		Linux Mint 7 Gloria x64, memtest86+ root		(hd4,2) kernel		/boot/memtest86+.bin quiet  ### END DEBIAN AUTOMAGIC KERNELS LIST  # This is a divider, added to separate the menu items below from the Debian # ones. title		Other operating systems: root   # This entry automatically added by the Debian installer for a non-linux OS # on /dev/sda1 title		Windows Vista (loader) rootnoverify	(hd0,0) savedefault makeactive chainloader	+1   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sda4. title		Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sda4) root		(hd0,3) kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=666c26ba-0fe2-4938-87bf-469783bf146e ro quiet splash  initrd		/boot/initrd.img-2.6.28-16-generic savedefault boot   # This entry automatically added by the Debian installer for a non-linux OS # on /dev/sdb1 title		Microsoft Windows XP Professional rootnoverify	(hd1,0) savedefault makeactive map		(hd0) (hd1) map		(hd1) (hd0) chainloader	+1   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdb6. title		openSUSE 11.1 - 2.6.27.37-0.1 (on /dev/sdb6) root		(hd1,5) kernel		/boot/vmlinuz-2.6.27.37-0.1-default root=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part6 resume=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part5 splash=silent showopts vga=0x317  initrd		/boot/initrd-2.6.27.37-0.1-default savedefault boot   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdb6. title		Failsafe -- openSUSE 11.1 - 2.6.27.37-0.1 (on /dev/sdb6) root		(hd1,5) kernel		/boot/vmlinuz-2.6.27.37-0.1-default root=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part6 showopts ide=nodma apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317  initrd		/boot/initrd-2.6.27.37-0.1-default savedefault boot   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdc6. title		linux (on /dev/sdc6) root		(hd2,5) kernel		/boot/vmlinuz BOOT_IMAGE=linux root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788  initrd		(hd2,5)/boot/initrd.img savedefault boot   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdc6. title		linux-nonfb (on /dev/sdc6) root		(hd2,5) kernel		/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d  initrd		(hd2,5)/boot/initrd.img savedefault boot   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdc6. title		failsafe (on /dev/sdc6) root		(hd2,5) kernel		/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=15a961f4-90a9-4905-b392-20fff44da061 failsafe  initrd		(hd2,5)/boot/initrd.img savedefault boot   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdc6. title		desktop586 2.6.29.1-4mnb (on /dev/sdc6) root		(hd2,5) kernel		/boot/vmlinuz-2.6.29.1-desktop586-4mnb BOOT_IMAGE=desktop586_2.6.29.1-4mnb root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788  initrd		(hd2,5)/boot/initrd-2.6.29.1-desktop586-4mnb.img savedefault boot   # This entry automatically added by the Debian installer for an existing # linux installation on /dev/sdc6. title		desktop586 2.6.29.6-1mnb (on /dev/sdc6) root		(hd2,5) kernel		/boot/vmlinuz-2.6.29.6-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.29.6-1mnb root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788  initrd		(hd2,5)/boot/initrd-2.6.29.6-desktop586-1mnb.img savedefault boot   # This entry automatically added by the Debian installer for a non-linux OS # on /dev/sdd2 title		Windows Vista (loader) rootnoverify	(hd3,1) savedefault makeactive map		(hd0) (hd3) map		(hd3) (hd0) chainloader	+1   # This entry automatically added by the Debian installer for a non-linux OS # on /dev/sde1 title		Windows Vista (loader) rootnoverify	(hd4,0) savedefault makeactive map		(hd0) (hd4) map		(hd4) (hd0) chainloader	+1   =============================== sde3/etc/fstab: ===============================  # /etc/fstab: static file system information. # # Use 'vol_id --uuid' to print the universally unique identifier for a # device; this may be used with UUID= as a more robust way to name devices # that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    defaults        0       0 # / was on /dev/sde3 during installation UUID=0ee4a80f-0df5-4e24-9c57-bbbbce82806b /               ext3    relatime,errors=remount-ro 0       1 # /home was on /dev/sde4 during installation UUID=a1d44f32-88d0-4e6f-874e-901ccdab2133 /home           ext4    relatime        0       2 # swap was on /dev/sda5 during installation UUID=9d97498c-e003-46d4-b24a-70bd5c3bdd3a none            swap    sw              0       0 # swap was on /dev/sdb5 during installation UUID=f7be76b7-60cc-4e9c-8a1c-3b164ca92d4a none            swap    sw              0       0 # swap was on /dev/sdc7 during installation UUID=dd58cd60-4923-494f-80d9-73525b53675d none            swap    sw              0       0 # swap was on /dev/sde5 during installation UUID=c964ca19-6737-4815-85f8-db7c687c46b4 none            swap    sw              0       0 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0  =================== sde3: Location of files loaded by Grub: ===================     69.0GB: boot/grub/menu.lst   69.0GB: boot/grub/stage2   68.7GB: boot/initrd.img-2.6.28-11-generic   68.8GB: boot/vmlinuz-2.6.28-11-generic   68.7GB: initrd.img   68.8GB: vmlinuz =========================== Unknown MBRs/Boot Sectors/etc =======================  Unknown BootLoader  on sdc7  00000000  71 d1 0e db 13 40 7c 00  00 00 4f 8a 28 fe 4d 6d  |q....@|...O.(.Mm| 00000010  4d c0 be dd 68 d7 cc ec  20 42 32 6f f9 c9 8c de  |M...h... B2o....| 00000020  ba 0a c4 a2 19 b1 8b 7d  ff 05 04 02 7d 38 19 42  |.......}....}8.B| 00000030  38 84 c4 12 1b 54 dd 27  36 8c 60 d5 0c 8e 5a 9b  |8....T.'6.`...Z.| 00000040  83 b5 22 ad 5a df c2 7f  d2 1d 04 20 08 f8 3a 0a  |..".Z...... ..:.| 00000050  0a 3a 48 49 12 e0 09 b6  2f 3e 34 69 c5 f6 8f a2  |.:HI..../>4i....| 00000060  1e 3d 15 35 01 2a fa 42  51 94 1d cc 1d e9 41 2f  |.=.5.*.BQ.....A/| 00000070  03 9f 85 f8 06 87 f8 b4  b0 0b 9b a5 c9 b2 a1 a7  |................| 00000080  50 4c b6 8b 84 b0 5c cb  3b a6 db 75 2d 12 53 ba  |PL....\.;..u-.S.| 00000090  31 d3 d3 db 4a da 72 22  33 1b 93 fc 87 d2 4f e3  |1...J.r"3.....O.| 000000a0  67 e4 5c 75 e3 54 17 81  ef 24 e9 ea c5 ec 14 20  |g.\u.T...$..... | 000000b0  bb 10 72 90 28 51 08 ef  60 35 c4 29 5c 11 2d 51  |..r.(Q..`5.)\.-Q| 000000c0  16 d1 3a 6f 60 ac 96 e0  f8 6b 5d 1c 35 32 f5 cb  |..:o`....k].52..| 000000d0  a1 a3 55 c8 4f d1 8f 67  1e 27 47 aa 29 ac e5 a2  |..U.O..g.'G.)...| 000000e0  90 0b 8e d6 ea 6f 9a dc  35 32 b5 97 33 87 2b ac  |.....o..52..3.+.| 000000f0  7a 8c 7d 1a f0 ab 6e cd  c6 0f 47 47 63 6c 58 cc  |z.}...n...GGclX.| 00000100  ea b6 34 8d 3d 60 f8 00  80 5b ea f4 7a 44 4c f9  |..4.=`...[..zDL.| 00000110  d2 58 55 e1 53 7c a6 c1  0b 0e 61 3e a6 96 a0 ca  |.XU.S|....a>....| 00000120  58 2d 9f fe 93 f8 06 2b  ea a8 01 c7 c5 29 cd f6  |X-.....+.....)..| 00000130  56 a0 9a 22 00 3f 42 ab  c7 1a a3 4e 03 7c 57 ee  |V..".?B....N.|W.| 00000140  f4 80 2b 88 3a a3 64 21  2b 98 78 ca 52 a3 66 16  |..+.:.d!+.x.R.f.| 00000150  35 44 0b 9f 39 4e 2b 6c  b8 89 87 a0 84 41 c3 d8  |5D..9N+l.....A..| 00000160  eb 38 b3 3f 49 c2 b4 79  49 bc 79 87 c4 fd ed 60  |.8.?I..yI.y....`| 00000170  69 79 f8 95 79 af cf c3  c7 f0 0f b1 f1 3a 66 20  |iy..y........:f | 00000180  f5 4f 2d d2 b3 52 07 57  ab 83 64 a4 39 34 8b ce  |.O-..R.W..d.94..| 00000190  3e 8f d0 8e d9 72 ea 05  12 9f d2 aa 57 2e 2a dd  |>....r......W.*.| 000001a0  97 f8 26 ce 65 84 1e 49  cd f5 e5 31 39 cb 8e 36  |..&.e..I...19..6| 000001b0  29 01 84 49 f8 07 1e 4b  1d 9d f1 6d 89 d5 00 ca  |)..I...K...m....| 000001c0  01 0a 3b fd b1 92 95 7d  a4 ad 36 b9 d8 4b 35 56  |..;....}..6..K5V| 000001d0  bd c9 5a b5 2c 63 90 eb  fc 3b 27 58 e8 eb 54 0c  |..Z.,c...;'X..T.| 000001e0  e6 9a 2b 6e 9b 97 84 95  92 37 11 8d 32 da 47 57  |..+n.....7..2.GW| 000001f0  39 cf 43 9f e1 d5 4a c7  44 ca 81 97 52 bd 8d 31  |9.C...J.D...R..1| 00000200   =======Devices which don't seem to have a corresponding hard drive==============  sdf sdg

---

### Post by archp2009 on 2009-11-24
That's the end.  I think I got it all but the format is messed up.  If there's a better way to attach that results.txt file, please advise.

---

### Post by lisati on 2009-11-24
> **archp2009 said:**
> That's the end.  I think I got it all but the format is messed up.  If there's a better way to attach that results.txt file, please advise.

Suggestion: put [noparse]```
[/noparse] at the start of what you're quoting, and a matching [noparse]
```[/noparse] at the end of the quote. That can help make it easier for use to read.
There are some other options. For more information read here:
[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by presence1960 on 2009-11-24
> **archp2009 said:**
> That's the end.  I think I got it all but the format is messed up.  If there's a better way to attach that results.txt file, please advise.

RE: see highlighted text in my original directions-

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. **_Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text._**

Like this:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub1.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sdc6 and looks 
                       at sector 159957180 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdc7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x85858585

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   488,392,064   488,392,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00072abb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02020202

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    83,891,429    83,891,367   7 HPFS/NTFS
/dev/sdc2          83,891,430   167,782,859    83,891,430   5 Extended
/dev/sdc5          83,891,493    92,277,359     8,385,867  82 Linux swap / Solaris
/dev/sdc6          92,277,423   130,030,109    37,752,687  83 Linux
/dev/sdc7         130,030,173   167,782,859    37,752,687  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="data" UUID="ca51ec3c-d4d9-44a6-823c-162ede8e5184" TYPE="ext3" 
/dev/sdb1: LABEL="backup" UUID="e759faab-0d70-4270-ba1f-ac046a37c392" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="AE542F2F542EF9AB" LABEL="xp" TYPE="ntfs" 
/dev/sdc5: UUID="a7907e24-9e12-4b51-8d78-7995579d955a" TYPE="swap" 
/dev/sdc6: LABEL="jaunty" UUID="f31336b1-0908-4580-aad2-6b04ac995b9b" TYPE="ext4" 
/dev/sdc7: LABEL="karmic" UUID="36d96022-7809-48c5-b527-7c7a156f8480" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sdc7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/raz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=raz)
/dev/sda1 on /media/data type ext3 (rw,nosuid,nodev,uhelper=devkit)


================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=========================== sdc6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		4

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f31336b1-0908-4580-aad2-6b04ac995b9b

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

#title		Ubuntu 9.04, kernel 2.6.28-13-generic
#uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
#kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-13-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
#uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
#kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  single
#initrd		/boot/initrd.img-2.6.28-13-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
chainloader	+1

title           Ubuntu Karmic Koala
rootnoverify    (hd0,7)
chainloader     +1


=========================== sdc6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd2,6)
search --fs-uuid --set f31336b1-0908-4580-aad2-6b04ac995b9b
if font /usr/share/grub/ascii.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
set root=(hd2,6)
search --fs-uuid --set f31336b1-0908-4580-aad2-6b04ac995b9b
menuentry "Ubuntu, linux 2.6.28-16-generic" {
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, linux 2.6.28-16-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro single 
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, linux 2.6.28-15-generic" {
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, linux 2.6.28-15-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro single 
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, linux 2.6.28-13-generic" {
	linux	/boot/vmlinuz-2.6.28-13-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  quiet splash
	initrd	/boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu, linux 2.6.28-13-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-13-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro single 
	initrd	/boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic" {
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro single 
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
	set root=(hd2,1)
	chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdc7)" {
	set root=(hd2,7)
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=3e4ff0dd-b3af-42a8-ba71-5771e5fbfcf0 ro quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdc7)" {
	set root=(hd2,7)
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=3e4ff0dd-b3af-42a8-ba71-5771e5fbfcf0 ro single
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdc7)" {
	set root=(hd2,7)
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdc8)" {
	set root=(hd2,8)
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=c9545759-d324-4ebd-936a-d0e99ac465d1 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdc8)" {
	set root=(hd2,8)
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=c9545759-d324-4ebd-936a-d0e99ac465d1 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
### END /etc/grub.d/40_custom ###

=============================== sdc6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc6 during installation
UUID=f31336b1-0908-4580-aad2-6b04ac995b9b /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=a7907e24-9e12-4b51-8d78-7995579d955a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc6: Location of files loaded by Grub: ===================


  47.2GB: boot/grub/grub.cfg
  47.2GB: boot/grub/menu.lst
  47.2GB: boot/grub/stage2
  47.2GB: boot/initrd.img-2.6.28-11-generic
  47.2GB: boot/initrd.img-2.6.28-13-generic
  47.2GB: boot/initrd.img-2.6.28-15-generic
  47.2GB: boot/initrd.img-2.6.28-16-generic
  47.2GB: boot/vmlinuz-2.6.28-11-generic
  47.2GB: boot/vmlinuz-2.6.28-13-generic
  47.2GB: boot/vmlinuz-2.6.28-15-generic
  47.2GB: boot/vmlinuz-2.6.28-16-generic
  47.2GB: initrd.img
  47.2GB: initrd.img.old
  47.2GB: vmlinuz
  47.2GB: vmlinuz.old

=========================== sdc7/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=36d96022-7809-48c5-b527-7c7a156f8480 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=36d96022-7809-48c5-b527-7c7a156f8480

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-15-server
uuid		36d96022-7809-48c5-b527-7c7a156f8480
kernel		/boot/vmlinuz-2.6.31-15-server root=UUID=36d96022-7809-48c5-b527-7c7a156f8480 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-server

title		Ubuntu 9.10, kernel 2.6.31-15-server (recovery mode)
uuid		36d96022-7809-48c5-b527-7c7a156f8480
kernel		/boot/vmlinuz-2.6.31-15-server root=UUID=36d96022-7809-48c5-b527-7c7a156f8480 ro  single
initrd		/boot/initrd.img-2.6.31-15-server

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		36d96022-7809-48c5-b527-7c7a156f8480
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=36d96022-7809-48c5-b527-7c7a156f8480 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		36d96022-7809-48c5-b527-7c7a156f8480
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=36d96022-7809-48c5-b527-7c7a156f8480 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		36d96022-7809-48c5-b527-7c7a156f8480
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=36d96022-7809-48c5-b527-7c7a156f8480 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		36d96022-7809-48c5-b527-7c7a156f8480
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=36d96022-7809-48c5-b527-7c7a156f8480 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		36d96022-7809-48c5-b527-7c7a156f8480
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		36d96022-7809-48c5-b527-7c7a156f8480
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdc7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd2,7)
search --no-floppy --fs-uuid --set 36d96022-7809-48c5-b527-7c7a156f8480
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd2,7)
	search --no-floppy --fs-uuid --set 36d96022-7809-48c5-b527-7c7a156f8480
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=36d96022-7809-48c5-b527-7c7a156f8480 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,7)
	search --no-floppy --fs-uuid --set 36d96022-7809-48c5-b527-7c7a156f8480
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=36d96022-7809-48c5-b527-7c7a156f8480 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd2,7)
	search --no-floppy --fs-uuid --set 36d96022-7809-48c5-b527-7c7a156f8480
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=36d96022-7809-48c5-b527-7c7a156f8480 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,7)
	search --no-floppy --fs-uuid --set 36d96022-7809-48c5-b527-7c7a156f8480
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=36d96022-7809-48c5-b527-7c7a156f8480 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
	insmod ntfs
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set ae542f2f542ef9ab
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sdc6)" {
	insmod ext2
	set root=(hd2,6)
	search --no-floppy --fs-uuid --set f31336b1-0908-4580-aad2-6b04ac995b9b
	linux /boot/vmlinuz-2.6.28-16-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash
	initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode) (on /dev/sdc6)" {
	insmod ext2
	set root=(hd2,6)
	search --no-floppy --fs-uuid --set f31336b1-0908-4580-aad2-6b04ac995b9b
	linux /boot/vmlinuz-2.6.28-16-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro single
	initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sdc6)" {
	insmod ext2
	set root=(hd2,6)
	search --no-floppy --fs-uuid --set f31336b1-0908-4580-aad2-6b04ac995b9b
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sdc6)" {
	insmod ext2
	set root=(hd2,6)
	search --no-floppy --fs-uuid --set f31336b1-0908-4580-aad2-6b04ac995b9b
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro single
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdc6)" {
	insmod ext2
	set root=(hd2,6)
	search --no-floppy --fs-uuid --set f31336b1-0908-4580-aad2-6b04ac995b9b
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc7 during installation
UUID=36d96022-7809-48c5-b527-7c7a156f8480 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=a7907e24-9e12-4b51-8d78-7995579d955a none            swap    sw              0       0

=================== sdc7: Location of files loaded by Grub: ===================


  66.5GB: boot/grub/grub.cfg
  66.5GB: boot/grub/menu.lst
  66.5GB: boot/initrd.img-2.6.31-14-generic
  66.5GB: boot/initrd.img-2.6.31-15-generic
  66.5GB: boot/vmlinuz-2.6.31-14-generic
  66.5GB: boot/vmlinuz-2.6.31-15-generic
  66.5GB: initrd.img.old
  66.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

---

### Post by archp2009 on 2009-11-24
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdd
 => Grub0.97 is installed in the MBR of /dev/sde and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb6 and 
                       looks at sector 1366053992 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Welcome to openSUSE 11.1 - 
                       Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdc6 and 
                       looks at sector 159663839 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Mandriva Linux release 2009.1 
                       (Official) for i586 Kernel 2.6.29.6-desktop586-1mnb on 
                       a Dual-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sdc8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdd3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sde2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sde4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07510751

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   564,202,799   564,202,737   7 HPFS/NTFS
/dev/sda2         564,202,800   564,283,124        80,325   7 HPFS/NTFS
/dev/sda3         564,283,125   579,914,369    15,631,245   5 Extended
/dev/sda5         564,283,188   579,914,369    15,631,182  82 Linux swap / Solaris
/dev/sda4         579,914,370   618,984,449    39,070,080  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x09490dc5

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    40,962,047    40,960,000   7 HPFS/NTFS
/dev/sdb2          40,962,048 1,064,962,047 1,024,000,000   7 HPFS/NTFS
/dev/sdb3       1,418,299,392 1,953,525,119   535,225,728   7 HPFS/NTFS
/dev/sdb4       1,331,202,048 1,418,299,391    87,097,344   5 Extended
/dev/sdb5       1,331,202,096 1,335,396,383     4,194,288  82 Linux swap / Solaris
/dev/sdb6       1,335,396,432 1,377,339,455    41,943,024  83 Linux
/dev/sdb7       1,377,339,504 1,418,299,391    40,959,888  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x500b9b3f

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    15,856,154    15,856,092   7 HPFS/NTFS
/dev/sdc2          15,856,155   269,458,244   253,602,090   5 Extended
/dev/sdc5          15,872,220   159,236,279   143,364,060   7 HPFS/NTFS
/dev/sdc6         159,236,343   184,426,199    25,189,857  83 Linux
/dev/sdc7         184,426,263   192,603,284     8,177,022  82 Linux swap / Solaris
/dev/sdc8         192,603,348   269,458,244    76,854,897  83 Linux
/dev/sdc3         269,458,308 1,250,258,813   980,800,506   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5d7d47e1

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048    63,326,207    63,324,160   7 HPFS/NTFS
/dev/sdd2    *     63,328,230   107,105,354    43,777,125   7 HPFS/NTFS
/dev/sdd3         107,105,355   778,202,616   671,097,262   7 HPFS/NTFS
/dev/sdd4         778,204,665 1,953,520,064 1,175,315,400   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xba1a5abd

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63   125,576,374   125,576,312   7 HPFS/NTFS
/dev/sde2         125,580,105   133,387,694     7,807,590   5 Extended
/dev/sde5         125,580,168   133,387,694     7,807,527  82 Linux swap / Solaris
/dev/sde3         133,387,695   152,922,734    19,535,040  83 Linux
/dev/sde4         152,922,735   156,296,384     3,373,650  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="0628CBA728CB9459" LABEL="XP32" TYPE="ntfs" 
/dev/sda2: UUID="4E208D54208D43C5" TYPE="ntfs" 
/dev/sda4: UUID="666c26ba-0fe2-4938-87bf-469783bf146e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="9d97498c-e003-46d4-b24a-70bd5c3bdd3a" TYPE="swap" 
/dev/sdb1: UUID="823E2AB43E2AA161" LABEL="XP64" TYPE="ntfs" 
/dev/sdb2: UUID="2D7EEE6F1366209C" LABEL="Server" TYPE="ntfs" 
/dev/sdb3: UUID="24FE8453501D67B0" TYPE="ntfs" 
/dev/sdb5: UUID="f7be76b7-60cc-4e9c-8a1c-3b164ca92d4a" TYPE="swap" 
/dev/sdb6: UUID="1fd70a14-a507-40aa-9c59-046c25cda355" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb7: UUID="fb4fbc01-2e95-481f-bfc0-9fd9c5a96df9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="4DEC9064196B76C6" TYPE="ntfs" 
/dev/sdc3: UUID="901C34721C345606" LABEL="Vol_MOVIES" TYPE="ntfs" 
/dev/sdc5: UUID="44E130AFA8CEA628" LABEL="Vol_F-Movies2" TYPE="ntfs" 
/dev/sdc6: UUID="15a961f4-90a9-4905-b392-20fff44da061" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc7: UUID="dd58cd60-4923-494f-80d9-73525b53675d" TYPE="swap" 
/dev/sdc8: UUID="92bdb8b9-1de1-46ca-899d-0f7c66b299fe" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: UUID="1680E14B80E13243" LABEL="VistaEtern32" TYPE="ntfs" 
/dev/sdd2: UUID="10D2399DD239884C" LABEL="Win7" TYPE="ntfs" 
/dev/sdd3: UUID="226AA1626AA13407" LABEL="Backups" TYPE="ntfs" 
/dev/sdd4: UUID="5A0C57E40C57BA29" LABEL="Vol_movies3" TYPE="ntfs" 
/dev/sde1: UUID="88285A6A285A56F2" LABEL="VistaEtern64" TYPE="ntfs" 
/dev/sde3: UUID="0ee4a80f-0df5-4e24-9c57-bbbbce82806b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sde4: UUID="a1d44f32-88d0-4e6f-874e-901ccdab2133" TYPE="ext4" 
/dev/sde5: UUID="c964ca19-6737-4815-85f8-db7c687c46b4" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
;timeout=3 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
;C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sda4/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
 color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=666c26ba-0fe2-4938-87bf-469783bf146e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=666c26ba-0fe2-4938-87bf-469783bf146e

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Windows operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional (32-bit)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional (64-bit)
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sde1
title        Microsoft Windows Vista (64-bit)
rootnoverify    (hd4,0)
savedefault
makeactive
map        (hd0) (hd4)
map        (hd4) (hd0)
chainloader    +1



# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Linux operating systems:
root


title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        666c26ba-0fe2-4938-87bf-469783bf146e
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=666c26ba-0fe2-4938-87bf-469783bf146e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

## title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
## uuid        666c26ba-0fe2-4938-87bf-469783bf146e
## kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=666c26ba-0fe2-4938-87bf-469783bf146e ro  single
## initrd        /boot/initrd.img-2.6.28-16-generic

## title        Ubuntu 9.04, kernel 2.6.28-11-generic
## uuid        666c26ba-0fe2-4938-87bf-469783bf146e
## kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=666c26ba-0fe2-4938-87bf-469783bf146e ro quiet splash 
## initrd        /boot/initrd.img-2.6.28-11-generic
## quiet

## title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
## uuid        666c26ba-0fe2-4938-87bf-469783bf146e
## kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=666c26ba-0fe2-4938-87bf-469783bf146e ro  single
## initrd        /boot/initrd.img-2.6.28-11-generic

## title        Ubuntu 9.04, memtest86+
## uuid        666c26ba-0fe2-4938-87bf-469783bf146e
## kernel        /boot/memtest86+.bin
## quiet


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title        openSUSE 11.1 - 2.6.27.37-0.1 (on /dev/sdb6)
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.27.37-0.1-default root=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part6 resume=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part5 splash=silent showopts vga=0x317 
initrd        /boot/initrd-2.6.27.37-0.1-default
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
# title        Failsafe -- openSUSE 11.1 - 2.6.27.37-0.1 (on /dev/sdb6)
# root        (hd1,5)
# kernel        /boot/vmlinuz-2.6.27.37-0.1-default root=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part6 showopts ide=nodma apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317 
# initrd        /boot/initrd-2.6.27.37-0.1-default
# savedefault
# boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
# title        linux (on /dev/sdc6)
# root        (hd2,5)
# kernel        /boot/vmlinuz BOOT_IMAGE=linux root=UUID=15a961f4-90a9-4905-b392-20fff44da061  resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788 
# initrd        (hd2,5)/boot/initrd.img
# savedefault
# boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
# title        linux-nonfb (on /dev/sdc6)
# root        (hd2,5)
# kernel        /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d 
# initrd        (hd2,5)/boot/initrd.img
# savedefault
# boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
# title        failsafe (on /dev/sdc6)
# root        (hd2,5)
# kernel        /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=15a961f4-90a9-4905-b392-20fff44da061 failsafe 
# initrd        (hd2,5)/boot/initrd.img
# savedefault
# boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
# title        desktop586 2.6.29.1-4mnb (on /dev/sdc6)
# root        (hd2,5)
# kernel        /boot/vmlinuz-2.6.29.1-desktop586-4mnb BOOT_IMAGE=desktop586_2.6.29.1-4mnb  root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788 
# initrd        (hd2,5)/boot/initrd-2.6.29.1-desktop586-4mnb.img
# savedefault
# boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
# title        desktop586 2.6.29.6-1mnb (on /dev/sdc6)
# root        (hd2,5)
# kernel        /boot/vmlinuz-2.6.29.6-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.29.6-1mnb root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788 
# initrd        (hd2,5)/boot/initrd-2.6.29.6-desktop586-1mnb.img
# savedefault
# boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd2
# title        Please use BIOS to change boot drive to 4M for Vista or Windows 7
# rootnoverify    (hd3,1)
# savedefault
# makeactive
# map        (hd0) (hd3)
# map        (hd3) (hd0)
# chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sde1
# title        Windows Vista (loader)
# rootnoverify    (hd4,0)
# savedefault
# makeactive
# map        (hd0) (hd4)
# map        (hd4) (hd0)
# chainloader    +1



# title Mandriva grub
# root (hd2,5)
# chainloader +1

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title        Linux Mandriva One i586 KDE4(on /dev/sdb7)
root        (hd1,6)
kernel        /boot/vmlinuz BOOT_IMAGE=linux 
root=UUID=15a961f4-90a9-4905-b392-20fff44da061 
resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788
initrd (hd1,6)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
  Mandriva installation on /dev/sdc6.
#  title        Mandriva-nonfb (on /dev/sdc6)
#  root        (hd2,5)
#  kernel        /boot/vmlinuz BOOT_IMAGE=linux-nonfb 
root=UUID=15a961f4-90a9-4905-b392-20fff44da061
  resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d
#  initrd        (hd2,5)/boot/initrd.img
#  savedefault
#  boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
#  title        Mandriva failsafe (on /dev/sdc6)
#  root        (hd2,5)
#  kernel        /boot/vmlinuz BOOT_IMAGE=failsafe 
root=UUID=15a961f4-90a9-4905-b392-20fff44da061 failsafe
#  initrd        (hd2,5)/boot/initrd.img
#  savedefault
#  boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
# title        Mandriva desktop586 2.6.29.1-4mnb (on /dev/sdc6)
# root        (hd2,5)
# kernel    /boot/vmlinuz-2.6.29.1-desktop586-4mnb 
BOOT_IMAGE=desktop586_2.6.29.1-4mnb 
root=UUID=15a961f4-90a9-4905-b392-20fff44da061
# resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788
# initrd        (hd2,5)/boot/initrd-2.6.29.1-desktop586-4mnb.img
# savedefault
# boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
# title        Mandriva desktop586 2.6.29.6-1mnb (on /dev/sdc6)
# root        (hd2,5)
# kernel    /boot/vmlinuz-2.6.29.6-desktop586-1mnb 
BOOT_IMAGE=desktop586_2.6.29.6-1mnb 
root=UUID=15a961f4-90a9-4905-b392-20fff44da061
# resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788
# initrd        (hd2,5)/boot/initrd-2.6.29.6-desktop586-1mnb.img
# savedefault
# boot







# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sde5.
title        Linux Mint 7 Gloria x64 (on /dev/sde5)
root        (hd4,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sde5 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=666c26ba-0fe2-4938-87bf-469783bf146e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9d97498c-e003-46d4-b24a-70bd5c3bdd3a none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=f7be76b7-60cc-4e9c-8a1c-3b164ca92d4a none            swap    sw              0       0
# swap was on /dev/sdc7 during installation
UUID=dd58cd60-4923-494f-80d9-73525b53675d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


 298.4GB: boot/grub/menu.lst
 298.4GB: boot/grub/stage2
 297.8GB: boot/initrd.img-2.6.28-11-generic
 297.8GB: boot/initrd.img-2.6.28-16-generic
 297.7GB: boot/vmlinuz-2.6.28-11-generic
 297.8GB: boot/vmlinuz-2.6.28-16-generic
 297.8GB: initrd.img
 297.8GB: initrd.img.old
 297.8GB: vmlinuz
 297.7GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=20 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 

=========================== sdb6/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Sun Nov  8 21:22:52 NST 2009
default 0
timeout 8
gfxmenu (hd0,5)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.1 - 2.6.27.37-0.1
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.27.37-0.1-default root=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part6 resume=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part5 splash=silent showopts vga=0x317
    initrd /boot/initrd-2.6.27.37-0.1-default

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.1 - 2.6.27.37-0.1
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.27.37-0.1-default root=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part6 showopts ide=nodma apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317
    initrd /boot/initrd-2.6.27.37-0.1-default

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title windows 2
    rootnoverify (hd0,1)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 3###
title windows 3
    rootnoverify (hd0,2)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    rootnoverify (fd0)
    chainloader +1

=============================== sdb6/etc/fstab: ===============================

/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part5 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part6 /                    ext3       acl,user_xattr        1 1
/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part1 /windows/C           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part2 /windows/D           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part3 /windows/E           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sdb6: Location of files loaded by Grub: ===================


 699.4GB: boot/grub/menu.lst
 699.3GB: boot/grub/stage2
 699.3GB: boot/initrd
 699.3GB: boot/initrd-2.6.27.37-0.1-default
 699.3GB: boot/vmlinuz
 699.3GB: boot/vmlinuz-2.6.27.37-0.1-default

=========================== sdc6/boot/grub/menu.lst: ===========================

timeout 5
color black/cyan yellow/cyan
gfxmenu (h2,5)/boot/gfxmenu
default 0

title linux
kernel (hd2,5)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788
initrd (hd2,5)/boot/initrd.img

title linux-nonfb
kernel (hd2,5)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d
initrd (hd2,5)/boot/initrd.img

title failsafe
kernel (hd2,5)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=15a961f4-90a9-4905-b392-20fff44da061 failsafe
initrd (hd2,5)/boot/initrd.img

title desktop586 2.6.29.1-4mnb
kernel (hd2,5)/boot/vmlinuz-2.6.29.1-desktop586-4mnb BOOT_IMAGE=desktop586_2.6.29.1-4mnb root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788
initrd (hd2,5)/boot/initrd-2.6.29.1-desktop586-4mnb.img

title desktop586 2.6.29.6-1mnb
kernel (hd2,5)/boot/vmlinuz-2.6.29.6-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.29.6-1mnb root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788
initrd (hd2,5)/boot/initrd-2.6.29.6-desktop586-1mnb.img

=============================== sdc6/etc/fstab: ===============================

# Entry for /dev/sda6 :
UUID=15a961f4-90a9-4905-b392-20fff44da061 / ext3 defaults 1 1
# Entry for /dev/sda8 :
UUID=92bdb8b9-1de1-46ca-899d-0f7c66b299fe /home ext3 defaults 1 2
none /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=dd58cd60-4923-494f-80d9-73525b53675d swap swap defaults 0 0

=================== sdc6: Location of files loaded by Grub: ===================


  81.6GB: boot/grub/menu.lst
  81.7GB: boot/grub/stage2
  81.6GB: boot/initrd-2.6.29.1-desktop586-4mnb.img
  81.7GB: boot/initrd-2.6.29.6-desktop586-1mnb.img
  81.7GB: boot/initrd.img
  81.7GB: boot/vmlinuz
  81.6GB: boot/vmlinuz-2.6.29.1-desktop586-4mnb
  81.7GB: boot/vmlinuz-2.6.29.6-desktop586-1mnb
  81.7GB: boot/vmlinuz-2.6.29.6-desktop586-2mnb
  81.7GB: boot/vmlinuz-desktop586

=========================== sde3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/linuxmint.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sde3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd4,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic
root        (hd4,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sde3 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic (recovery mode)
root        (hd4,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sde3 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Linux Mint 7 Gloria x64, memtest86+
root        (hd4,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title        Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sda4)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=666c26ba-0fe2-4938-87bf-469783bf146e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title        openSUSE 11.1 - 2.6.27.37-0.1 (on /dev/sdb6)
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.27.37-0.1-default root=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part6 resume=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part5 splash=silent showopts vga=0x317 
initrd        /boot/initrd-2.6.27.37-0.1-default
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title        Failsafe -- openSUSE 11.1 - 2.6.27.37-0.1 (on /dev/sdb6)
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.27.37-0.1-default root=/dev/disk/by-id/ata-WDC_WD10EADS-00L5B1_WD-WCAU48401505-part6 showopts ide=nodma apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317 
initrd        /boot/initrd-2.6.27.37-0.1-default
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title        linux (on /dev/sdc6)
root        (hd2,5)
kernel        /boot/vmlinuz BOOT_IMAGE=linux root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788 
initrd        (hd2,5)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title        linux-nonfb (on /dev/sdc6)
root        (hd2,5)
kernel        /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d 
initrd        (hd2,5)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title        failsafe (on /dev/sdc6)
root        (hd2,5)
kernel        /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=15a961f4-90a9-4905-b392-20fff44da061 failsafe 
initrd        (hd2,5)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title        desktop586 2.6.29.1-4mnb (on /dev/sdc6)
root        (hd2,5)
kernel        /boot/vmlinuz-2.6.29.1-desktop586-4mnb BOOT_IMAGE=desktop586_2.6.29.1-4mnb root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788 
initrd        (hd2,5)/boot/initrd-2.6.29.1-desktop586-4mnb.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title        desktop586 2.6.29.6-1mnb (on /dev/sdc6)
root        (hd2,5)
kernel        /boot/vmlinuz-2.6.29.6-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.29.6-1mnb root=UUID=15a961f4-90a9-4905-b392-20fff44da061 resume=UUID=dd58cd60-4923-494f-80d9-73525b53675d splash=silent vga=788 
initrd        (hd2,5)/boot/initrd-2.6.29.6-desktop586-1mnb.img
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd2
title        Windows Vista (loader)
rootnoverify    (hd3,1)
savedefault
makeactive
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sde1
title        Windows Vista (loader)
rootnoverify    (hd4,0)
savedefault
makeactive
map        (hd0) (hd4)
map        (hd4) (hd0)
chainloader    +1


=============================== sde3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sde3 during installation
UUID=0ee4a80f-0df5-4e24-9c57-bbbbce82806b /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sde4 during installation
UUID=a1d44f32-88d0-4e6f-874e-901ccdab2133 /home           ext4    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=9d97498c-e003-46d4-b24a-70bd5c3bdd3a none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=f7be76b7-60cc-4e9c-8a1c-3b164ca92d4a none            swap    sw              0       0
# swap was on /dev/sdc7 during installation
UUID=dd58cd60-4923-494f-80d9-73525b53675d none            swap    sw              0       0
# swap was on /dev/sde5 during installation
UUID=c964ca19-6737-4815-85f8-db7c687c46b4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sde3: Location of files loaded by Grub: ===================


  69.0GB: boot/grub/menu.lst
  69.0GB: boot/grub/stage2
  68.7GB: boot/initrd.img-2.6.28-11-generic
  68.8GB: boot/vmlinuz-2.6.28-11-generic
  68.7GB: initrd.img
  68.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc7

00000000  71 d1 0e db 13 40 7c 00  00 00 4f 8a 28 fe 4d 6d  |q....@|...O.(.Mm|
00000010  4d c0 be dd 68 d7 cc ec  20 42 32 6f f9 c9 8c de  |M...h... B2o....|
00000020  ba 0a c4 a2 19 b1 8b 7d  ff 05 04 02 7d 38 19 42  |.......}....}8.B|
00000030  38 84 c4 12 1b 54 dd 27  36 8c 60 d5 0c 8e 5a 9b  |8....T.'6.`...Z.|
00000040  83 b5 22 ad 5a df c2 7f  d2 1d 04 20 08 f8 3a 0a  |..".Z...... ..:.|
00000050  0a 3a 48 49 12 e0 09 b6  2f 3e 34 69 c5 f6 8f a2  |.:HI..../>4i....|
00000060  1e 3d 15 35 01 2a fa 42  51 94 1d cc 1d e9 41 2f  |.=.5.*.BQ.....A/|
00000070  03 9f 85 f8 06 87 f8 b4  b0 0b 9b a5 c9 b2 a1 a7  |................|
00000080  50 4c b6 8b 84 b0 5c cb  3b a6 db 75 2d 12 53 ba  |PL....\.;..u-.S.|
00000090  31 d3 d3 db 4a da 72 22  33 1b 93 fc 87 d2 4f e3  |1...J.r"3.....O.|
000000a0  67 e4 5c 75 e3 54 17 81  ef 24 e9 ea c5 ec 14 20  |g.\u.T...$..... |
000000b0  bb 10 72 90 28 51 08 ef  60 35 c4 29 5c 11 2d 51  |..r.(Q..`5.)\.-Q|
000000c0  16 d1 3a 6f 60 ac 96 e0  f8 6b 5d 1c 35 32 f5 cb  |..:o`....k].52..|
000000d0  a1 a3 55 c8 4f d1 8f 67  1e 27 47 aa 29 ac e5 a2  |..U.O..g.'G.)...|
000000e0  90 0b 8e d6 ea 6f 9a dc  35 32 b5 97 33 87 2b ac  |.....o..52..3.+.|
000000f0  7a 8c 7d 1a f0 ab 6e cd  c6 0f 47 47 63 6c 58 cc  |z.}...n...GGclX.|
00000100  ea b6 34 8d 3d 60 f8 00  80 5b ea f4 7a 44 4c f9  |..4.=`...[..zDL.|
00000110  d2 58 55 e1 53 7c a6 c1  0b 0e 61 3e a6 96 a0 ca  |.XU.S|....a>....|
00000120  58 2d 9f fe 93 f8 06 2b  ea a8 01 c7 c5 29 cd f6  |X-.....+.....)..|
00000130  56 a0 9a 22 00 3f 42 ab  c7 1a a3 4e 03 7c 57 ee  |V..".?B....N.|W.|
00000140  f4 80 2b 88 3a a3 64 21  2b 98 78 ca 52 a3 66 16  |..+.:.d!+.x.R.f.|
00000150  35 44 0b 9f 39 4e 2b 6c  b8 89 87 a0 84 41 c3 d8  |5D..9N+l.....A..|
00000160  eb 38 b3 3f 49 c2 b4 79  49 bc 79 87 c4 fd ed 60  |.8.?I..yI.y....`|
00000170  69 79 f8 95 79 af cf c3  c7 f0 0f b1 f1 3a 66 20  |iy..y........:f |
00000180  f5 4f 2d d2 b3 52 07 57  ab 83 64 a4 39 34 8b ce  |.O-..R.W..d.94..|
00000190  3e 8f d0 8e d9 72 ea 05  12 9f d2 aa 57 2e 2a dd  |>....r......W.*.|
000001a0  97 f8 26 ce 65 84 1e 49  cd f5 e5 31 39 cb 8e 36  |..&.e..I...19..6|
000001b0  29 01 84 49 f8 07 1e 4b  1d 9d f1 6d 89 d5 00 ca  |)..I...K...m....|
000001c0  01 0a 3b fd b1 92 95 7d  a4 ad 36 b9 d8 4b 35 56  |..;....}..6..K5V|
000001d0  bd c9 5a b5 2c 63 90 eb  fc 3b 27 58 e8 eb 54 0c  |..Z.,c...;'X..T.|
000001e0  e6 9a 2b 6e 9b 97 84 95  92 37 11 8d 32 da 47 57  |..+n.....7..2.GW|
000001f0  39 cf 43 9f e1 d5 4a c7  44 ca 81 97 52 bd 8d 31  |9.C...J.D...R..1|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdf sdg 
```

---

### Post by presence1960 on 2009-11-24
Somewhat of a mess, although I have seen worse! Here is what I can gather out of all that:

You have 5 Windows OSs installed (why?) XP 32bit on sda1, XP 64 bit on sdb1, Vista 32bit on sdd1, Windows 7 on sdd2 & Vista 64bit on sdc1.

You have 4 Linux OSs installed- Ubuntu Jaunty on sda4, mandriva on sdc6, OpenSusu on sdb6 & Mint on sde3.

You do have multiple instances of swap partitions which are unnecessary but not a major problem in my opinion.

This is what I would do. Linux Mint uses it's own special version of GRUB so I would use the Mint Live CD to install GRUB to MBR of sde. Then I would go into BIOS and set my hard disk boot order as follows- sde, sda, sdb, sdc & sdd. This will bring up Mint's GRUB when you boot. Then I would edit Mint's menu.lst to change all OSs except Mint to a chainload entry. This is going to be a lot of work. If you want to go ahead I would start by booting off the Mint Live CD and restoring Mint's GRUB like this: 

```
1. Boot your computer up with Mint CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd4,2)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd4,2)", or whatever your hard disk + boot partition 
   numbers are for Mint.
6. Type "setup (hd4)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

When you reboot go into BIOS and set your hard disk boot order as sde, sda, sdb, sdc & sdd. Save changes to CMOS & continue booting. Boot into Mint when you get the GRUB menu.

From there post back and then we can try to add the chainload entries to Mint's menu.lst. 

personally if this were my machine I would decide on maybe 2 windows OSs to keep and then redo the whole partition scheme keeping both Windows OSs on the same hard disk. I would also keep all Linux OSs on a hard disk of their own and then use the other 3 disks and the remaining free space on the OS disks for all your various storage needs. Your partition scheme needs to be simplified and more ordered in my opinion. 

I like experimenting with different OSs but I can't see for the life of me why someone would need 5 Windows OSs (1 is too many for me :p) . I would cut that down to 2.

Let me know what you want to do.

---

### Post by archp2009 on 2009-11-25
I get this:
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,3)
 (hd1,5)
 (hd2,5)
 (hd4,2)
grub> 
When you say,

```
Type "root (hd4,2)", or whatever your hard disk + boot partition 
   numbers are for Mint
```
I'm not sure if that's the correct hard drive and partition for Mint or not.

---

### Post by presence1960 on 2009-11-25
> **archp2009 said:**
> I get this:
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,3)
 (hd1,5)
 (hd2,5)
 (hd4,2)
grub> 
When you say,

```
Type "root (hd4,2)", or whatever your hard disk + boot partition 
   numbers are for Mint
```
I'm not sure if that's the correct hard drive and partition for Mint or not.
That (hd4,2) is correct for Mint so proceed with:
root (hd4,2) 
setup (hd4)
quit

FYI info:
(hd0,3) is jaunty on sda4
(hd1,5) is OpenSuse on sdb6
(hd2,5) is Mandriva on sdc6
(hd4,2) is Mint on sde3

In GRUB Legacy numbering for hard disks & partitions start at 0. 
sda=(hd0), sda1=(hd0,0) sda2=(hd0,1), sda3=(hd0,2), etc.
sdb=(hd1), sdb1=(hd1,0), sdb2=(hd1,1), sdb3=(hd1,2), etc.
sdc=(hd2), etc.

But when you get to menu.lst the (hdx) is determined by the boot order of your hard disks in BIOS. That is because that is the actual order in which your BIOS looks to the hard disks to boot. But we will cross that bridge when we get to editing your other OSs to chainload from GRUB.

---

### Post by archp2009 on 2009-11-25
Grub was restored but the only options that I could get to work were Vista 64 which came up under Vista Loader and Mandriva which I am into now.  I need to go into PartedMagic to help me decide which disk is which. How critical are the order of the hard drives?
[edit: It's odd because Vista64 and Mandriva were the ONLY two OS's that I could NOT load the last time Mint installed GRUB. It was then written to (hd0,0)]

---

### Post by archp2009 on 2009-11-25
I fixed the order of my hard drives in BIOS and now I can only get into Vista 64.  According to PartedMagic my drives are listed as
80gb hdb IDE Drive (vista64/Mint)
320gb sda (xp32/ubuntu)
1tb sdb (has xp64/Mandriva/OpenSuse)
640gb sdc (data)
1tb sdd (vista32/win7)

I will double-check that I have them in that order in BIOS. I'm not sure about the id numbers for the two tb drives though.
[Edit1: Yes, that's the order I have them in BIOS]
[Edit2:  Actually, the one working Windows item was Win7 not WinVista64]

---

### Post by presence1960 on 2009-11-25
> **archp2009 said:**
> I fixed the order of my hard drives in BIOS and now I can only get into Vista 64.  According to PartedMagic my drives are listed as
80gb hdb IDE Drive (vista64/Mint)
320gb sda (xp32/ubuntu)
1tb sdb (has xp64/Mandriva/OpenSuse)
640gb sdc (data)
1tb sdd (vista32/win7)

I will double-check that I have them in that order in BIOS. I'm not sure about the id numbers for the two tb drives though.
[Edit1: Yes, that's the order I have them in BIOS]
[Edit2:  Actually, the one working Windows item was Win7 not WinVista64]
sorry for the delay, last minute holiday shopping. Can you boot into Mint? If you can open a terminal and run ```
gksu gedit /boot/grub/menu.lst

``` That is a lowercase L in .lst
Post the entire output of that command.

---

### Post by archp2009 on 2009-11-25
No worry about the delay.  I am in awe with the quality and promptness of your assistance. Although I don't expect all this, I appreciate it very much, especially at this time of the year.  Unfortunately, I cannot boot into any distro the way the menu.lst is written now. I could get into Mandriva when I had the order of the two 1tb drives reversed.  Possibly, this is because it is the first time I wrote the loader to the same drive as the Mint is located on. It was always written to the 320gb sata drive which I used to previously list in Bios as the first drive   I have no idea what to do from here.  I'm not sure if the IDE drive which has the Mint on it is considered by Linux to be the first drive or the last. Anyway, as I wrote previously, I set it to be first before doing what you asked.

---

### Post by presence1960 on 2009-11-25
> **archp2009 said:**
> No worry about the delay.  I am in awe with the quality and promptness of your assistance. Although I don't expect all this, I appreciate it very much, especially at this time of the year.  Unfortunately, I cannot boot into any distro the way the menu.lst is written now. I could get into Mandriva when I had the order of the two 1tb drives reversed.  Possibly, this is because it is the first time I wrote the loader to the same drive as the Mint is located on. It was always written to the 320gb sata drive which I used to previously list in Bios as the first drive   I have no idea what to do from here.  I'm not sure if the IDE drive which has the Mint on it is considered by Linux to be the first drive or the last. Anyway, as I wrote previously, I set it to be first before doing what you asked.

Let's get a look at that Mint menu.lst another way. Boot from the Mint Live CD and get to the desktop. Open a file browser and mount the Mint partition. Go to /boot/grub and then open the menu.lst file. paste the contents back here. It has been a while since i used Mint. I think I may know what the problem is. Mint's grub used to use (hdx,y) instead of UUID. If that is the case we need to change the (hdx,y) designations for the OSs not able to boot.

When using (hdx,y) in GRUB x is determined by the order in BIOS, not from fdisk. Example- your 80 Gb is listed as (hd4) sde, but it is now the first disk to boot in BIOS thus it is now (hd0) in GRUB. So in menu.lst if Mint uses (hdx,y) Mint on sde3 goes from (hd4,2) to (hd0,2)

---

### Post by presence1960 on 2009-11-25
I am correct. Mint uses (hdx,y). Boot the Mint Live CD & get to desktop. Open a terminal and run ```
gksu nautilus
```

Mount Mints directory on the left pane by highlighting it. On the right navigate to /boot/grub and open menu.lst file. Change this:
```

## ## End Default Options ##

title        Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic
root        (hd4,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sde3 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic (recovery mode)
root        (hd4,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sde3 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Linux Mint 7 Gloria x64, memtest86+
root        (hd4,2)
kernel        /boot/memtest86+.bin
quiet
```

TO:

```
## ## End Default Options ##

title        Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sde3 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sde3 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Linux Mint 7 Gloria x64, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet


```

Click Save on toolbar. Close file.

Then reboot and boot into Mint. if successful (it should be!) then we can get rid of the other entries and add them as chainload entries.

---

### Post by archp2009 on 2009-11-25
Whe I open Filesystem and boot There is no grub inside the boot folder.  Aren't I just looking in the cd?  When I click computer it says Nautlus does not allow.

---

### Post by presence1960 on 2009-11-25
> **archp2009 said:**
> Whe I open Filesystem and boot There is no grub inside the boot folder.  Aren't I just looking in the cd?  When I click computer it says Nautlus does not allow.

From the Live CD Filesystem on left pane is the Live CD Filesystem. You need to mount the directory on the left which is Mint's directory.

You have so many partitions you may not know which one is which. Why not go to Partition Editor (gparted) from the live cd. Open a terminal and run ```
gksu gparted
```

Right click on the following partitions and choose label. Type in the OS name as label. Then click apply. This will put a label on each partition so when you use nautilus you will know which OS filesystem you are mounting.

sda1- XP32
sda4-Jaunty

sdb1-XP64
sdb6-OpenSuse

sdc1-Vista64
sdc6-Mandriva

sdd1-Vista32
sdd2-Win7

sde3-Mint

After applying labels close gparted & run in terminal ```
gksu nautilus
``` and try mounting Mint's directory and navigate to /boot/grub & open menu.lst
Then make the edit to mint's stanza's I suggested earlier.

---

### Post by archp2009 on 2009-11-25
When you say mount, do you mean that I need to use the mount command?

Something like this?

# mount -t ext3 /dev/sde3 /opt

I haven't done that before except to copy and paste what somebody gave me.  I have no idez what the -t or /opt mean or if they are needed.
Can I use PartedMagic to rename the partitions? Is Gparted on the Mint CD?  I have a year old GParted CD on the shelf if I can't use PartedMagic.

---

### Post by presence1960 on 2009-11-25
> **archp2009 said:**
> When you say mount, do you mean that I need to use the mount command?

Something like this?

# mount -t ext3 /dev/sde3 /opt

I haven't done that before except to copy and paste what somebody gave me.  I have no idez what the -t or /opt mean or if they are needed.
Can I use PartedMagic to rename the partitions? Is Gparted on the Mint CD?  I have a year old GParted CD on the shelf if I can't use PartedMagic.

you can mount a directory from nautilus by clicking the appropriate directory on the left pane

---

### Post by archp2009 on 2009-11-25
I renamed all the partitions as you suggested.  There is no sde.  Mint is on the IDE drive which is listed as hd.  It appears that the main partition ext3 is on hdb3.  I also have a smaller ext4 partition hdb4. When i enter Nautlius I am unable to view any of these partitions in the left pane.

---

### Post by presence1960 on 2009-11-25
> **archp2009 said:**
> I renamed all the partitions as you suggested.  There is no sde.  Mint is on the IDE drive which is listed as hd.  It appears that the main partition ext3 is on hdb3.  I also have a smaller ext4 partition hdb4. When i enter Nautlius I am unable to view any of these partitions in the left pane.

Ok, I booted my Live Cd and was reminded that there is a quirk about using nautilus as root. it will only show partitions already mounted. So what you have to do is go Places > Computer. This will bring up a file browser. Click on the Mint partition to mount it. Once it shows directories on right side it is mounted. Now open a terminal and run ```
gksu nautilus
```. You should be able to access the Mint subdirectories now. Open the menu.lst file in Mint and make the edits.

---

### Post by archp2009 on 2009-11-25
This is going nowhere.  All that shows for computer is partition sizes folllowed by the word media.  When I clock on the partition whose size is nearest that of Mint it comes up in Nautilus as "disk"  When I open menu.lst and edit I am unable to save (no permissions).

---

### Post by presence1960 on 2009-11-25
> **archp2009 said:**
> This is going nowhere.  All that shows for computer is partition sizes folllowed by the word media.  When I clock on the partition whose size is nearest that of Mint it comes up in Nautilus as "disk"  When I open menu.lst and edit I am unable to save (no permissions).

you have to open menu.lst as root. Must use the gksu command when opening nautilus.

Recap: Open file browser, mount Mint partition by clicking it. When subdirectories appear on right it is mounted. NOW open a terminal and run ```
gksu nautilus
``` This will open nautilus with root permissions. now find the menu.lst file on Mint partition, edit it & save it. Close file and reboot.

---

### Post by presence1960 on 2009-11-25
> **archp2009 said:**
> This is going nowhere.  All that shows for computer is partition sizes folllowed by the word media.  When I clock on the partition whose size is nearest that of Mint it comes up in Nautilus as "disk"  When I open menu.lst and edit I am unable to save (no permissions).

I thought you added the labels to those partitions? if you did not all that will show is media and the size.

The first file browser you open through the Mint menu. I don't have Mint but below is a pic of how to do it in Ubuntu. Choose Computer.

Mount the Mint partition on the browser that opens by clicking on it. When the directories appear on right it is mounted.

Now use terminal and run gksu nautilus. This will open a root file browser. Go to Mint's partition, find, edit, save & close menu.lst

Reboot.

---

### Post by archp2009 on 2009-11-26
I'm sorry that there seems to be something I am not doing exactly the way you intended. It's really frustrating. I used Partedmagic "mount list" to rename the folders sda1 renamed to xp32, etc. but I can't see them using the instructions you game me. All I see are the Windows names and media sizes and the media sizes are not the same as viewed in Partedmagic.  For some reason I can't see the pic of Ubuntu that you refer to. I don't see the name Mint except for the cd or any of the other folders I renames. When I clicked save I get the familiar, "you do not have permissions, etc."  I need to figure out what I am missing or doing wrong. Perhaps someone else can figure out what i'm doing wrong. Perhaps I'm just dumb.

---

### Post by archp2009 on 2009-11-26
I tried reinstalling Mint - got Grub 17 error again.  Then tried reinstalling Jaunty - Gloria and Jaunty are booting now as well as the main WinXP. I'm not too much concerned with OpenSuse and Mandriva - I may remove the drive that those are on  for use in a new HTPC. That's if Santa is better to me than I expect! There were pre-existing boot issues with the other Windows installations.  I can still access them via BIOS and may have to fix BootMgr in one.  I'm a poor looser.  There's lots of great information on this thread though that I'm sure will be useful to many Newbies like me.

---

