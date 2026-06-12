---
title: "RAID issues (NEWBIE)"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by turbo_h4 on 2011-08-07
I've been trying all day to mount my RAID1 setup but no luck. Can anyone help?
It's on an old PC my friend passed to me so I decided to use it as NAS+HTPC machine.

Asus Striker II Formula
Q6600 ?
4x 1GB ram
1x 250GB (ubuntu installation)
2x 2TB seagate (RAID 1 for NAS)

-I've tried using the disk manager (file -> create ->  ....), doesn't work.
-tried using Gpart Live but couldn't figure it out
-tried using the "sudo mdadm ..." doesn't work (drive not suitable)
-tried fdisk both drives to type fd, cat /proc/mdstat still doesn't show anything usable...

ARGH!!!

I've been searching all day but haven't found any working solutions.
Also, do I need ubuntu server or will desktop suffice? I will share files to Mac and Windows machines.

---

### Post by MAFoElffen on 2011-08-08
> **turbo_h4 said:**
> I've been trying all day to mount my RAID1 setup but no luck. Can anyone help?
It's on an old PC my friend passed to me so I decided to use it as NAS+HTPC machine.

Asus Striker II Formula
Q6600 ?
4x 1GB ram
1x 250GB (ubuntu installation)
2x 2TB seagate (RAID 1 for NAS)

-I've tried using the disk manager (file -> create ->  ....), doesn't work.
-tried using Gpart Live but couldn't figure it out
-tried using the "sudo mdadm ..." doesn't work (drive not suitable)
-tried fdisk both drives to type fd, cat /proc/mdstat still doesn't show anything usable...

ARGH!!!

I've been searching all day but haven't found any working solutions.
Also, do I need ubuntu server or will desktop suffice? I will share files to Mac and Windows machines.How (physically and logically) is your RAID defined?  You mention it as if it is hardware RAID... or is it software RAID?

Ubuntu and diskutilities will not see yje RAID until the RAID is defined.  But the Alternate Install disk > partitioner will, where you can see what's going on or do what you need to do. After it gets going, then you'll have to mount it.

Along the lines of some of your other comments/questions....  You can server services, providing file sharing services, from the Desktop Edition or from The Server Editiom.  What services are you going to provide? SMB, SMBFS. CIFS, NFS?  The first 3 would be through SAMBA.  The last through NFS.

---

### Post by turbo_h4 on 2011-08-08
Thanks for the quick reply...

It's a BIOS raid so it's a software raid I think (99% sure).
The two 2TB drives are defined in the BIOS as RAID enabled, inside the BIOS menu as RAID1 (mirroring). The 250GB is not RAID enabled in the BIOS.

As for linux, I'm not sure what is meant by defined. They are both now set to Linux raid autodetect (type FD using fdisk). Have tried a bunch of things but nothing worked so I'm not sure the state of them.

As for services, I plan to run SMB and AFP. Other things will just be a media center like operation for TV output.

---

### Post by turbo_h4 on 2011-08-08
just thought of more to add...

250GB is /dex/sda
the 2x2TB are /dev/sdb and /dev/sbc

I tried partitioning linux raid on sdb and sdc to make sdb1 and sdc1.

---

### Post by YesWeCan on 2011-08-08
would you post the output of
sudo sfdisk -luS

I am assuming your 2TB disks are not being used for anything already, like Windows.

You don't want to use your mobo RAID. This is just for Windows use. So disable all bios RAID options. If these disks have been used for RAID by Windows in the past, it is necessary to erase their metadata blocks:
sudo dmraid -E -r /dev/sdb
sudo dmraid -E -r /dev/sdc

Now try creating a RAID on them using Disk Utility.

---

### Post by turbo_h4 on 2011-08-08
I removed the mobo RAID.

Then I fresh installed ubuntu desktop. deleted the partitions and made them again using fdisk.
Disk utilities sees the disks but they're not selectable for raid array.


sudo sfdisk -luS 

shows my sda partitoned 


the others sdb and sdc each show partition one as type FD, using all sectors. partitions 2-4 are all 
0 - Empty


I tired using the dmraid command but it doesn't exist. The drives are new, never had windows running.

---

### Post by turbo_h4 on 2011-08-08
update....if I delete the partitions, disk utilities lets me select the drives, but when creating the arrays, I get a "error creating RAID array" details "Error starting job: Failed to execute".

The drives are then automatically partitioned back to linux RAID autodetect.

---

### Post by turbo_h4 on 2011-08-08
Got the arrays to work. forgot I didn't have mdadm installed after the fresh ubuntu install.
Many thanks to all that helped.

Further question, what's the best way to format the drive, and to what filesystem? I wouldn't mind using EXT3/4 even though I would have to continue using linux to use the drives. However, I'm most concerned about hard drive failure, which would be easiest to replace the drive and recover the data and rebuild the RAID?

---

### Post by YesWeCan on 2011-08-08
ext4 is the most reliable.

---

