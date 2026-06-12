---
title: "Problem Creating RAID 5"
date: 2011-12-08
forum: Installation &amp; Upgrades
---

### Post by sibleytr on 2011-12-08
I am trying to create an Ubuntu Server, with a RAID5 storage area.

The current ROOT and SWAP are running on /dev/sda1 and /dev/sdb1 as /dev/md0 and /dev/md1 (RAID 1). By itself the Ubuntu Server OS is working perfectly.

The RAID 5 is causing some frustration and I believe it has to do with a single (possibly bad) drive. The best I can tell /dev/sdc will not format to "fd" (Linux Raid Auto).

All of the drives being used for the servers RAID 5 are recycled from used backup drives when I had Windows. For whatever reason I cannot delete the previous label and partition on /dev/sdc drive. 

The "blkid" shows as:

/dev/sdc1: LABEL="TRS_320" UUID="7864D7DF64D79DE6" TYPE="ntfs" 

Tried using "sudo fdisk /dev/sdc" to remove partition and recreate Linux Raid, but no luck.

Anyone have any ideas on how to get the drive formatted or at least confirm that the drive is still good?

:confused:

---

### Post by darkod on 2011-12-09
Even though you are installing the server version, if you have the ubuntu desktop cd at hand you can run it in live mode (Try Ubuntu option) and use Gparted to try and delete the partitions on the drive and create raid type partition(s).

---

### Post by sibleytr on 2011-12-09
Good point, but after reading the following thread it may not work, may have to try it when I get back home, right now its just telnet.

After reading this thread, I'm wondering if the reference is locking the drive and that is why I cannot do anything with it.
[http://www.overclockers.com/forums/showthread.php?t=667317]("http://www.overclockers.com/forums/showthread.php?t=667317")

---

### Post by sibleytr on 2011-12-09
Well this is interesting:
(I'm wondering if my /dev/sdc is listed in the /dev/md_d2 somewhere).

sibleytr@sv1:~$ ls -l /dev/md*
[COLOR="blue"]brw-rw---- 1 root disk   9,   0 2011-12-09 14:33 /dev/md0
brw-rw---- 1 root disk   9,   1 2011-12-09 14:33 /dev/md1
brw-rw---- 1 root disk 254, 128 2011-12-09 14:33 /dev/md_d2
lrwxrwxrwx 1 root root        7 2011-12-09 14:33 /dev/md_d2p1 -> md/d2p1
lrwxrwxrwx 1 root root        7 2011-12-09 14:33 /dev/md_d2p2 -> md/d2p2
lrwxrwxrwx 1 root root        7 2011-12-09 14:33 /dev/md_d2p3 -> md/d2p3
lrwxrwxrwx 1 root root        7 2011-12-09 14:33 /dev/md_d2p4 -> md/d2p4[/COLOR]


I have no idea what the /dev/md_d2(*)'s are in reference to:

Did the following:

sibleytr@sv1:~$ sudo mdadm --query /dev/md_d2
[COLOR="Blue"]/dev/md_d2: is an md device which is not active[/COLOR]

sibleytr@sv1:~$ sudo mdadm --stop --scan /dev/md_d2
[COLOR="blue"]mdadm: stopped /dev/md_d2[/COLOR]
sibleytr@sv1:~$ sudo mdadm --remove /dev/md_d2
[COLOR="blue"]mdadm: error opening /dev/md_d2: No such file or directory[/COLOR]


Other than hitting the drive with a Win98 StartUp disk with the fdisk /mbr command, I'm at a lose.

Anyone have any ideas?

---

### Post by darkod on 2011-12-09
And what does

cat /proc/mdstat

say?

---

### Post by sibleytr on 2011-12-10
Shows that the none existent md_d2 is present. As you can se it all comes back to the sdc.


md_d2 : inactive sdc[0](S)
      312571136 blocks
       
md1 : active raid1 sda5[0] sdb5[1]
      7882688 blocks [2/2] [UU]
      
md0 : active raid1 sdb1[1] sda1[0]
      304686016 blocks [2/2] [UU]

---

### Post by darkod on 2011-12-10
It shows it's present but as spare (S).

What if you try to remove it and check what mdstat is saying after?

sudo mdadm --manage /dev/md_d2 --remove /dev/sdc
cat /proc/mdstat

---

### Post by sibleytr on 2011-12-10
...and the result is:

[COLOR=Blue]mdadm: cannot get array info for /dev/md_d2[/COLOR]


It is like there is a reference called "/dev/md_d2" but there is no real content to the array. I'm thinking this drive may have been a previous array experiment, but I keep going back as to why I am unable to eliminate it.

---

### Post by darkod on 2011-12-10
If I'm not mistaken you destroy mdadm data on a HDD with:
sudo mdadm --zero-superblock /dev/sdc

But not sure if there is some reference in mdadm.conf that you will need to remove after that too.

---

### Post by sibleytr on 2011-12-10
From everything I've read, you are correct. The most I've ever done with RAID is 1. I think the issue with the RAID 5 all has to do with a "faulty" drive that just want give it up.

Tried zero block and no other command seem to work on the drive. I'm hoping to find a way to replace it and start over.

Thanks for all you suggestions, if nothing else you definitely double checked all the steps and processes.

---

### Post by docbop on 2011-12-10
Are the drives for your RAID 5 set all the same size, best if they are otherwise it will only use as much as the smallest drive has to offer.   As someone else said you should be able to use GParted or another drive utility to wipe the drives, then you can use the RAID utiltiy to create your RAID set.   

Also with RAID 5 you need to monitor your RAID set.  If a drive dies in RAID 5 and there is no hot spare you only have so much time to replace the bad drive and rebuild the RAID set.  The parity can only keep the RAID set for so long if you keep writing to the drive.

---

### Post by sibleytr on 2011-12-14
Went back and "preped" all 6 of my hard drives using a combination of GParted and Win98SE boot disk for FDISK /MBR. Re-installed the server from scratch. When trying to recreate the RAID5 my cleaning efforts did not resolve the issue. MD2 still failed to create and then it would not "let go" of sdc1.

After much continued research. Apparently this is a known bug. (Sorry did not keep the reference to the bug report - Google md_d125 array error).

If I understand the "BUG" report correctly; if the creation of a new array fails it can leave the array element listed on the first drive (in my case md2 stayed attached to my sdc1). This is most likely to occur if another array is present, (again, in my case array md0 is root and md1 is swap).

The work around is to simply recreate the array, but with a different none sequential number, (instead of arrays md0, md1, [COLOR="red"]md2[/COLOR], create [COLOR="Blue"]**md5**[/COLOR] in place of [COLOR="Red"]md2[/COLOR]

Process:
[COLOR="blue"]mdadm --stop /dev/md2[/COLOR] (reply shows array stopped)
[COLOR="blue"]mdadm --remove /dev/md2[/COLOR] (reply shows array does not exist)
[COLOR="blue"]mdadm --zero-superblock[/COLOR] /dev/sdc through /dev/sdf (reply was ...array not present... or blah, blah, blah
fdisk all the array drives again with new partitions, and the "fd" partition type
[COLOR="blue"]sudo mdadm --create --verbose --auto=yes **/dev/md5** --level=5 --raid-devices=4 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1[/COLOR]

Then sit back and watch the magic:
[COLOR="blue"]sudo watch cat /proc/mdstat[/COLOR]

Hu-ra!

At this point what I would really like to know is, if I had created the array using [COLOR="blue"]md5[/COLOR] as opposed to [COLOR="Red"]md2[/COLOR] would this have been an issue at all. Oh well, will have to wait until the next server build to find out.


Help Array Links:
Installing Raid 1 on Existing Ubuntu Server
[http://ascend4.org/Installing_Raid_1_on_Existing_Ubuntu_Server]("http://ascend4.org/Installing_Raid_1_on_Existing_Ubuntu_Server")

Mdadm Cheat Sheet
[http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/]("http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/")

---

### Post by sibleytr on 2011-12-15
Ok - either everything went off with out a his or doing the none sequential raid numbering worked.

Had an additional file server to build. The drive mix (SATA w/ IDE) was different but the design configuration (/ Root RAID1 md0 and swap RAID1 md1) was the same.

Used md5 as my next /DEV/MD# for the RAID5 array. Installation worked like a charm with now hiccups.

---

