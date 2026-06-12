---
title: "cant find etc/fstab"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by flsantos on 2007-01-23
I just migrated do Ubuntu 6.10 from xp.
Have two HD one with 8Gb and other with 120Gb. In Win the 8Gb I had the sistem and the other HD my arquive and files.
Boot the livecd and instaled ubuntu on the 8Gb. Now I can´t find the other disk.
Did a search in the forum and find a threath that include editing my etc/fstab, but i can´t find it.
Theres any solution to mount the other disk without erasing all the files or formating the disk. It´s 75% full.
Thanks in advance, and sorry for my lousy english.

---

### Post by bernied on 2007-01-23
EDIT - *** Please ignore all this - I did not understand your question ***

Try using the commands (from the live-cd):
```
mount
```
to tell you what is already mounted
and
```
sudo fdisk -l
```
(you may not need the 'sudo')
to tell you what disks you have access to.
If you cant find the disk already mounted, then you can mount it by creating a mount point:
```
sudo mkdir /tempmount
```
then mounting it
```
sudo mount -t ext3 /dev/xxxx /tempmount
```
Note that:
1 - xxxx is the partition that you want to mount - it will be one of those in the fdisk output (above)
2 - ext3 is the default filesystem for ubuntu (as I recall) but may not necessarily be the right one, if you have used a different filesystem
Then you can access the file like so:
```
sudo nano /tempmount/etc/fstab
```

---

### Post by randiroo76073 on 2007-01-23
Open file manager, click Edit/Preferences, on View tab make sure "Show hidden and backup files" is checked

---

### Post by bernied on 2007-01-23
My apologies for my previous post - I misunderstood.

/etc/fstab is not normally accessible to the ordinary user, and like randiroo says you need to allow hidden files to be seen to even find it in the file manager.

But, even doing this won't allow you to edit it. To edit it, open a terminal (in the system menu), and type:
```
sudo nano /etc/fstab
```
you will be asked for your password - this is to be sure you have the right to administrative access.

---

### Post by flsantos on 2007-01-23
Thanks, fount it (it´s so simple, I´m a noob!)
And if I mount the other disk it will erase all of my files?

---

### Post by Canis familiaris on 2007-01-23
It is not etc/fstab, it's /etc/fstab --don't omit the slash before etc
If the drive you want to access is ntfs, then follow the thread below:
[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3gtp://]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3gtp://")

If the drive you want to shared is fat32 then:
(1) Open the terminal and make a folder:
sudo mkdir /mnt/shared
(2) Now find the device name of the drive, by passing the command:
```
sudo fdisk -l

```
[HTML]You will receive an output like this:
/dev/hda1   *           1         459     3686886    7  HPFS/NTFS
/dev/hda2             460         752     2353522+   7  HPFS/NTFS
/dev/hda3             753        1262     4096575    c  W95 FAT32 (LBA)
/dev/hda4            1263        7445    49664947+   f  W95 Ext'd (LBA)
/dev/hda5            1263        1326      514048+  82  Linux swap / Solaris
/dev/hda6            1327        4003    21502971   83  Linux
/dev/hda7            4004        6043    16386268+  83  Linux
/dev/hda8            6044        7445    11261533+  83  Linux
[/HTML]
(3)You should be now able to know the device name, in my case was that W95 FAT32 partition, so I select /dev/hda3*
* This may be differ in your computer, it could be /dev/hdb8. (Make sure you don't mount the extended partition.)
(4) Now open fstab by command:
```
sudo nano /etc/fstab

```
(5) Scroll to the last line and add the following line
```
/dev/hda3	/mnt/shared	vfat	noauto, user	0 0
```
Replace /dev/hda3 according to output below.
Save the file by Crtl+O and then exit by Crtl+X
(6) You can now share your drive. Just mount the drive in terminal every time before accessing it in /mnt/shared
sudo mount /dev/hda3 /
(7) You may not like to mount the partition every time before you use it, in that case use this line instead of the line in fstab I gave before:
```
/dev/hda3 /mnt/shared  vfat    uid=anurag,gid=anurag 0 0

```
Just replace anurag by your user name and Save by Crtl + O and Exit by Crtl + X (Make sure you remove the previous entry)
(8) Now you can access your drive.

---

### Post by flsantos on 2007-01-23
Thanks. The drive is ntfs. But the question maintains. It will erase the disk?

---

### Post by bernied on 2007-01-23
Mounting the disk will not erase it - mounting will not write to the disk at all, as far as I know.
You can be extra careful by mounting with the ro (read-only) option.
Just add ',ro' (without the quotes) to the end of the list of options in the appropriate line in fstab (the options are just before the two numbers '0 0').

---

### Post by flsantos on 2007-01-23
Thanks.

---

