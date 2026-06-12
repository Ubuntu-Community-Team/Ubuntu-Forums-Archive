---
title: "Partition help"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by drpjkurian on 2010-02-03
Hi Guys
I recently installed Jaunty in my departmental machine which is having 70 GB harddisk and 512 MB RAM. Before installing I partitioned the Hard disk by using Gparted of Live CD into Four compartments namely

**1.** Primary partition of 30 GB of file type ext3

**2.** Extended partition of 39 GB which I divided again into two logical    Partition of 20 GB and 19 GB. Labelled it as D and E 

**3.** 1 GB of swap partition

I installed the Jaunty in primary partition, gave the mount point as /
The problem is I am not able to copy or save file in the extended partition namely D and E

Please help me. Thanks in advance

---

### Post by drpjkurian on 2010-02-03
I tried my level best to convince everyone in dept to switch over to Linux. Well now I do not have enough ground to remain in Linux.There is a strong pressure from other quarters to switch back to Windows. So PLEASE GUIDE ME in this problem

---

### Post by darkod on 2010-02-03
How did you format the extended partition? Linux works with /dev/sda1, /dev/sda2, etc, you should start getting used to it. D and E mean nothing. Please post the result of:
sudo fdisk -l

Also, you are aware that you need to mount any partition you want to read/write from right? Only / and swap are mounted by default usually, any other partition you have created needs to be mounted first.

Do they not show up in Places? Can you open the partitions from there?

---

### Post by 2hot6ft2 on 2010-02-03
> **drpjkurian said:**
> Hi Guys
I recently installed Jaunty in my departmental machine which is having 70 GB harddisk and 512 MB RAM. Before installing I partitioned the Hard disk by using Gparted of Live CD into Four compartments namely

**1.** Primary partition of 30 GB of file type ext3

**2.** Extended partition of 39 GB which I divided again into two logical    Partition of 20 GB and 19 GB. Labelled it as D and E 

**3.** 1 GB of swap partition

I installed the Jaunty in primary partition, gave the mount point as /
The problem is I am not able to copy or save file in the extended partition namely D and E

Please help me. Thanks in advance
Since you let windows assign drive letters they must be formatted to NTFS so a couple things come to mind.

If you labeled them like "For Apps" Or "My Progs" the labels should NOT have spaces in them so you would change those to "For_Apps" Or "My-Progs" basically replacing spaces with either a "_"(underscore) or "-" (a hyphen).
Linux doesn't like spaces in volume labels it translates them into "%20" which will create problems.

If you don't already have ntfs-config install it by opening a terminal and using
```
sudo apt-get install ntfs-config
```
Hit Enter then your password (which wont be displayed) and Enter again.

Then it will be under
System > Administration > NTFS Configuration Tool
**BEFORE using it** be sure to unmount the drives. Just open a folder and they will show up in the left column, if they are already mounted there will be a eject like icon next to them just click on it to unmount them.

Then start the NTFS Configuration Tool
Select the 2 drives by ticking the box next to them.
(I suggest NOT ticking the box by the Windows partition to keep anyone from messing with windows from linux without first entering the password)
Hit Apply
Tick the 2 boxes on the next window to allow Read AND Write permissions.
(the second box will allow Read AND Write permissions for things like flash drives that get plugged into the usb port).
Click OK

All done.

---

### Post by oldfred on 2010-02-03
You should understand mounting and fstab to permanent mount partitions.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager

---

### Post by 2hot6ft2 on 2010-02-03
> **oldfred said:**
> You should understand mounting and fstab to permanent mount partitions.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
PySDM is interesting...;) I like all the options.
I agree understanding fstab is a good thing and I've done it that way too. It's just a tad bit more risky for someone that hasn't done their research first. Plus that's where you go to fix the %20 errors when there are spaces in the volume names. After fixing the volume names that is.

---

### Post by drpjkurian on 2010-02-04
> **darkod said:**
> How did you format the extended partition? Linux works with /dev/sda1, /dev/sda2, etc, you should start getting used to it. D and E mean nothing. Please post the result of:
sudo fdisk -l

Also, you are aware that you need to mount any partition you want to read/write from right? Only / and swap are mounted by default usually, any other partition you have created needs to be mounted first.

Do they not show up in Places? Can you open the partitions from there?

Hi Darkod
The extended partition is in the file format of Ext2

The result of ```
sudo fdisk -l

``` is

```
materia@materia-desktop:~$ sudo fdisk -l
[sudo] password for materia: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf3f3f3f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2977    23912721   83  Linux
/dev/sda2            2978        9729    54235440    5  Extended
/dev/sda5            9551        9729     1437786   82  Linux swap / Solaris
/dev/sda6            2978        6526    28507279+  83  Linux
/dev/sda7            6527        9550    24290248+  83  Linux

Partition table entries are not in disk order
materia@materia-desktop:~$ 

```

I can see the partitions in Places. But when I click it I get the reply as 
```
Cannot mount volume.
Invalid mount option when attempting to mount the volume 'E'.
```

Thanks in Advance

---

### Post by drpjkurian on 2010-02-04
> **2hot6ft2 said:**
> Since you let windows assign drive letters they 



Hi 2hot6ft2
Please note that there is no other OS in the machine except Ubuntu Jaunty
The labels namely D & E were assigned by me.

---

### Post by kimda on 2010-02-04
I would change fstab. Change D and E in another name. Ex. mkdir /partd and /parte . You can test this with mount -t ext3 /dev/sda6  /partd  and issue the mount command to see that its mounted properly. Like said before D and E mean nothing in Linux. I would suggest reading a bit more about how filesystems work in Linux/Unix.

---

### Post by drpjkurian on 2010-02-10
Hi
I solved it by doing the following method
1. I booted from Live CD and launched GParted. 

2. I partioned the Entire HD into two primary partition and one Unallocated space

3.Installed Ubuntu using the "Install in free space"

My problem was solved. I got three partitions and all my partitions got mounted automatically

---

