---
title: "Upgrade to 9.10 failed; can't boot and have encrypted RAID disk"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by tonywhelan on 2010-02-23
I was running Ubuntu 9.04 Desktop on a headless Pentium 4 machine which is our file, mail, web & fax server. The two x 250GB SATA hard disks were in a RAID 1 array with full disk encryption.

Ran the 9.10 upgrade via WEBMIN and it failed. I should have known then to copy over everything to a backup disk, but instead I rebooted. 

On restart the machine accepted my encryption passphrase but promptly hung with a mountall symbol lookup error - code 127. 

So I can't start the machine to get at the disks, and using a Live CD is useless as it has no way to open the RAID array to get at the encrypted partitions.

Although we have data backed up (as at last night) I'd hoped not to have to rebuild the entire server from scratch. But its looking bad.

I have taken one drive out and plugged it into another machine (Hercules), and the partitions show up as /dev/sdb1 /dev/sdb2 /dev/sdb3. 

If it weren't for RAID, I could open /dev/sdb2 the main partition) in Disk Utility and enter my encryption passphrase to get access. But RAID adds a layer of obstruction that I have not yet overcome.

I used mdadm to scan the above partitions and created the /etc/mdadm.conf file, which I edited to show the 2nd drive as missing (rather than risk corrupting both drives). 

I activated the RAID array with mdadm, and cat shows:

```
root@HERCULES# cat /proc/mdstat
Personalities : [raid1] 
md1 : active raid1 sdb3[0]
      1815232 blocks [2/1] [U_]
      
md0 : active raid1 sdb2[0]
      242187840 blocks [2/1] [U_]
      
md2 : active raid1 sdb1[0]
      192640 blocks [2/1] [U_]
      
unused devices: <none>

``` 

So the array is active. My system files and data are all in /dev/sdb2 in /dev/md0 (sdb3/md1 is for swap, sdb1/md2 is the boot).

But I'm stumped as to how I can get access to the encrypted file system in the array. FWIW, mdadm for /dev/sdb2 returns this:

```
root@HERCULES# mdadm --examine /dev/sdb2
/dev/sdb2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 9e52263e:6462f4b8:6f5a7fad:1e86d8e9
  Creation Time : Sat Jul 18 13:37:59 2009
     Raid Level : raid1
  Used Dev Size : 242187840 (230.97 GiB 248.00 GB)
     Array Size : 242187840 (230.97 GiB 248.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0

    Update Time : Wed Feb 24 13:15:33 2010
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0
       Checksum : de17113f - correct
         Events : 54


      Number   Major   Minor   RaidDevice State
this     0       8       18        0      active sync   /dev/sdb2

   0     0       8       18        0      active sync   /dev/sdb2
   1     1       0        0        1      faulty removed

```

and mdadm for /dev/md0 gives this:

```
root@HERCULES# mdadm --examine /dev/md0
mdadm: No md superblock detected on /dev/md0.

```

I've been searching the web for hours but have yet to find someone with a solution to this situation. 

If anyone has a thought on how to access this disk I'd be pleased to hear from you. 

In the meantime I will start building a new (9.10) machine from scratch, without RAID, 'cos that's probably going to be necessary. :cry:

---

### Post by tonywhelan on 2010-02-24
> **tonywhelan said:**
>  <snip>

But I'm stumped as to how I can get access to the encrypted file system in the array. 


An update.

Came back to the hercules machine after a couple of hours doing other things ..  and opened nautilus  ... and behold it is seeing the encrypted partitions and I can open the main one with my passphrase. 

Now to do some serious backups .... and hope the rebuild is not too traumatic.

---

