---
title: "Asus EeePc install questions"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by bcnaat on 2008-11-25
Asus 900 (NOT 901) eeepc, 4g flash 'hard drive', 8g flash drive in card slot, 1g RAM. Currently running variant ubuntu-eee (Hardy).

I currently have Ubuntu-eee installed. Before I totally trash my system trying to figure this out, I wanted to ask here about the best way to go about this...I need it to read the 8g as a part of the ubuntu file system, not just an external storage spot.

What I would love to have the 8g in the card reader slot be a part of the file system, maybe the home files only. Currently when I try to shortcut my xampp/lampp install to a folder on the 8g, it won't let me create the link to the drive or any folders on it. I guess that's because its not part of the file system? These files get large and I want them on the 8g card instead of the internal flash drive.

I just run out of hard drive space quickly (only 4g, not upgradeable). For my massive storage of things, I use an external hard drive (360g) but don't keep it hooked up to the netbook all the time, only when I need those files.

I would also like to be able to dual boot off my Jbook (360g external drive) into windows for flash programming. I'm nervous about trying to dual boot from there. Its got a lot of files on there that I don't want to risk losing if I screw up. I only want to dual boot IF I have the JBook attached to the Asus. 

Is any of this possible without a complete reinstall? Either way, I'm not sure how to accomplish any of this without totally destroying my information.

Thnx in advance to anyone that can advise me *smile*.

---

### Post by brallan on 2008-12-01
are you sure you have a eee 901? Mine came with two drives, a 4G and a 16G drive. can you post the results from these two commands?

```
sudo fdisk -l
```

and

```
mount
```

---

### Post by bcnaat on 2008-12-02
You are right! It is a 900 not the 901. Big difference.

I'll post the two command results in a moment, but I did clear off the 8g card that is in the side slot, formatted it to ext3, and then chmod to me instead of root. So far that's helped with me being to access the drive using lampp and other programs. Not to mention the permissions are now correct when I send my web pages to the site to make them live. 

Here is the first command results:

```
Disk /dev/sda: 7948 MB, 7948206080 bytes
255 heads, 63 sectors/track, 966 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001556e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         966     7759363+  83  Linux

Disk /dev/sdb: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b2643

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         462     3710983+  83  Linux
/dev/sdb2             463         490      224910    5  Extended
/dev/sdb5             463         490      224878+  82  Linux swap / Solaris
```

Here is the mount command results:
```
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)
```

Kay

---

### Post by brallan on 2008-12-08
> **bcnaat said:**
> What I would love to have the 8g in the card reader slot be a part of the file system, maybe the home files only.

here is a guide to do just that:

[http://reiber.org/joomla12/index.php?option=com_content&task=view&id=12&Itemid=30](http://reiber.org/joomla12/index.php?option=com_content&task=view&id=12&Itemid=30)

good luck!

---

### Post by bcnaat on 2008-12-21
I finally got the permission/owner changed on both my card reader and my external drive. I wasn't connecting in my head the difference in permissions and owners. Once I changed the owners, I was good to go on being able to read off any of them.

brallan: I have read through the link that you gave me, and when I can make sure that I've have everything backed up that I need/want and am reading for the swap I will do a clean install that will follow the guide. Makes more sense to use the 8g as a /home than anything. 

I love my Asus and its portability, however, I am not use to running out space so quickly that I can't even download my emails.

Thanks to you two for replying and I will post the results whether they be good or bad.

Thanks again!

Kay

---

### Post by bcnaat on 2009-01-01
Totally messed that up somehow. Not sure. It simply would not boot up. 

I may have done something right on the next format/install because after installing eee on the internal flash, I then made the extra 8g card (through gparted) ext3.  

This is what my 'sudo fdisk -l' reads:
```

Disk /dev/sda: 7948 MB, 7948206080 bytes
245 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 15190 * 512 = 7777280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b2643

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         462     3710983+  83  Linux
/dev/sdb2             463         490      224910    5  Extended
/dev/sdb5             463         490      224878+  82  Linux swap / Solaris
```

sda (my 8g that I added) doesn't have a valid partition table? It all works just like another drive again. I have permissions, can read/write, access whatever is there without a hitch. Although it uses the drive, why would it say that it doesn't contain a valid partition table and is that going to cause problems later? So far everything seems to be running fine.

---> What would happen if I just installed Hardy, straight up? I know that I'll lose the desktop enhancements for such a small screen and how things appear, but I can make changes to make it 'fit'. Is Hardy full version just too much for an Asus to handle?

---

