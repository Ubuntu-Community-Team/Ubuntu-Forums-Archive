---
title: "How to mount Documents AND Desktop to the same (currently un-mounted) HD?"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by Raavea on 2006-08-09
> **hopstah said:**
> i'm not quite sure what you mean, but if you want to read / write to your hard drive, you need to mount it.

you do this by creating a folder where you want the drive to be - for me, my music hard drive is mounted at /media/music/

next, you need to tell the computer that you want to mount the drive.  for me, this is done by ```
sudo mount /dev/hdd1 /media/music
```

obviously you need to change 'hdd1' to your hard drive and partition.

to get it to automatically mount at boot, you need to add a line to your /etc/fstab file.  search the forums for details on doing that as well as the proper syntax of that file.

i hope this helps a bit!
 I saw this, and I can see how it works. Seems simple. However, I want to put **both** my Documents and Desktop folders onto the same HD - my other HD. The other HD is formatted, but I dunnoh how to mount two folders to it at once, so it's not mounted at all yet.

 Is this possible? I don't want to try, and risk killing old Bernard here, so I thought I'd ask the general Ubur populace. :lol:

---

### Post by Raavea on 2006-08-10
Well... Since no help has been forthcoming, I'm going to mount documents up. I'll leave Desktop, and just try to remember not to clutter it. :)


Augh, it seems to be harder than I thought... -_-

---

### Post by Raavea on 2006-08-10
Ha-ha! I knew something was missing. I needed gparted.

 I then partitioned my second drive (with a teeny swap) by copying the format of the Ubuntu HD. ^___^

 ...Now to figure out this fstab thing. xD

> **rekahsoft said:**
> You fstab should look like this:
```
# /etc/fstab: static file system information.
# 
# <file system> <mount point>   <type>  <options>               <dump>  <pass>
proc            /proc           proc    defaults                   0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw                         0       0
/dev/hdb5       /mnt/one        ext3    defaults                   0       1
/dev/hdb6       /mnt/two        ext3    defaults                   0       1
/dev/hdb7       /mnt/three      ext3    defaults                   0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto            0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto            0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto             0       0
#Added by diskmounter utility
/dev/hdb1 /media/hdb1 ntfs ro,user,fmask=0111,dmask=0000           0       0
```
 ... 

 Looking at the above quote, I guess I should make my /etc/fstab look like this (my own fstab with my additions marked);
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# the next two are my additions
/dev/hda1       /home/raavea/everything   ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
```
 Would that be correct? The hda5 bit is a tiny swap I added (50mb) as I wasn't sure if it would help with data transfer, but felt it wouldn't hurt to try.

 Eyy.. Testing it anyhow.



 Okay, cannot write to it. Think I saw something lying around about setting the permissions...
 -_- No wonder this is such a popular topic. Everyone says things like 'you need to search the forums and/or wiki for /etc/fstab' well... Done that. Nothing telling me how to fix this yet. :X

 Gah. Everything I find is useless. It's all for bloody NTFS partitions. -_- How on earth... Hmm.. Mebbe I can CHMOD it or something, like I do with certain website folders... CHMOD to 700, no luck. It worked, but I still can't access the damn thing, because I'm 'not the owner'.


 Finally. (I really have no idea why I'm updating this thread with my progress. I guess at some point someone else might be as confused as I, and find it..)

 Eventually I found [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions) and using gksudo nautilus and SEARCHING for everything (the folder I tried to mount) I managed to find it and set the permissions to be;```

x x x
x o x
x o x
```
 And changed the owner and group to raavea.

 All sorted! Bah-bye.

---

