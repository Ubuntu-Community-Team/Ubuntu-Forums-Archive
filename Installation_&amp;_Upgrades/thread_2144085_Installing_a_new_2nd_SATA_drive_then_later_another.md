---
title: "Installing a new 2nd SATA drive then later another disk to RAID 1."
date: 2013-05-11
forum: Installation &amp; Upgrades
---

### Post by Windowsxpnomore on 2013-05-11
I am a complete beginning to Ubuntu. I want to move 2 3Tb Raid 1 discs in ZFS format to Ubuntu server 12.04. I understand that Ubuntu cannot access the ZFS, hence I will split the Raid getting one disk working on Ubuntu and setup the Raid on Ubuntu.

I have installed Ubuntu server 12.04 on to a 80Gb Sata disk. This I am going to use as the "system" disk and boot disk.
I have then fitted a 3Tb GParted Sata disk
I have booted with Gpart and set the disk up using VLM2  only because if I use ext4 46Gb of the 3Tb disk is not used. Some 2% why?

Then thru a battle with google I have got the disk volume and drive named thru VLM and mounted and can copy data on to it. (Although I have only copied a few Gb of the 1.8Tb to copy). But I have no confidence in what I have done is correct and no idea of the next step ! I want place another identical 3Tb drive in and Raid 1 this.

I am willing to ditch all I have done so far. No data has been lost. I have 1 3Tb still in the other server (although now not RAID1).

Is this the best guide to follow for installing the drive [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive), copy the data across, setup the 2nd drive (same instructions) and then RAID 1 (instructions?).

Any help I would appreciate it - thanks.

---

### Post by darkod on 2013-05-11
No, you need to create the raid1 first, not last. Whether you use LVM or not, it's up to you. The 2% I guess is the journaling info that the ext4 filesystem keeps (to be able to recover corruptions). Unless these 2% are really important to you, you can skip using LVM because it will add another layer of complexity that you need to worry about.
But on the other hand LVM can help you expand your storage in the future. For example, you can add two new disks and create new raid1 array from them, then join it to the LVM and the OS will see one huge continuos space, not two arrays. I think you will lose the 2% inside the LVM too, because when you format the LV as ext4 it will do the same. Now it only looks like LVM allowed you to use the whole disk because the ext4 is inside the LVM.

But in any case, you need to start over and do the raid1 first. The 3TB disk with the data and ZFS is in another machine, right?

Lets assume in your ubuntu you now have the 80GB OS disk as sda, and the 3TB disk as sdb.
Open Gparted (or use parted in the command line if that's easier for you), select /dev/sdb, delete the current LVM partitions. Make one single partition of type RAID (or Physical Device for RAID), or depending how it's called exactly in Gparted. Apply the Gparted changes. So that will be /dev/sdb1 and it will be only partition on the disk.

After that, install the mdadm package because the desktop OS does not have it, and from that sdb1 partition create a raid1 array telling mdadm that it has two raid members and one member missing (the second disk you will add later):
```
sudo apt-get install mdadm
sudo mdadm --create --verbose --level=1 --raid-devices=2 /dev/md0 /dev/sdb1 missing
```

That will create the /dev/md0 device. Wait until it's fully created, you can watch the process with:
```
watch cat /proc/mdstat
```

or simply check it from time to time with only:
```
cat /proc/mdstat
```

Once that is done, the /dev/md0 is ready to use. Whether you will use it directly or for LVM, it's up to you. If you decide to use LVM, you will use that as physical device, not sdb1 as you did earlier.
If you decide to use it directly, you will of course need to format it:
```
sudo mkfs.ext4 /dev/md0
```

That should be it for now. When done, we can discuss how to add the other disk to the array.

---

### Post by Windowsxpnomore on 2013-05-11
ok, thanks done all that and mdadm -D shows:

@MediaServer:~$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sat May 11 11:52:01 2013
     Raid Level : raid1
     Array Size : 2930133824 (2794.39 GiB 3000.46 GB)
  Used Dev Size : 2930133824 (2794.39 GiB 3000.46 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Sat May 11 11:54:52 2013
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : MediaServer:0  (local to host MediaServer)
           UUID : 94c8b9dd:8a6c9061:83d1dd29:2bbeef2b
         Events : 2

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed

I now need to copy over the data from the other server, with the 3T ZFS mounted drive to this disk.
How do I mount this disk? As I cannot see it.
I cannot install the missing disk from the array yet as it holds the only copy of my data now.

Many thanks for your help.

---

### Post by darkod on 2013-05-11
If you decide to use it without LVM (directly), you need to format it first:
```
sudo mkfs.ext4 /dev/md0
```

After that is done, decide whether you want to mount it temporarily, or right away permanently. For temporarily you can use /mnt. For permanently you need to create a mount point (new empty folder) like /data for example, and use that as mount point. You will also need to create entry in /etc/fstab to mount it automatically at boot, but right now for copying you can skip that. You only need to remember that it won't mount automatically after reboot. So, depending what you decided to use, try something like:
```
sudo mount /dev/md0 /mnt
or
sudo mkdir /data
sudo mount /dev/md0 /data
```

After that you can start copying to /data (/mnt).

---

### Post by Windowsxpnomore on 2013-05-11
thanks - i decided not to use LVM.
so did the following
 
cd \mnt
mkdir data

sudo mount /dev/md0 /mnt/data

df shows:
Filesystem                    1K-blocks    Used  Available Use% Mounted on
/dev/mapper/MediaServer-root   60201060 2805116   54337872   5% /
udev                            8154060       4    8154056   1% /dev
tmpfs                           3265548     968    3264580   1% /run
none                               5120       0       5120   0% /run/lock
none                            8163860       0    8163860   0% /run/shm
/dev/sdb1                        233191   52483     168267  24% /boot
/dev/md0                     2884154400  205808 2737441904   1% /mnt/data


when I /mnt/data I cannot create any files. eg vi reports not being able to write.
so I did
cd /mnt
sudo chmod 777 * -R

now I can write to /mnt/data

I now want to start copying over my data.

ssh 192.168.2.111 and I can see a directory called PENDRIVE when I do a ls.

ls 
drwxrwxrwx    4 gary  wheel    63 Dec  4 12:24 PENDRIVE/

back on Ubuntu server. (192.168.2.111 is the other ZFS server).

scp 192.168.2.111:/PENDRIVE/* .
gary@192.168.2.111's password:
scp: No match.

 scp 192.168.2.111:/PENDRIVE .
gary@192.168.2.111's password:
scp: /PENDRIVE: No such file or directory

 scp 192.168.2.111:/PENDRIVE/ .
gary@192.168.2.111's password:
scp: /PENDRIVE: No such file or directory

but PENNDRIVE does exist and there are files in the directory.
-------
I have Samba installed also 
and can happy drag and drop the between the ZFS server and the Ubuntu server, but must be moving the data from the ZFS machine to my windows box then to Ubuntu as Windows networking reports equal amounts of received and sent data. If I could scp the data from ZFS machine to Ubuntu directly this would be much quickly. I need to move 1.8Tb.

thanks for your help so far.

---

### Post by Windowsxpnomore on 2013-05-11
ok, sorry fixed that the remote server (ZFS) is mounted under /mnt/RAIDZ 

I can see it now and copy across.

---

### Post by darkod on 2013-05-11
Hold on. On the machine with the ZFS and the data, do you have samba or similar? I assume you do, otherwise how does windows conect to it?

If you do have a samba share running, you should be able to mount the share directly from the ubuntu server and you can copy directly.

If the share doesn't need a password and it's a samba share, try something like:
```
sudo mkdir /mnt/tempzfs
sudo mount -t cifs //zfsserverIP/sharename /mnt/tempzfs -o guest
```

If that works, you should be able to copy from /mnt/tempzfs to /mnt/data.

---

### Post by darkod on 2013-05-11
OK, I didn't see your previous post. Glad you got it working.

When the copying is done and you have verified the data, you can add the other disk to the raid1.

---

### Post by Windowsxpnomore on 2013-05-12
Thanks !!!

yes this worked - 

sudo mount -t cifs -o username=gary //192.168.2.111/Share /mnt/tempzfs

7 directories copied over last night. 3 in progress 
This was just in time to start copying over the 900G directory. One more waiting.

This is when i wish had a Gig Router !

I am very appreciative of your time and help on this

---

### Post by Windowsxpnomore on 2013-05-13
ok, all the data has copied across. I've checked totals and are happy.

df shows
Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/MediaServer-root   58G  2.8G   52G   6% /
udev                          7.8G  4.0K  7.8G   1% /dev
tmpfs                         3.2G  1.3M  3.2G   1% /run
none                          5.0M     0  5.0M   0% /run/lock
none                          7.8G     0  7.8G   0% /run/shm
/dev/sdb1                     228M   52M  165M  24% /boot
/dev/md0                      2.7T  1.4T  1.2T  55% /mnt/data
//192.168.2.111/Share         2.7T  1.4T  1.4T  52% /mnt/tempzfs

mdadm shows:
/dev/md0:
        Version : 1.2
  Creation Time : Sat May 11 11:52:01 2013
     Raid Level : raid1
     Array Size : 2930133824 (2794.39 GiB 3000.46 GB)
  Used Dev Size : 2930133824 (2794.39 GiB 3000.46 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Mon May 13 20:13:12 2013
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : MediaServer:0  (local to host MediaServer)
           UUID : 94c8b9dd:8a6c9061:83d1dd29:2bbeef2b
         Events : 107342

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed


I guess the next part is to power off the ZFS server move the HD and insert into Ubuntu server?

---

### Post by darkod on 2013-05-13
Yeah. You would need to move the disk, delete all partitions on it and again create one big partition for raid as you did with the first disk. Lets say that partition will be /dev/sdb1.

You simply add it to the array with:
```
sudo mdadm /dev/md0 --add /dev/sdb1
```

It will start syncing automatically and you can watch the progress in /proc/mdstat.

Once done it should be a full raid1 mirror with two members.

---

### Post by Windowsxpnomore on 2013-05-15
thanks for that.

Added the disk. its appeared as /dev/sda1 so cmd was 
sudo mdadm /dev/md0 --add /dev/sda1

cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sda1[2] sdb1[0]
      2930133824 blocks super 1.2 [2/1] [U_]
      [>....................]  recovery =  0.1% (5542272/2930133824) finish=286.5min speed=170118K/sec


So Im in the hands of the OS now to mirror the data. I'll either end up with a mirrorred pair of disks or a pair of disks with no data on. (joke).

Find out in little under 5 hours.

Many thanks for your help. If I could shake your hand to say thanks I would ! :P

---

### Post by Windowsxpnomore on 2013-05-16
just to report that all is well

/dev/md0:
        Version : 1.2
  Creation Time : Sat May 11 11:52:01 2013
     Raid Level : raid1
     Array Size : 2930133824 (2794.39 GiB 3000.46 GB)
  Used Dev Size : 2930133824 (2794.39 GiB 3000.46 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Thu May 16 19:22:54 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : MediaServer:0  (local to host MediaServer)
           UUID : 94c8b9dd:8a6c9061:83d1dd29:2bbeef2b
         Events : 113681

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       2       8        1        1      active sync   /dev/sda1



many thanks !:)

---

