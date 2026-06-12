---
title: "Troubleshooting Maverick installation on IBM T42"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by jimbobs on 2010-11-06
Installed Maverick on a T42 (Pentium M 1.70GHz, 1GB RAM, 20GB harddrive with 3.5GB available space) and everything is fine - except machine freezes occasionally and will not respond to anything except power cycling.  Fires back up again and works fine until it happens again.  It seems to happen when I am using any browser.  Being new to Linux and Ubuntu, I have no idea how to even begin diagnosing the problem.  Can anyone help or point me towards a tutorial on troubleshooting this installation?

---

### Post by Quackers on 2010-11-06
3.5GB is not really enough space for Ubuntu to work in. You need to make more space for it.

---

### Post by jimbobs on 2010-11-07
> **Quackers said:**
> 3.5GB is not really enough space for Ubuntu to work in. You need to make more space for it.

Tks, I wondered about that.  I have just changed the original 20GB drive to a 60GB hard drive using ddrescue and will see what happens.

---

### Post by jimbobs on 2010-11-07
> **jimbobs said:**
> Tks, I wondered about that.  I have just changed the original 20GB drive to a 60GB hard drive using ddrescue and will see what happens.

Problem appears to be still there.  Moved my installation to a 60GB drive and checked that it was working OK which it appeared to be.  Then fired up Firefox and 20 minutes later - frozen!

---

### Post by Quackers on 2010-11-07
If you have just moved the installation to a bigger drive, you will need to expand the file system to fill the larger space. Otherwise it will still think it's 3.5GB. Sadly I can't remember the command. I'll get back to you!

---

### Post by garvinrick4 on 2010-11-07
Open a terminal and run:
```
sudo fdisk -l 
```
that is a lower case L

```
sudo parted -l
```
that is a lower case L
Copy and paste results to your thread if you would:

---

### Post by jimbobs on 2010-11-07
Powered up this morning to discover a new problem: Maverick opens, allows me to log on and accepts password, gives me the jingle and wallpaper and then freezes with only the (frozen)mouse pointer on screen.  Arghhhhh ......

OK, got it running through repeated power cycles and reboots, and here is my log:

ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf983f983

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2386    19165513+  83  Linux
/dev/sda2            2387        2432      369495    5  Extended
/dev/sda5            2387        2432      369463+  82  Linux swap / Solaris

ubuntu:~$ sudo parted -l

Model: ATA ST960822A (scsi)
Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  19.6GB  19.6GB  primary   ext3            boot
 2      19.6GB  20.0GB  378MB   extended
 5      19.6GB  20.0GB  378MB   logical   linux-swap(v1)


Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only.
Error: /dev/fd0: unrecognized disk label

---

### Post by garvinrick4 on 2010-11-09
ubuntu:~$ sudo parted -l

Model: ATA ST960822A (scsi)
Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  19.6GB  19.6GB  primary   ext3            boot
 2      19.6GB  20.0GB  378MB   extended
 5      19.6GB  20.0GB  378MB   logical   linux-swap(v1)

Only 20 gig of partitions in 60 gig drive and you say out of space.
```
df -h
```
You might have to resize your partition in gparted to assume more of 
the 60 gig since you swapped out your 20 gig.

---

### Post by zaxon on 2010-12-20
i have T42 with very similar configuration and it freezes exactly the same way as [jimbobs]("http://ubuntuforums.org/member.php?u=661762")'s. at first i thought that it is so because T42 common problem related to bad GPU but i have dualboot wiht W7 and W7 works perfectly fine even on hard load aka games and everything. i can not find anything specific about that problem from system logs so i am really confused what to do or what to check next.

---

