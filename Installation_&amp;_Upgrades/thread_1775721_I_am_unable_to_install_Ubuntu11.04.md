---
title: "I am unable to install Ubuntu11.04"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by MGTHEBOSS on 2011-06-05
I have 57339MB free space. I tried to install Ubuntu11.04 with following partitions:
Size                 Use as          Mount point
100MB             Ext2             /boot
2000MB           Swap area
10000MB          Ext4             /
45239MB          Ext4             /home


Upto the Swap area everything runs fine.Then I get this error(See attachment please).
How can I install Ubuntu11.04 perfectly?
Please help me.I want to practice programming(C and C++) and I like Ubuntu to use for programming.
Please give reply as soon as possible.

---

### Post by Quackers on 2011-06-05
I have only seen that error when I have been using a raid setup. Are you using a raid array?
On a normal, everyday system there is not usually a need for a separate boot partition.

---

### Post by MGTHEBOSS on 2011-06-05
> **Quackers said:**
> I have only seen that error when I have been using a raid setup. Are you using a raid array?
On a normal, everyday system there is not usually a need for a separate boot partition.
I don't know what RAID is.Can you please explain that in simple words.
How can I check if I have a RAID set up?
I have a 250 GB HDD.
I am making this reply by going to the  "Try Ubuntu" option.
Another thing , in a normal machine ,which doesn't have a RAID Set up, can you give me the step-by-step
procedure to install Ubuntu11.04?You know about available free space from my previous post.
Please answer these 3  questions.
Thanks for your reply.
Addition:
A couple of minutes ago I tried to install Ubuntu11.04 and this time it said "Conflicting installation files".
I want to mention here that I had Windows7 before which I deleted during the installation of Ubuntu11.04.

---

### Post by Quackers on 2011-06-05
If you only have one HDD installed you will not be using raid.
From the live cd desktop please open up gparted and post a screenshot of its screen.

---

### Post by MGTHEBOSS on 2011-06-06
> **Quackers said:**
> If you only have one HDD installed you will not be using raid.
From the live cd desktop please open up gparted and post a screenshot of its screen.
Thanks for your reply.
Here is the screenshot(See attachment please).

I don't want to  lose any data on Downloads1,Downloads2,Downloads3.

Please help me to install Ubuntu11.04.

---

### Post by Quackers on 2011-06-06
Where are you trying to install Ubuntu to? Sda1 or sda10?
The file systems on sda1, sda5 and sda10 are showing as having a problem.
In gparted try right-clicking on each one and select "check" then see if any errors show up.

---

### Post by MGTHEBOSS on 2011-06-06
> **Quackers said:**
> Where are you trying to install Ubuntu to? Sda1 or sda10?
The file systems on sda1, sda5 and sda10 are showing as having a problem.
In g parted try right-clicking on each one and select "check" then see if any errors show up.
Gparted is failing to check.
I have tried to install XP a few minutes before but i am unable to format the unpartioned space to ntfs
Gparted is also failing to format unallocated space to ntfs.
So problem has got a lot more complicated now.
I can't format the unpartitioned space to ext4.
I can't format the unpartitioned space to ntfs.
I can't install Ubuntu.
I can't install XP or 7.
How can I make everything normal?

---

### Post by Quackers on 2011-06-06
What unpartitioned space? The 10.34MB at the end?

---

### Post by MGTHEBOSS on 2011-06-06
> **Quackers said:**
> What unpartitioned space? The 10.34MB at the end?

I deleted some unnecessary partitions and this is the situation now(See the screenshot please).

I am talking about the 2nd and 3rd unallocated space.

---

### Post by Quackers on 2011-06-06
The first unallocated space is too small for XP, I would imagine.
The second is inside an extended partition so can only be a logical partition and XP would not be able to boot from a logical partition unless its boot files were in a separate primary partition.
I see no reason why gparted will not format the 3rd unallocated space. But, of course, that depends on what you are asking gparted to do :-)
What error messages are you getting when you try?

---

### Post by MGTHEBOSS on 2011-06-06
> **Quackers said:**
> The first unallocated space is too small for XP, I would imagine.
The second is inside an extended partition so can only be a logical partition and XP would not be able to boot from a logical partition unless its boot files were in a separate primary partition.
I see no reason why gparted will not format the 3rd unallocated space. But, of course, that depends on what you are asking gparted to do :-)
What error messages are you getting when you try?

I tried to format the 3rd unallocated space to ntfs file system 
It fails with an error (see screenshot please).
Here are the saved details:
_______________________________________________________________________________________
GParted 0.7.0 --enable-libparted-dmraid
 Libparted 2.3
    **Create Primary Partition #1 (ntfs, 42.13 GiB) on /dev/sda**  00:03:07    ( ERROR )             create empty partition  00:00:01    ( SUCCESS )             [I]path: /dev/sda1
start: 400035840
end: 488396799
size: 88360960 (42.13 GiB)[/I]          set partition type on /dev/sda1  00:00:01    ( SUCCESS )             *new partition type: ntfs*          create new ntfs file system  00:03:05    ( ERROR )             ***mkntfs -Q -v -L "Primary" /dev/sda1***             [I]Cluster size has been automatically set to 4096 bytes.
Creating NTFS volume structures.
Creating root directory (mft record 5)
Creating $MFT (mft record 0)
Creating $MFTMirr (mft record 1)
Creating $LogFile (mft record 2)
Creating $AttrDef (mft record 4)
Creating $Bitmap (mft record 6)
Creating $Boot (mft record 7)
Creating backup boot sector.
Creating $Volume (mft record 3)
Creating $BadClus (mft record 8)
Creating $Secure (mft record 9)
Creating $UpCase (mft record 0xa)
Creating $Extend (mft record 11)
Creating system file (mft record 0xc)
Creating system file (mft record 0xd)
Creating system file (mft record 0xe)
Creating system file (mft record 0xf)
Creating $Quota (mft record 24)
Creating $ObjId (mft record 25)
Creating $Reparse (mft record 26)
Syncing root directory index record.
Syncing $Bitmap.
Syncing $MFT.
Updating $MFTMirr.
Syncing device.
[/I]       *Syncing device. FAILED*             ========================================
____________________________________________________________________________________
But the weird thing is now I have returned to the main G parted window and it is not showing any
problem symbol(that red symbol)(See the 2nd attachment please).
Will I try to install Windows 7 on it?

---

### Post by Quackers on 2011-06-06
I see sda1 has been created at the end of the disc - in the old 3rd unallocated space.
There is still some kind of error with sda5
The failure to create a partition in the second unallocated space has occurred, I suspect, because you tried to create a primary partition inside an extended partition. This is not allowed.
Try creating a NTFS partition of type LOGICAL and it should be ok. It will probably be named sda6.

---

### Post by MGTHEBOSS on 2011-07-16
I am going to close this thread.
Reason behind the problem:
I swapped the cables for DVD drive and HDD for some experimental purposes.
Solution:
I swapped the cables again.
Current situation:
I am using Windows 7 Professional and Ubuntu11.04 Dual-boot
 system.
Reason behind delayed reply:
I was busy in my study.
Thanks to :
Quackers

---

