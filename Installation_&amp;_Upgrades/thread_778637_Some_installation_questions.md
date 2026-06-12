---
title: "Some installation questions"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by gdelta9 on 2008-05-02
Hello everyone,recently i decided to leave opensuse and try (k)ubuntu 8.04 Hardy.On opensuse instalation many things were completely automated,so i have some questions.

The main problem seems to be that kubuntu does not see one of my HD's.The way i have partitioned my system is.

**80GB HD**:
1.60GB  for win xp(ntfs)
2.5.5GB for root parition(ext3,primary)
3.14 GB for home parition(ext3,primary)
4.0.5GB for swap (primary)

**200GB HD**
1.180 GB(ntfs)
2.20GB   (fat32)

300GB HD usb

My problem here is that

On the live cd kubuntu will not see the 60GB win xp partition at all.But all the other partitions are visible.
My other issue is that there not seem to be a boot loader worikng after instalation,or there is no bott loader installed,cause after i finish instalation and make the initial boot system boots directly to windows,like a boot loader does not exist.

I think i have made something wrong with partitions or during instalation.
The only steps i might do wrong is the the steps with paritioning.
At this step i choose manual paritioning and i partition my HDD as stated above.I set mount points for ntfs partions(/windows/c , /windows/d....etc and check the option "use--as ntfs and fat32" for these paritions and i only set the option format for the ext3 partitions.
Also at the next screen at advanced options the box install boot loader is checked and the device for the boot loader to be installed is (hd0) should that be a different device?

To sum up my main problems is that the partition or HD that win xp partition is,is not visible and i have no boot loader working.

Long  and not well written post,i know, really sorry for that.If u need any different infos from the one's above plz let me know.

Thnx a lot in advance

---

### Post by Pumalite on 2008-05-02
Post:
sudo fdisk -l
And a screenshot of Gparted.

---

### Post by gdelta9 on 2008-05-02
Here is the fdisk -l output:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe09ce09c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7634    61320073+   7  HPFS/NTFS
/dev/sda2            7635        7696      498015   82  Linux swap / Solaris
/dev/sda3            7697        8365     5373742+  83  Linux
/dev/sda4            8366        9729    10956330   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04a404a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       22763   182843766    7  HPFS/NTFS
/dev/sdb2           22764       24321    12514635    f  W95 Ext'd (LBA)
/dev/sdb5           22764       24321    12514603+   b  W95 FAT32

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0dea4941

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS


Here is a scrennshot of gparted as initially is:
[IMG]http://img379.imageshack.us/img379/9336/snapshot1el5.png[/IMG]


A screenshot of what i make:
[IMG]http://img389.imageshack.us/img389/3852/snapshot2bx3.png[/IMG]

And a screenshot of the boot loader setup
[IMG]http://img370.imageshack.us/img370/551/snapshot3wj5.png[/IMG]

Notice that on the windows ,root and home partition the use of disk space is 0MB which is wrong.
All the ext3 and swap partitions are created as "primary"

And thanks a lot for your reply

---

### Post by Pumalite on 2008-05-02
You have to work with unmounted drives/partitions. Get Gparted Live CD and prepare your partitions ahead of time, then go Manual and use the partitions already prepared.

---

### Post by XemeX on 2008-05-02
On Kubuntu live CD you will find QtParted to manage all your HDDs and partitions, you can try prepare partitions there.

---

### Post by gdelta9 on 2008-05-02
thnx for your answears.
Ill try both ways.Hope im done in a hour or so....

---

### Post by gdelta9 on 2008-05-02
Nope the 80Gb disk is still not visible at kubuntu live cd and during installation it appears but not with the correct info(still says 0MB in use).
Also from live cd's disk and filesystems section the 80GB HD appears but with no info available for it and cant see its partitions as well.

I tried gparted live cd, which is a great tool btw,
but preparing the partitions with gparted gives errors during installation.If i say installer to use the already made partitions without formating i get the error that conflicting operating systems could not be removed and if i say the installer to use the preformarted partitions and format this time as well again i get the error that it could not format the ext3 partion etc

---

### Post by gdelta9 on 2008-05-02
As i see now,kubuntu will not see the HD that is connected to the last socket of the IDE cable of the motherboard.It can only see the HD that is conected to the middle socket of the IDE bus cable.And in that way only one of my HD's is visible at a time

---

### Post by Pumalite on 2008-05-02
In Gparted live CD, you delete the partition first, then make 'New' partition with format and mount point that you desire. Then boot Ubuntu, go Manual and use the partitions. (you'll have to delete them again, etc)

---

### Post by gdelta9 on 2008-05-02
well as i worte on the above post i cant do anything to taht disk cause its not visble not from kubuntu live cd nor from the installer's gparted.
Kubuntu can see only one of the two HD's connected to the same IDE cable

---

### Post by Pumalite on 2008-05-02
You have to correct how you connect your HDD's.

---

### Post by gdelta9 on 2008-05-03
Yeap,everything is working perfectly now.
THnx a lot for your hint
Just changed the IDE cable with a new one.
THe old IDE cable is till working perfectly under opensuse and winxp but not under kubuntu...
Go figure....

---

### Post by Pumalite on 2008-05-03
We are more sensitive.

---

