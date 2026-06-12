---
title: "[SOLVED] Gparted - moving swap &amp;amp; merging /home"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by ee19921 on 2008-10-06
[FONT="Verdana"]Hi, this is the layout of my laptop HD. 

/dev/sda1 fat16 55MB
sda2 fat32 20GB C:\ (4 GB free space)
sda3(extended)
-sda5 fat32 15GB E:\ (100 MB free space)
-sda6 ext3 20GB / (13 GB free space)
-sda8 swap 1GB
-sda9 ext3 353 MB /home partition (150 MB free space)
-free hidden 8MB

Since the /home partition is too small, I want to either allocate more space to it or merge it into / partition(so that I don't have to worry how much to allocate for / and /home). But I am not sure if I know how to do it.

**For allocating more space to /home
Using the Gparted live CD,  if I simply
- create a partition out of root, 
- copy /home to that new partition 
- move swap to the end
- Expand /home to take up any unsed space(created by previous step)

will it work? I am worried it may not boot as the fstab entries aren't updated to the new /home and swap locations.

**For moving /home dir into / partition?
Will it work, if I 
- copy /home into /
- Delete the /home partition

[/FONT]

TIA!

~Karthik

---

### Post by kosmiciatakuja on 2008-10-06
I'm not a big expert here so please treat my responses with caution, in case it wipes your entire disk :)

First, moving /home to / is relatively simple and what you described should work. But if I were you, I would do think either from the rescue console (when booting, select the alternate menu option) or from a LiveCD (boot the system from some LiveCD, mount both / and /home and then copy. 

Of course later, if everything works after reboot you erase /home and assign the free space to /

About resizing /home: first of all check if your filesystem supports resizing or enlarging. Ext3 supports this, so chances are you are okay. I'm not sure about ReiserFS or Reiser 4, or others, so you have to check if you use something more exotic than ext3. 
If you do, it should be enough to just resize the partition using gparted, probably doing this from the liveCD would be safer. I'm not sure I understood the approach you described, but I think just resizing the partition should be enough.
One thing to notice here is this (this is a bit technical): resizing a partition actually consists of two actions. 1 is resizing the partition on the disk (by editing the partition table) - gparted does this for sure. And step 2 is resizing the _filesystem_ on that partition - now I believe gparted does this, but I'm not 100% sure, this one you should check with man gparted or the online documentation [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php) 

If gparted does resize the filesystem, then it should be okay to just resize /home with gparted from livecd. 

Oh and one more word of caution: don't try to resize the partition or filesystem when it is mounted (to be sure check the output of 'mount' command) - I don't think this is safe. Unmount first (with ' sudo umount /dev/yourpartition'). Oh and the last thing: don't 'sudo umount /' :)

hope this helps, I know it's a bit chaotic...

---

### Post by ee19921 on 2008-10-06
Copying /home sounds simpler than I thought. hopefully, it won't wipe out my HD.  :)

rescue console - in booting list, i only see different versions of ubuntu and windows to select. how do I select rescue console?

Yesterday I increased the size of root by wiping a windows partition. Though I don't understand the difference between resizing partition and filesystem, yesterday's change seems to work. 

And both / and /home are ext3s.

Since I am doing resizing with gparted live cd, I assume I need not worry of mount/unmounts.

> **kosmiciatakuja said:**
> I'm not a big expert here so please treat my responses with caution, in case it wipes your entire disk :)

First, moving /home to / is relatively simple and what you described should work. But if I were you, I would do think either from the rescue console (when booting, select the alternate menu option) or from a LiveCD (boot the system from some LiveCD, mount both / and /home and then copy. 

Of course later, if everything works after reboot you erase /home and assign the free space to /

About resizing /home: first of all check if your filesystem supports resizing or enlarging. Ext3 supports this, so chances are you are okay. I'm not sure about ReiserFS or Reiser 4, or others, so you have to check if you use something more exotic than ext3. 
If you do, it should be enough to just resize the partition using gparted, probably doing this from the liveCD would be safer. I'm not sure I understood the approach you described, but I think just resizing the partition should be enough.
One thing to notice here is this (this is a bit technical): resizing a partition actually consists of two actions. 1 is resizing the partition on the disk (by editing the partition table) - gparted does this for sure. And step 2 is resizing the _filesystem_ on that partition - now I believe gparted does this, but I'm not 100% sure, this one you should check with man gparted or the online documentation [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php) 

If gparted does resize the filesystem, then it should be okay to just resize /home with gparted from livecd. 

Oh and one more word of caution: don't try to resize the partition or filesystem when it is mounted (to be sure check the output of 'mount' command) - I don't think this is safe. Unmount first (with ' sudo umount /dev/yourpartition'). Oh and the last thing: don't 'sudo umount /' :)

hope this helps, I know it's a bit chaotic...

---

### Post by Sef on 2008-10-06
>  Since I am doing resizing with gparted live cd, I assume I need not worry of mount/unmounts.

That is correct.  With the GParted Live CD, the hard drive is unmounted.

---

### Post by caljohnsmith on 2008-10-06
It sounds like you are on the right track, just make sure to update your /etc/fstab and possibly your /boot/grub/menu.lst with whatever changes you make, because your partition's UUIDs will be changed. Once you have everything moved around the way you want, you can find your UUIDs with:
```
sudo blkid
```
Also, if your swap partition's UUID changes, you'll want to update your /etc/initramfs-tools/conf.d/resume file if you want to be able to hibernate/suspend your computer. I would be happy to lead you through all the steps if you want, once you get your partition changes completed; just let me know.

---

### Post by ee19921 on 2008-10-06
OK. I did the following steps, thought might be useful to other newbies.

- first I booted in recovery mode to root console
- unmount /home
- mkdir /home.old
- mount /dev/sda8 /home.old
- cd /home.old
- cp -ax * /home
- 'sudo vim /etc/fstab' and commented the line for mounting /home

Rebooted to check if the user login works. 

Then with Gparted moved SWAP to the end and let the root partition grow. And I am done. 


```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda8       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2       /media/c        vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda5       /media/e        vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda7       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

[http://www.ibm.com/developerworks/linux/library/l-partplan.html](http://www.ibm.com/developerworks/linux/library/l-partplan.html)

---

### Post by ee19921 on 2008-10-06
If we can use the partition names in /etc/fstab, any particular reason to use UUIDs? 

/boot/grub/menu.lst - I didn't make any change, still I was able to boot problem free. What needs to be done here?

swap partition/Hibernate - I would have missed otherwise. Thanks!!!!!!!!

> **caljohnsmith said:**
> It sounds like you are on the right track, just make sure to update your /etc/fstab and possibly your /boot/grub/menu.lst with whatever changes you make, because your partition's UUIDs will be changed. Once you have everything moved around the way you want, you can find your UUIDs with:
```
sudo blkid
```
Also, if your swap partition's UUID changes, you'll want to update your /etc/initramfs-tools/conf.d/resume file if you want to be able to hibernate/suspend your computer. I would be happy to lead you through all the steps if you want, once you get your partition changes completed; just let me know.

---

### Post by caljohnsmith on 2008-10-06
> **ee19921 said:**
> If we can use the partition names in /etc/fstab, any particular reason to use UUIDs? 

/boot/grub/menu.lst - I didn't make any change, still I was able to boot problem free. What needs to be done here?

swap partition/Hibernate - I would have missed otherwise. Thanks!!!!!!!!
Certainly OK to use device names instead of UUIDs, just keep that in mind in case you ever move your HDD, because then its device name might change. 

About the hibernate/suspend changes, first make sure that the swap UUID (from blkid) is correct in the following two files:
```
/etc/initramfs-tools/conf.d/resume
etc/uswsusp.conf
```
You probably won't have that second file, so if you don't, no need to worry about it. If you do change the first "resume" file, then you need to update your initrd images with:
```
sudo update-initramfs -u -k all
```
Then you should be all set. Let me know how it goes. :)

---

### Post by ee19921 on 2008-10-06
Ok. I did the initramfs command also. Hibernate seems to work without a problem. 

Thanks all for your help!!

---

### Post by caljohnsmith on 2008-10-06
That's great news it all seems to be working, and I'm glad I could help out. Cheers and have fun. :)

---

