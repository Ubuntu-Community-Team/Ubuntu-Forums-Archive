---
title: "partitioning problems"
date: 2005-03-26
forum: Installation &amp; Upgrades
---

### Post by ubuntu_demon on 2005-03-26
I didn't know where to post this thread.

I want to shrink my hda1 ntfs partition and use the new free space to enlarge my hda6 root ext3 partition.

This is the relevant section of my /etc/fstab :

/dev/hda6       /               ext3    defaults,errors=remount-ro  0       1
/dev/hda7       none            swap    sw               0       0
/dev/hda1       /mnt/windows    ntfs    umask=0222      0       0

problems :

1) I can't use partition magic because it keeps giving error 117.

2) I can't use gparted because I can't seem to move the new unallocated free space into the extended partition.

So I have to

Figure out a way to remove error 117. (not much luck with it) I already did a search on the forums here and also on google. I don't have diskdrive and 
"sfdisk -d /dev/hda | sfdisk --no-reread -H255 /dev/hda --force" I found on linuxquestions doesn't help (it creates a couple of dialog boxes "...do you want to fix this". After those dialog boxes error 117 still pops up.

Or run gparted or some other tool from ubuntu livecd. But then I have to know how to move unallocated free space into the extended partition.

Anyone ?

---

### Post by Xian on 2005-03-27
[QUOTE=demon666_nl]I can't use gparted because I can't seem to move the new unallocated free space into the extended partition.[/QUOTE]
My advise would be to not try and change the size of that existing Linux partition. I've seen far to many such attempts fail and then the only option is to reinstall your system. I would instead use those unallocated GB's to create a new partition for one or more of your subdirectories (/home, /usr, /opt and so forth), and thereby increase the total size without having to chance a more risky maneuver.

---

### Post by emperor on 2005-03-28
I would recommend running chkdsk on your ntfs drive, from windows.

The best way is to force win2000 or XP to run check disk and fix any errors on bootup. You'll need to go the the C: drive folder and select this!

[http://pcworld.about.com/magazine/2109p160id111653.htm](http://pcworld.about.com/magazine/2109p160id111653.htm)   
 
Running defrag would also be a good idea. 

I have used Partion Magic 8 a number of times to shrink ntfs drives to make room for Linux. I have also encountered errors which are usually correctable. In rare cases, I have had to do a low level format of the drive.

---

