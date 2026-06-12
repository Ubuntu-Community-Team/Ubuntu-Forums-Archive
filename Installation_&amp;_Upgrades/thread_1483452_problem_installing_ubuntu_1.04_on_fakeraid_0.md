---
title: "problem installing ubuntu 1.04 on fakeraid 0"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by nevelast on 2010-05-14
Ubuntu does't recognise my fakeraid 0 array. (fedora has no problem seeing my fakeraid partitios)

ubuntu@ubuntu:~$ sudo dmraid -ay
ERROR: jmicron: wrong # of devices in RAID set "jmicron_xb              " [1/2] on /dev/sdb
ERROR: removing inconsistent RAID set "jmicron_xb              "
ERROR: no RAID set found
no raid sets

ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sdb: jmicron, "jmicron_xb              ", stripe, ok, 625082368 sectors, data@ 0

Help!

---

### Post by nevelast on 2010-05-15
bump

---

### Post by samg34 on 2010-05-15
have you tried using the GUI tools for partitioning?
(on liveCD) try System>Administration>GParted
these were the tools i used to get my partitions3

I don't think ubuntu supports fake raid [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by nevelast on 2010-05-15
Gparted doesn't work, it shows me 2 unformatted harddrives.

---

### Post by darkod on 2010-05-15
It might be that it's not recognizing your controller unfortunately.
But on another note, you are supposed to use the Alternate Install CD (image) for RAID. Have you tried with it?

---

### Post by ronparent on 2010-05-15
My experience has been that gparted will not show your raid in 10.04. What does dmraid -ay show in fedora?

---

### Post by nevelast on 2010-05-16
^
fedora 13 beta x86_64:
[root@none q]# dmraid -ay
ERROR: ddf1: seeking device "/dev/dm-4" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-4" to 4608
ERROR: hpt45x: seeking device "/dev/dm-4" to 18446744073709547008
ERROR: pdc: seeking device "/dev/dm-4" to 137438913024
ERROR: pdc: seeking device "/dev/dm-4" to 137438920192
ERROR: pdc: seeking device "/dev/dm-4" to 137438927360
ERROR: pdc: seeking device "/dev/dm-4" to 137438934528
ERROR: sil: seeking device "/dev/dm-4" to 18446744073709289984
RAID set "jmicron_xb" already active
RAID set "jmicron_xb" was not activated
RAID set "jmicron_xbp1" already active
RAID set "jmicron_xbp1" was not activated
RAID set "jmicron_xbp2" already active
RAID set "jmicron_xbp2" was not activated
RAID set "jmicron_xbp3" already active
RAID set "jmicron_xbp3" was not activated
RAID set "jmicron_xbp5" already active
RAID set "jmicron_xbp5" was not activated
RAID set "jmicron_xbp6" already active
RAID set "jmicron_xbp6" was not activated
RAID set "jmicron_xbp7" already active
RAID set "jmicron_xbp7" was not activated


ps: i have a ga-965p-s3 rev 1 motherboard, 2xST3320620AS hdd





> **darkod said:**
> It might be that it's not recognizing your controller unfortunately.
But on another note, you are supposed to use the Alternate Install CD (image) for RAID. Have you tried with it?
it's on the "to do" list

---

### Post by ronparent on 2010-05-16
Although it doesn't seem likely, there appears to be a possibility that fakeraid is implemented differently in the two distributions??? Dmraid in Ubuntu seems to be picking up only the raid on sdb. What does **dmraid -r** give you in Fedora? Unless you can identify both disks within the Ubuntu live cd, it probably would not be wise to attempt an installation without complete data backup. As things stand formatting and data would be lost on the entire array, if it still exists.

---

### Post by nevelast on 2010-05-16
fedora 13:
[root@none q]# dmraid -r
ERROR: ddf1: seeking device "/dev/dm-4" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-4" to 4608
ERROR: hpt45x: seeking device "/dev/dm-4" to 18446744073709547008
ERROR: pdc: seeking device "/dev/dm-4" to 137438913024
ERROR: pdc: seeking device "/dev/dm-4" to 137438920192
ERROR: pdc: seeking device "/dev/dm-4" to 137438927360
ERROR: pdc: seeking device "/dev/dm-4" to 137438934528
ERROR: sil: seeking device "/dev/dm-4" to 18446744073709289984
/dev/sdb: jmicron, "jmicron_xb", stripe, ok, 625140224 sectors, data@ 0
/dev/sda: jmicron, "jmicron_xb", stripe, ok, 625140224 sectors, data@ 0

weird is the fact that ubuntu kills my fakeraid, but a cold reboot solves the problem

ps: this is the correct ubuntu error (including the spaces after jmicron_xb)
ubuntu@ubuntu:~$ sudo dmraid -ay
ERROR: jmicron: wrong # of devices in RAID set "jmicron_xb               &#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;"  [1/2] on /dev/sdb
ERROR: removing inconsistent RAID set "jmicron_xb              &#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; "
ERROR: no RAID set found
no raid sets

& there's noting in /dev/mapper except a file called "control"

---

### Post by ronparent on 2010-05-16
Apparently in Fedora the raid set on sda and sdb are found and are ok. Completely different from what you are finding in ubuntu. This definitely suggests that dmraid in ubuntu interprets Fedora created meta data differently than Ubuntu. Could the dmraid versions possibly be different between the two distributions?

Regardless,with this situation it doesn't appear that the two distributions could co-exist using the same raid sets!! That doesn't sound at all possible since dmraid should be designed function identically in all linux environments. Unless we can get to the bottom of this, if you want to install Ubuntu you would have to backup all your data and basically destroy all of your partition tables to reconstitute them under Ubuntu. This could work but may not be advisable at this point. I'm not familiar enough with Fedora to give any sensibly advise on this.

---

### Post by bitlisz on 2010-05-17
I think I have similar problem. I just upgraded from 9.10 to 10.04 (what a mistake).
Then the pc was not bootable anymore (different story...i tried many thing, I would not recommend to anyone the upgrade!)
Then fresh install Ubuntu 10.04. Better...but one of my software RAID1 not accessible anymore (mdadm says ok, but I cannot mount if i not reformat before...and this was not init).
And then very strange thing came up: at every boot I see different device path for the partitions, sometimes /dev/sda also used for one RAID mirror component (originally the raids: sdd+sde, sdf+sdg) which is where i installed the os (?).
Now i get nowhere, maybe i will remove the 2 drives and get the data back on windows (!)...couse i dont made any backup from these drives before this upgrade-nightmare (seriously who has 1-2TB free space in the drawer just for backup their raid?).

So think twice before upgrade to 10.04 if you have sw raid1!

---

### Post by mikebailey on 2010-11-30
i think i may have found a solution to your "ERROR: pdc: wrong # of devices in RAID set" issue.

short story, if the only drive in your computer is the raid array, windows creates a 100 mb partiton for the boot files and MBR. like grub 1, the windows MBR will not function on a raid array, so it created the 100 MB partition on only one of the drives, so that 100 mb partition messes up the partition boundaries on one of the drives in the array so they don't match, causing the "ERROR: pdc: wrong # of devices in RAID set" issue.

long story, if you wish to read it.

i too was plagued by that issue. i decided to try and find out the problem to it. after many hours of backing up my windows 7 install on my raid array, i decided to take the plunge and start from scratch. 

i noticed in ubuntu 10.10 that i had installed to one of the ide drives on my computer, that when i looked at the 2 drives in the fakeraid raid 0 array on my computer (amd sb750 chip) as separate drives with "fdisk -l", one drive had an extra partition that the other did not. i looked at its size and noticed it was only about 100 MB in size.

when the only drive in your computer is the raid array drive, and you install windows 7 to the raid array with no other drives in the computer, windows creates that 100 mb partition to store the boot data on (i think thats what they put on it). when i created the raid array in the bios i then went in the windows install far enough to create the partitions, i have 2 other ide hard drive in my computer, a 200 GB and an 80 GB. when i created the partitions, it used my 200 GB ide drive to put the mbr and the other windows boot stuff on it, instead of creating the 100 mb partition on the raid array. linux now sees the raid array properly, and i am going to be putting ubuntu 10.10 on it later, using my 80 GB ide drive grub.

i hope this solves a few peoples issues with the "ERROR: pdc: wrong # of devices in RAID set"

---

