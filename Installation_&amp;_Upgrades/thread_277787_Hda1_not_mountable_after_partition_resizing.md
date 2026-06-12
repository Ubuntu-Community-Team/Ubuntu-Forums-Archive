---
title: "Hda1 not mountable after partition resizing"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by paechan on 2006-10-15
Hello

This is my first post on this forum so bear with me if i sound too new.

I've been using ubuntu for some time now and i think i have grown to like it     . Problem is that i keep messing it up somehow so that i need to reinstall. This is also the case with this.

As many others  i started out with a rather small linux partition. As i grew fond of using it i wanted to try and install wow on it. See if i could get it to work. The first thing i realized was that i needed a bigger partition for that to work out. I boot up windows (i use dualboot with grub), fire up partition magic and there we go. Prior to this i have reinstall windows and gotten grub to work again with the live cd.  
So i resize the windows partition to give ubuntu 10 gb more. Everything works out fine and i can boot both operating systems.

So here i my problem, finally.

Windows is on /dev/hda1 and ubuntu is on /dev/hda5

FOr some reason, ubuntu isnt mounting hda1 anymore. /dev/hdb and /dev/sda both get mounted in media/whatever but when i open /media/hda1 its empty!
This started after the resizing and before that i had full access to this partition.

When i open up gparted i can see that there is some kind of error on the harddisk. It says that it is unable to read the contents and that i should check if i have intalled  the right plugin. 
I think that maybe my fstab is broken or something, but i have no idea how to fix this. Its not life threatening or anything, but after all the work i did to reinstall grub i would really like this installation of ubuntu to work out :D

Hope someone will be able to help me and my unmountable partition

---

### Post by aysiu on 2006-10-15
Can you post the output of these three terminal commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
``` Go ahead and just copy and paste them into the terminal. Don't retype them.

---

### Post by paechan on 2006-10-15
**johannes@johannes-desktop:~$ sudo fdisk -l**
Password:

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       36481   293025600    f  W95 Ext'd (LBA)
/dev/sda5               2       36481   293025568+   7  HPFS/NTFS

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12680   101852068+   7  HPFS/NTFS
/dev/hda2           12681       14593    15366172+   f  W95 Ext'd (LBA)
/dev/hda5           12681       14529    14852061   83  Linux
/dev/hda6           14530       14593      514048+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   82  Linux swap / Solaris
/dev/hdb2              14        9729    78043770    7  HPFS/NTFS
**johannes@johannes-desktop:~$ df -h**
Filesystem            Size Used Avail Use% Mounted on
/dev/hda5              14G  3.3G   11G  24% /
varrun               1014M   76K 1014M   1% /var/run
varlock              1014M  4.0K 1014M   1% /var/lock
procbususb             10M  188K  9.9M   2% /proc/bus/usb
udev                   10M  188K  9.9M   2% /dev
devshm               1014M   16K 1014M   1% /dev/shm
lrm                  1014M   18M  996M   2% /lib/modules/2.6.17-10-386/volatile
/dev/hdb2              75G   75G  390M 100% /media/hdb2
/dev/sda5             280G  276G  4.4G  99% /media/sda5
**johannes@johannes-desktop:~$ cat /etc//fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/hda5 -- converted during upgrade to edgy
UUID=00d1ba35-9490-40c4-87e8-0dfec0e4de0b / ext2 defaults,errors=remount-ro 0 1

# /dev/hda1 -- converted during upgrade to edgy
UUID=5AC8DE36C8DE105D /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

# /dev/hdb2 -- converted during upgrade to edgy
UUID=00A80B0FA80B02C0 /media/hdb2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

# /dev/sda5 -- converted during upgrade to edgy
UUID=641C1D911C1D5F7C /media/sda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

# /dev/hda6 -- converted during upgrade to edgy
UUID=d9d8dc2b-73b7-425b-9e8c-bb9a222bf32e none swap sw 0 0

# /dev/hdb1 -- converted during upgrade to edgy
UUID=f2f3fece-4da1-49a7-b2a5-ad9cbc431ea8 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Thats the output i get from inputing those commands. I see the section with /dev/hda1 in the fstab file, and i found that very weird. Im still learning this, but isnt the fstab file what Ubuntu is supposed to mount?

Tell me if you, or anyone else, need more info. I will probably figure out how to get it after a while :D

---

### Post by aysiu on 2006-10-15
Yeah, it looks good to me, except that clearly /dev/hda1 *isn't* mounted. Try this: ```
sudo mkdir /media/hda1
``` If it says the directory already exists, that's okay. That's what we want--for it to exist! Then: ```
sudo mount -a
``` See if /media/hda1 is still empty.

---

### Post by paechan on 2006-10-16
I tried the command now, but there is something wrong.

johannes@johannes-desktop:~$ sudo mount -a
mount: special device /dev/disk/by-uuid/5AC8DE36C8DE105D does not exist

Did the ID of the disk maybe change when i resized it? Anyway thats the output i got. Looking into it myself now

EDIT

Tried looking into the folder and here is what i found:

johannes@johannes-desktop:~$ dir /dev/disk/by-uuid/
00A80B0FA80B02C0                      641C1D911C1D5F7C
00d1ba35-9490-40c4-87e8-0dfec0e4de0b  d9d8dc2b-73b7-425b-9e8c-bb9a222bf32e
3454225D542221DA                      f2f3fece-4da1-49a7-b2a5-ad9cbc431ea8

---

### Post by Kateikyoushi on 2006-10-16
The UUID changed when you resized the partition.
Change the hda1 partition's line in fstab

Open for editing
```
sudo nano /etc/fstab
```

Then change the line to look like this.

```
/dev/hda1 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
```
Save it with CTRL+X and Yes to write changes to disc.

Then mount it.
```
sudo mount -a
```

Now check again the /media/hda1

---

### Post by paechan on 2006-10-16
SO the command you told me to run showed me that fstab was referring to an outdated name of hda1. I looked up that folder and went through the files untill i found the one pointing at hda1. I then copied the name of that file into fstab instead of the outdated one and voila! It works now. xD 


Im so new to this so it feels really good when you get something to work, even with extensive help from the forums. At least i learned something from it.

Again thx for the time and the help.

EDIT

Seems like we typed at the same time, anyway as you can see i got it to work, but thx for the alternative solution as well.

---

