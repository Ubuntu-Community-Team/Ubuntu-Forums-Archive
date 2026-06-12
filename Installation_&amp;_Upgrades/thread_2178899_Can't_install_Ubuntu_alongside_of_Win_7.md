---
title: "Can't install Ubuntu alongside of Win 7"
date: 2013-10-05
forum: Installation &amp; Upgrades
---

### Post by sequimbob on 2013-10-05
I am running an HP Pavilion g7-2069wm Notebook PC, AMD A8 Vision 64bit processor with Windows 7 Home Premium, 6gb ram, 600gb hard drive partitioned as follows:

System: 199MB NTFS Healthy (system, Active, Primary Partition
(C: ) 353.58GB NTFS Healthy )(Boot, PageFile, Crash Dump, Primary Partition)
326.25GB Unallocated
Recovery (D: ) 18.51GB NTFS Healthy (Primary Partition)
HP_TOOLS (F: ) 102MB FAT32 Healthy (Primary Partion)

I placed the Unbuntu 12.04 CD in the drive, booted with the cd and then selected install alongside of Windows.  The installation appeared to start then the following messages appeared:

* Checking battery state...												                [OK]
* Stopping System V runlevel compatibility										        [OK]
udevd[5130]:  udisk-parted-id /dev/sda2' [6204] terminated by signal 15 (Terminated)

acpid: exiting
Checking for running unattended-upgrades:
					  speech-dispatcher disabled; edit /etc/default/speech-dispatcher
* Asking all remaing processes to terminate...										
* All processes ended within 2 seconds....										        [OK]
nm-dispatcher.action: Caught signal 15, shutting down...								[OK]
modem-manager[1777]: <info>  Caught signal 15, shutting down...	

* Deconfiguring network interfaces...										  	        [OK]
* Unmounting temporary filesystems...											        [OK]
* Deactivating swap...													                [OK]
* Stopping remaining crypto disks...											        [OK]
* Stopping early drypto disks...											                [OK]
unmount: /run/lock: not mounted
unmount: /run/shm: not mounted
* casper is resyncing snapshots and caching reboot files...

Please remove installation media and close the tray (if any) then press enter

Once I remove the media, close the tray and press enter, it reboots immediately into Windows.

It appears that udevd[5130]:  udisk-parted-id /dev/sda2' [6204] terminated by signal 15 (Terminated) terminated the install but I haven't found any info on what this is or what causes it.

Anyone have any idea why it won't install.  I have used this same disk to install before on this same computer.  Then I had to send the computer back to HP for service and they re-installed Windows and wiped out the Ubuntu installation.  Sure would like to get it back.  Unfortunately I still need Windows for a couple of tasks or would just install Ubuntu over it.  Sure could use some help here. Thanks

---

### Post by ubfan1 on 2013-10-05
You already have the max of four primary partitions, so even though you have enough free space, you cannot create another.  Backup a partition next to the free space (and if it's the last one, so much the better, but maybe not necessary), delete the partition, and make an extended partition from all the free space.  Now logical partitions may be added in the extended partition, make one to replace the one you deleted, and make any linux install paritions you want (/ root  and swap at a minimum).  Now the installer should succeed.

---

### Post by Mark Phelps on 2013-10-06
Since you already have four partitions, that is the maximum allowed. Simply removing HP_TOOLS is not the solution -- as it is too small to be of any use.

So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition.  Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive.  Then, use the MR option to create and burn a Linux Boot CD.

Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by sequimbob on 2013-10-07
Okay,  I used the Windows MiniTool Partition Wizard and changed my C: partition to a logical partition and then shrunk that partition to it's minimum size, leaving me a free partition into which Ubuntu installed with no problem. Thanks for your help.  It is greatly appreciated. I will mark this as solved.

---

