---
title: "Ubuntu 22.04 install on Dell R710 with RAID-10"
date: 2024-04-01
forum: Installation &amp; Upgrades
---

### Post by lawadm1 on 2024-04-01
I'm experimenting with an extra Dell R710 that we have and I want to install Ubuntu with a RAID 10 config (PERC H700).

The RAID-10 is configured: 6 physical drives at 4 TB each.
Span 0 (Drive 0 and 1)
Span 1 (Drive 2 and 3)
Span 2 (Drive 4 and 5)

When I attempt to install Ubuntu from the USB drive, it just spins and spins on the Ubuntu logo screen.  Is there a step that I missed, or will it take a while to come up with the setup options because of the number of drives?

Jeff

---

### Post by yuralamov on 2024-04-01
Ubuntu-desktop?
Maybe better ubuntu-server?

---

### Post by ActionParsnip on 2024-04-01
Is the PERC known to work with Ubuntu?

---

### Post by yancek on 2024-04-01
Does the link below describe your hardware and also, answer to the question in post 2?

[https://i.dell.com/sites/csdocuments/Shared-Content_data-Sheets_Documents/en/R710-SpecSheet.pdf](https://i.dell.com/sites/csdocuments/Shared-Content_data-Sheets_Documents/en/R710-SpecSheet.pdf)

Based on the information you posted, this computer has no other OS installed and no data, correct?  Have you read through the instructions on the Ubuntu site on installing desktop/server?    What software did you use to write whichever Ubuntu iso you are using to the USB drive?  Have you done an installation of Ubuntu using RAID previously so that you are familiar with the process?

---

### Post by lawadm1 on 2024-04-01
This R710 server was just a server to hold our Veeam backups, and used to have Windows 10 on it.  Something happen ed to that server, and we purchased a new server to hold the Veeam backups.  Now I just want to install Ububtu desktop or server on this spare R710 and create samba partitions to hold the Veeam backups.

I am not familiar with this process, and I'm just trying to research and wing it so to speak.  Maybe I need to delete the RAID virtual disk and create a new RAID 10 setup.

I used Rufus to create the USB drive with the Ubuntu iso.

---

### Post by yuralamov on 2024-04-02
install the ubuntu-server and look at the logs in real time. Hard raid (if it works) configuration has nothing to do with it.

---

### Post by lawadm1 on 2024-04-02
Attempting to install Ubuntu server did provide some additional information in the log. 

I get this error:  
Metadata in windows cache, refused to mount.  NTFS partition is in an unsafe state, please resume and shutdown windows fully (no hibernation or fast restart).

The problem is windows became corrupt and will not boot or repair.  Will I need to reinstall windows first before attempting to install Ubuntu?

---

### Post by yancek on 2024-04-02
The information you posted (post 7) indicates that the device has partitions with windows filesystems that were left in a hibernated state which is the reason for that message.  If you want to install Ubuntu server, why have windows filesystems on your partitions as they will be pretty useless.  Since you don't have any data on the device, create a new partition table on it, then before or during the install create your partitions with Linux filesystems.

If you want to use the drive to store some kind of windows backups, you can create an ntfs partition for that along with the Linux partitions for Ubuntu.  How does windows fit in?  Is that from other computers/drives?  Are you planning to install windows on this computer also?  If you don't plan to install windows on this computer, you will need to create a new partition table which will basically overwrite anything on the drive.  Other than booting windows and turning off hibernation, that's the only way I am aware that you can do it.

---

### Post by lawadm1 on 2024-04-02
We didn't need anything on those disks.  The new server now has all of the backup files.

I deleted the VD#0 and re-configured the RAID with fast init and now I am able to install Ubuntu.

Thanks for the help on this.

---

### Post by lawadm1 on 2024-04-02
Onto my next issue...

I have Ubuntu server installed with a hardware RAID-10 (PERC H700) setup. 
[COLOR=#000000]The RAID-10 is configured: 1 virtual drive with 6 physical drives at 4 TB each.[/COLOR]
[COLOR=#000000]Span 0 (Drive 0 and 1)[/COLOR]
[COLOR=#000000]Span 1 (Drive 2 and 3)[/COLOR]
[COLOR=#000000]Span 2 (Drive 4 and 5)[/COLOR]  

When I run fdisk -l I receive the following results:

Device       Start         End     Sectors  Size Type
/dev/sda1     2048     2203647     2201600    1G EFI System
/dev/sda2  2203648     6397951     4194304    2G Linux filesystem
/dev/sda3  6397952 23438817279 23432419328 10.9T Linux filesystem

My question is how do I get each physical drive to show up as a separate drive?  Or since it's a RAID 10 setup, is drive 0 and 1 a single drive, 2 and 3 a single drive, 4 and 5 a single drive?

Additional info:
NAME HCTL       TYPE VENDOR   MODEL                    REV SERIAL                           TRAN
sda  2:2:0:0    disk DELL     PERC H700               2.10 00a77c0b0f3be89e2d00ba585bb0bc82
sr0  0:0:0:0    rom  Optiarc  Optiarc DVD RW AD-7590S 1.02 Optiarc_DVD_RW_AD-7590S          ata

---

### Post by yuralamov on 2024-04-02
what you have configured in hard raid is seen by the OS

---

### Post by MAFoElffen on 2024-04-05
> **lawadm1 said:**
> Onto my next issue...

I have Ubuntu server installed with a hardware RAID-10 (PERC H700) setup. 
[COLOR=#000000]The RAID-10 is configured: 1 virtual drive with 6 physical drives at 4 TB each.[/COLOR]
[COLOR=#000000]Span 0 (Drive 0 and 1)[/COLOR]
[COLOR=#000000]Span 1 (Drive 2 and 3)[/COLOR]
[COLOR=#000000]Span 2 (Drive 4 and 5)[/COLOR]  

When I run fdisk -l I receive the following results:

Device       Start         End     Sectors  Size Type
/dev/sda1     2048     2203647     2201600    1G EFI System
/dev/sda2  2203648     6397951     4194304    2G Linux filesystem
/dev/sda3  6397952 23438817279 23432419328 10.9T Linux filesystem

My question is how do I get each physical drive to show up as a separate drive?  Or since it's a RAID 10 setup, is drive 0 and 1 a single drive, 2 and 3 a single drive, 4 and 5 a single drive?

Additional info:
NAME HCTL       TYPE VENDOR   MODEL                    REV SERIAL                           TRAN
sda  2:2:0:0    disk DELL     PERC H700               2.10 00a77c0b0f3be89e2d00ba585bb0bc82
sr0  0:0:0:0    rom  Optiarc  Optiarc DVD RW AD-7590S 1.02 Optiarc_DVD_RW_AD-7590S          ata

I'm really sorry I didn't see this earlier. Been quite busy working and had the day off today.

I have a Dell PE T720 with dual Xeons... Mine has 18x 2.5" SAS/SATA Hotswap bays.

The Dell PERC H700 used to only support 2TB drives. With the newer firmware it recognizes up to 8TB drives. Make sure your firmware is up to date.

The PERC controllers don't support JBOD mode, but I found a work-around to get around that to pass through the drives individually. In the PERC BIOS setup, select each drive as a single drive RAID0 array. That will pass the drives through to the OS individually.

I really recommend that to all Users using that hardware. Years of experience with Dell and Linux has shown me that doing it that way opens up so much more in possibilities in what you can do with your storage. 

I went through my hardware RAID, mdadm, LVM2, then ZFS phases. I learned a lot with how each grew on each other in data integrity, flexibility and possibilities. With LVM2 & ZFS (both are Volume Managers), you can do a lot of things on a live filesystem! I really like not having to be offline working on things when I can adjust things on the fly. Like being able to replace a failed drive while the system is still up and running, live. You can do all that live, except on the root drive.

You cannot do that on Hard RAID. That is why I evolved to passing drives through, and using the RAID controller as an HBA. There is hacked firmware to flash old PERC's as an HBA, but that's another story.

Plan your system for that, and adjust. You can always add some small drive(s) for your system (OS) that are easier to change out and replace. Make things "modular". Expect things might happen. (They do eventually.) That makes long-term easier and less painless when a disaster happens. It also makes system migration to new releases easier.

I tend to segregate my storage into OS, & data. data I split up into types & mission. 

I tend to want to do ZFS-On-Root, and ZFS based storage solutions these days. I've come full-circles with ZFS since I first learned it with OpenSolaris in 2005. That is what I use for most of my storage solutions today, with RAIDZ2 and RAIDZ3. 

With 6x 4 TB drives, in RAIDZ3, that's almost 20TB of storage, with the ability to lose 3 drives and still be up and running. And the striping increases I/O performance greatly... Something to think about. RAID 10 with 3 spans, it depends which 2 drives fail, where before it's completely down. You can safely lose 1 drive. With RAIDZ2, I can have 2 drives fail and still be up.

By the way, Dell does have a PowerEdge Ubuntu Repo for some of their offerings... Good to check out if curious.

EDIT:
I might also mention that I used to work as a Dell, HP and Lenovo Onsite Warranty Tech. And I've personally used Dell PE Server hardware with Windows Server & Linux since 2008. I am also an IT Consultant. Not that I claim to know everything, but I have been "exposed" to a lot of things. Both the good and bad. LOL

---

