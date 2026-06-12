---
title: "Selecting Windows 7 loader on the Ubuntu 11.10 Grub2 reboots PC"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by Ren123 on 2012-04-22
Hi All,
I have installed Ubuntu 11.10 OS on my PC which was already having Windows 7. Ubuntu is loading properly. But when I select windows 7 loader, the PC monitor turns off and the PC restarts :(

I have 2 hard disk drives **sda** and **sdb**
While installing Ubuntu I did the following configuration:

/dev/sda1 has the Windows 7:Chain loader 
and it is ntfs file system

/dev/sdb1 has ext4 filesystem and is the root
/dev/sdb9 is the swap.

The window 7 grub entry is as follows and I believe its correct, since the UUID 02E06A4DE06A474F is pointing to sda1

menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 02E06A4DE06A474F
	chainloader +1
}

What is wrong with my configuration? I am not able to figure out the issue. Please help me.

Thanks 
Ren

P.S.
I also tried an edit of Windows 7 during grub2
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set=root 02E06A4DE06A474F
	chainloader +1
}
but still the PC just reboots as if CTRL+ALT+DEL is pressed

---

### Post by oldfred on 2012-04-22
Welcome to the forums.

Use this to run the bootinfoscript and post the link back to show your entire configuration. Do you have a Windows repairCD or USB? Does pressing f8 almost at the same time you press enter on the grub Windows entry get you to a Windows repair console? Some say have have to try several times as it is very quick.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by Ren123 on 2012-04-22
Thanks Fred.

Here is the results of bootinfoscript. 

[ATTACH]216454[/ATTACH]

I tried pressing f8 but no hope, the reboot is very fast.

---

### Post by oldfred on 2012-04-22
Boot script looks pretty normal.

Your 11.10 Ubuntu is in sdb1, but your install of grub2 is in sda. You have an old install of grub legacy that is not doing anything. I would install grub to sdb. I prefer to have the boot loader of each system in the MBR of that system's drive, so each drive can be booted separately.

sudo grub-install /dev/sdb

But grub2 also remembers where to reinstall on major updates:

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Then we can install lilo to the MBR of sda, that will boot Windows directly. Maybe then f8 will work. 

Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.


If you have a Window repair CD run chkdsk on your sda1 or just c:.

chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by Ren123 on 2012-04-29
Thanks again Fred.
I had to delete the Adobe DRM installed in the boot records at Sector 32 od my /dev/sdb for this I did 
sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1 seek=32

I have moved the Grub 2 to /dev/sdb and reconfigured the package. I have got now Grub2 in both /dev/sda and /dev/sdb. 

I couldnt install lilo on MBR of sda :( (missed it from ur post sorry)
instead I ran the BootRepair tool and installed the MBR. 
Now the problem is there is TestDisk installed in MBR of /dev/sda. 

Then i had got a Windows Disk and I tried repairing the boot issues. But still no luck. 
No my option is to format the drive and install Windows 7 again. But the partition is not getting recognized. 

Also when I boot on Ubuntu still the disk is not getting recognized. 

Is there any restriction on Ubuntu installation? Now how will I proceed without loosing data on both drives?

---

### Post by oldfred on 2012-04-29
One more advantage of two drives is that you can leave the Windows boot loader in the MBR of the Windows drive, so that if you have DRM restricted Windows software it does not interfer with grub2's files in the sectors after the MBR and before the first partition.

Not sure about testdisk boot loader. It may just be another Windows like. Boot-Repair installs syslinux which also should work. All a Windows boot loader does is look for the active partition (boot flag) and jump to that to continue to boot. So if you cannot boot Windows you need to run Windows repairs. Do you have a Windows repairCD or full install DVD? Not recovery DVD which is just a hard drive image.

Rerun boot info script and post the link it creates to Boot-Info.

---

### Post by Ren123 on 2012-04-30
I have a Full Install DVD. Boot script is also fine in the /dev/sdb
 
Steps done so far.
I have removed the second harddisk(/dev/sdb), as the ubuntu is working fine I dont want to mess up things again :)
Now I have single harddisk. I have a Ubuntu DVD also a Windows DVD. The ubuntu DVD Detects the harddisk /dev/sda. I did a format of the earlier windows inorder to perform a clean windows install.
 
But the Windows Setup is not detecting my harddisk itself after this. (it is taking a very long time 15 - 20 minutes to even enter into the Setup screen)
 
There was issue on mounting the Drive but got rectified after a few restarts (Error 21)
 
I have tried formating the drive volume from Ubuntu but I am getting an error** FileSystem is NOT Clean**. (But the disk tool shows disk is healthy)
 
What could be the issue? At times it shows a read error while booting. Did I messup the partition and filesystem of the drive?
Please help me on fixing this FileSystem from Ubuntu? How will I check and clean my filesystem? How will I check and fix the file system?
How can I make this drive volume as C: in windows and make it bootable and still work with my ubuntu?

---

### Post by darkod on 2012-04-30
Have you tried to open Gparted in live mode and write new partition table? It's in Device - Create Partition Table...

I think it might be confused after the dd zeroing out the whole MBR. It doesn't expect that, plus part of the partition table is also in the first 512 bytes.

Since you want to reformat anyway, write a new blank partition table.

---

### Post by Ren123 on 2012-04-30
I did a dd zero second hard disk /dev/sdb and I have disconnected it. The issue is with first /dev/sda. I think I should create a new partition table.

---

### Post by Ren123 on 2012-04-30
I ran gparted and formated the drive to NTFS. Below is the fdisk run, The start is 2048. Is this the reason of issue?

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8acf1d8e

   Device    Boot      Start         End      Blocks   Id  System
[COLOR=Red]**/dev/sda1   *        2048    66025471    33011712    7  HPFS/NTFS/exFAT**[/COLOR]
/dev/sda2        66027150   131556284    32764567+   7  HPFS/NTFS/exFAT
/dev/sda3       131556285   197085419    32764567+   7  HPFS/NTFS/exFAT
/dev/sda4       197085420   703277504   253096042+   f  W95 Ext'd (LBA)
/dev/sda5       197085483   401882039   102398278+   7  HPFS/NTFS/exFAT
/dev/sda6       401882103   606678659   102398278+   7  HPFS/NTFS/exFAT
/dev/sda7       606678723   703277504    48299391    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1998 MB, 1998585856 bytes
16 heads, 32 sectors/track, 7624 cylinders, total 3903488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb36c89c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     3903487     1951728    6  FAT16

---

### Post by Ren123 on 2012-04-30
The new boot info script [ATTACH]216945[/ATTACH]

---

### Post by darkod on 2012-04-30
No, the first partition starting at sector 2048 is normal.

So, you can't install on this disk? It's not detected at all by the windows installer?

The results file looks normal, not much to see there since you have no OS on this disk. The partitions look normal.

---

### Post by Ren123 on 2012-04-30
Yes I am not able to install a clean  copy as the windows installer is very slow when I connect this disk. Also in Ubuntu Disk Utility shows the FileSystem is not clean. 

If you check my previous Boot Info, the disk sector shows starting at 63.

---

### Post by darkod on 2012-04-30
You might have hardware failure with this disk. In earlier versions the first partition was starting from sector 63 but now it's from 2048. That is not an issue at all.

---

### Post by Ren123 on 2012-04-30
How can I check this? The disk utility tool shows the Disk is Healthy in Ubuntu.

---

### Post by darkod on 2012-04-30
You need to enable SMART in BIOS and there was a command to do the check from ubuntu (it works from live mode too I think). I just have to google for the exact syntax.

---

### Post by darkod on 2012-04-30
smartmontools:
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

Doing the extended (long) test is best. Note that depending on disk size it can last hours (I think, never actually needed it).

---

### Post by oldfred on 2012-04-30
I know the PBR or partition boot sector is different for XP & Vista/7. I ran chkdsk from a Windows 7 repairUSB and it converted my XP PBR to a Windows 7 PBR.

Perhaps your NTFS partition created by gparted is not quite right for 7. Windows 7 used to install over XP so it should not matter, but a few have reported that they had to use the 7 install disk to reformat the partition they wanted to install into. I might see if the Windows DVD can reformat the sda1 partition. 

Some have also reported that Windows 7 has issues installing with extended partitions already created. But Windows 7 installs to an logical if it is a second install (still has to boot from a primary) so it should be ok, but if you do not yet have data in the other partitions, I might create then after the install.

---

### Post by Ren123 on 2012-04-30
I ran a SeaTools for Dos from Seagate. The Long Test PASSED (1.5 hour) DST Completed without error.

---

### Post by Ren123 on 2012-04-30
I have reconnected the slots of my SATA harddisk. Now the drives have been swapped. Disk2(80gb) is now /dev/sda and Disk1(360gb) is now /dev/sdb. The windows 7 installer detects the 80gb drive not the 360 gb one :(

---

### Post by darkod on 2012-04-30
Sounds like bad cable or sata port? Do you have other sata ports to try, or only two?

---

### Post by Ren123 on 2012-04-30
Now I have done a formatting of the /dev/sdb1 (earlier /dev/sda1) using Gparted to Fat32 and my windows installer now recognize both the drives. Trying to install windows now. Hope it works. (In progress)

If the installation works. Kindly help me boot with Ubuntu. 
My intention is dual boot. How can I configure my PC to boot in both ubuntu and windows. 
Also which device will be my boot disk?

---

### Post by Ren123 on 2012-04-30
My all three devices are SATA. 1 80 gb HDD 2. 360 gb HDD 3. DVD RW

---

### Post by Ren123 on 2012-04-30
> **darkod said:**
> Sounds like bad cable or sata port? Do you have other sata ports to try, or only two?

I don't think the issue was the cable/port as the HDDs where getting detected in Ubuntu. :(

Is there any concept like SATA master/slave Is there any relevance to which SATA Port a device is connected? :confused:

---

### Post by darkod on 2012-04-30
Why to FAT32, why not NTFS?

If the ubuntu disk has grub2 on it's MBR, it should not be touched by the windows installer. So you only need to configure BIOS to boot from that disk.

In any case, it's easy to configure the dual boot later, first see how the windows install goes.

---

### Post by Ren123 on 2012-04-30
> **darkod said:**
> Why to FAT32, why not NTFS?

If the ubuntu disk has grub2 on it's MBR, it should not be touched by the windows installer. So you only need to configure BIOS to boot from that disk.

In any case, it's easy to configure the dual boot later, first see how the windows install goes.

I tried NTFS but the installer was simply not taking recognizing the disk. So I gave a guess that may be windows installation detect a FAT32 drive. I hope there is logical explanation for this

---

### Post by Ren123 on 2012-04-30
Windows Installation success. 
Summarize
1. Had windows then installed Ubuntu 11.10 (but grub2 loader restarts PC on selecting windows 7)
2. Messed up with the MBR. The disk sectors where moved. The disk was not getting detected even after a  format to NTFS.
3. Ran SeaTools to check for Disk errors.
4. Reconnected the HDDs which swapped sda and sdb.
5. Formatted /dev/sdb1 (earlier /dev/sda1) to Fat32
6. Disk got detected by Windows 7 setup. Formated again to NTFS by Win 7 setup
7. Installed Windows.

---

### Post by Ren123 on 2012-04-30
Please help me with Configuring dual boot.
I don't see a boot option when I boot from the 360 gb harddisk

---

### Post by oldfred on 2012-04-30
Windows will not give boot option if Windows is 360GB drive. With both drives plugged in. Is Windows sda or sdb?


In BIOS choose to boot Ubuntu drive and run this:

sudo update-grub

That should find the Windows install.

If not we will need a new run of Bootinfoscript or BootInfo to see what is where now.

---

### Post by Ren123 on 2012-04-30
After manually mounting 
sudo mount /dev/sdXY /mnt
sudo mount /dev/sdXY /mnt/boot
I did a sudo update-grub ran Boot script looks fine

Now from BIOS when I configure boot device to  80 gb harddrive
Grub 2 is shown
The PC now boots normaly in ubuntu.
**On selecting Windows the PC reboots.**

Now from BIOS when I configure boot device to 360 gb one 
PC boots normally in Windows

---

### Post by oldfred on 2012-05-01
Is this a PC/BIOS that can only boot from one drive. Some old Dell computers were that way. 

Are both drives SATA or is one SATA & one PATA? Or both PATA and system only boots from primary master?

Is Windows configured for the first drive and when you add the Ubuntu drive is it then the second drive? Grub often adds map or mapdevice commands to get Windows to think it still is first drive.

Run 
sudo update-grub
and see if it works on reboot.

If not:
Post new run of boot info script or run it from Boot-Repair. With both drives configured and Windows not booting. 
Run 
sudo update-grub

---

### Post by Ren123 on 2012-05-01
Yes, unfortunately only one SATA can be configured to boot.
Both HDDs are SATA.

There is one more issue.
The root FS in Ubuntu is not mounting or pointing to a different UUID
 Unable to mount mount_point
mount:special device UUID=23046....does not exist.

---

### Post by Ren123 on 2012-05-01
[ATTACH]217003[/ATTACH]
Boot info

---

### Post by Ren123 on 2012-05-01
> **Ren123 said:**
> Yes, unfortunately only one SATA can be configured to boot.
Both HDDs are SATA.

There is one more issue.
The root FS in Ubuntu is not mounting or pointing to a different UUID
 Unable to mount mount_point
mount:special device UUID=23046....does not exist.

[SOLVED] unable to mount mount_point
Did a sudo nano -Bw /etc/fstab
Deleted the line starting from UUID=23056.... I was confident in removing this becoz This line was added by myself.
**[COLOR="Red"]But Will it create new problems or issues??[/COLOR]**

Latest Boot Info [ATTACH]217005[/ATTACH]

Still facing Ubuntu Grub2 Select Windows Restart Issue :(

---

### Post by darkod on 2012-05-01
I can't see anything wrong. All boot files are in place, for both windows and ubuntu. It looks good.

The only thing is that you can delete the grub/core.img file from /dev/sdb1. The boot/grub/core.img needs to be there, but not the grub/core.img.

Other than that, I can't see anything wrong.

There is still the chance that the windows boot process is doing the reboot. Because once you select windows in the boot menu, the windows boot process takes over and ubuntu doesn't have anything to do with it.

---

### Post by majtol on 2012-05-02
Hi everyone,
I've got same/similar problem, which has something to do with ntfs mount/umount and uuid of partition and nt kernel. I have trouble with it when for example I'm shuting down win, than start linux, than mount it and umount, than shut down and again start windows it works, but if windows is not properly closed, or partition under lin is not properly umounted I cannot boot windows anymore.
either with old grub legacy hadnt have this trouble:lolflag:

---

