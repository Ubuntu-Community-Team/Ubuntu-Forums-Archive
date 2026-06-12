---
title: "Quick question about gparted"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by poldie on 2008-10-01
I have an Aspire One, and have successfully installed the superior Ubuntu 8.4.1 in addition to the supplied Linpus.  I would now like to remove the partition Linpus is on, and return the space to the partition Ubuntu is using.  It's a dual boot system, and Linpus is on the partition flagged as `boot`, so I'm thinking that if I simply delete the partition and expand the one Ubuntu is using then the system will no longer boot.  The gparted documentation doesn't really elaborate on this sort of problem.  Does anyone have any idea what I can do about this?

---

### Post by Sef on 2008-10-01
In GParted, you can change the boot to Ubuntu.

---

### Post by poldie on 2008-10-02
> **Sef said:**
> In GParted, you can change the boot to Ubuntu.

Will that move the boot menu stuff to the other partition? I'm worried it lives on the initial partition and it wont boot any more.

---

### Post by unutbu on 2008-10-02
Usually, when Ubuntu is installed second, the Ubuntu installer will overwrite the MBR with its own version of GRUB, and this GRUB will read the /boot/grub/menu.lst that resides in the Ubuntu partition.

Therefore, usually the Ubuntu partition will be the one "controlling" the boot process.
(And in general the last OS you install will control the boot process).

However, if you are concerned that this may not be the case for you, you could do this:
Boot into Linpus. Find the file called menu.lst. The path is probably /boot/grub/menu.lst,
but if not, try to find it with any search tool you like, or type
```

locate menu.lst
```

Now edit the menu.lst. (You'll need to be root.)
Go about 2/3 of the way down until you find a stanza that looks somewhat like this:
```

title		Linpus
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```
The title line is what shows up in the GRUB menu at boot time.
You can change it to whatever you like without disturbing the boot process.
So change the title line to
```

title		Linpus Controls the Boot Process
```

save and exit. Reboot. Get to the GRUB menu. If you see "Linpus Controls the Boot Process" as one of the boot options, then post back and we can give you instructions on copying Linpus's menu.lst to the Ubuntu partition and redirecting GRUB to boot from the Ubuntu partition.

If you don't see "Linpus Controls the Boot Process" in the GRUB menu, it means Ubuntu's menu.lst is already controlling the boot process, and you are free to delete Linpus.

---

### Post by poldie on 2008-10-02
Thanks for the helpful reply!

There is no such file on my linpus partition.  I can't boot into linpus because I've made a mess of it (rather, i can boot into it but am then unable to get up a terminal or run any apps).  I also can't edit files on that partition from within Ubuntu.

What I can do is look for that file, and I can't see it.  The closest I can see is grub.conf, in the boot/grub folder, which contains:


-------
default=0
timeout=0
splashimage=(hd0,0)/boot/grub/splash.xpm.gz
hiddenmenu

title Linpus Linux RCD
	rootnoverify (hd0,0)
	kernel /boot/bzImage ro root=LABEL=linpus vga=0x311 splash=silent loglevel=1 console=tty1 quiet nolapic_timer nolapic_timer
  	initrd /boot/initrd-splash.img

-------

If I look in the same place on my Ubuntu partition, I see the following in menu.1st (this is edited to what I believe to be the relevant, similar part):

-------
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c7dbc1e1-56a1-471d-8e6b-43b025fbc1a9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c7dbc1e1-56a1-471d-8e6b-43b025fbc1a9 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Linpus Linux RCD (on /dev/sda1)
root		(hd0,0)
kernel		/boot/bzImage ro root=LABEL=linpus vga=0x311 splash=silent loglevel=1 console=tty1 quiet nolapic_timer nolapic_timer 
initrd		/boot/initrd-splash.img
savedefault
boot

-------


I'm 99% sure this must be the file responsible for the choices I get at boot time.  I just can't tell from that whether or not I can delete the linpus partition.  You're saying I can, by the sound of things. I'm just worried by the hd0,0 and hd0,4 things.  If that's describing where to go to boot, and I delete a partition and grow the Ubuntu one to use its space, then presumably gparted needs to edit menu.1st to give it its new location, right? 

I've spent a fair bit of time playing with Ubuntu, installing, customizing and patching.  Is there a tool which can backup the partition Ubuntu lives on to another partition, so if I were to make a mess of the OS in the future I could simply restore onto the boot partition?

Thanks again for your time!

---

### Post by unutbu on 2008-10-02
Hi poldie, yes there are many ways to backup a partition. One way is to use 
Partimage: [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page). Here is a tutorial on how to use it: [http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522).

Having good backups is always a great thing -- then you can try new things with a confidence that is otherwise unattainable.

When you delete a partition, the device name (e.g. /dev/sda5) and the GRUB device number (e.g. hd0,4) of the remaining partitions do not change. I have resized partitions and the UUID of those partitions did not change either. 

Before you delete Linpus, however, perhaps boot into Ubuntu, then type
```

gksu gedit /boot/grub/menu.lst
```

Now edit the Ubuntu boot stanza by changing:
```

title Ubuntu 8.04.1, kernel 2.6.24-19-generic

```
to
```

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (Hi!)

```
or something :)

Save, exit, and then reboot. If you see (Hi!), then I think deleting the Linpus partition will not disturb the boot process.

When using GParted, you'll find that deleting a partition is a very quick operation, but resizing can take some time. I have read that resizing the left end point of a partition can take longer than resizing the right end point. How long depends on the size of the partition and the speed of your drive. Whatever you do, do not cancel GParted once it has begun resizing a partition -- doing so can result in a corrupted filesystem, the need to do recovery work, and quite likely some significant data loss.

Realistically though, lots of people resize partitions using GParted without backing up first and have no problems. However, I'd feel more comfortable recommending this knowing you have a backup.

Finally, although I don't think anything will go wrong after you delete the Linpus partition, if anything does, post back here and we should be able to help get you back up and booting.

---

### Post by poldie on 2008-10-03
> **unutbu said:**
> Realistically though, lots of people resize partitions using GParted without backing up first and have no problems. However, I'd feel more comfortable recommending this knowing you have a backup.


I did the checks and confirmed it was the correct menu.lst, and successfully deleted that partition. Sadly, though, I can find no way of reclaiming the space it occupied - attempting a resize only lets me make it smaller.  I think the old partition was ext2 and ubuntu created an ext3 one. I've checked out the documentation but it's not helping.  I'm off to have another google, but I'd appreciate any advice from anyone who knows this.  

Cheers.

---

### Post by unutbu on 2008-10-03
Please post the output of 
```

sudo fdisk -l
```
This will list the partition table, and give us an idea of where the partitions are located on the drive.

One thing that comes to mind which might be the problem is that you can not resize a mounted partition. For example, if you are trying to resize the Ubuntu partition, you can not do this while Ubuntu is running.

If this sounds like your problem, then boot from the LiveCD, and launch GParted from there.

If this isn't the problem, please post the output of "sudo fdisk -l".

---

### Post by poldie on 2008-10-04
> **unutbu said:**
> Please post the output of 
```

sudo fdisk -l
```
This will list the partition table, and give us an idea of where the partitions are located on the drive.

One thing that comes to mind which might be the problem is that you can not resize a mounted partition. For example, if you are trying to resize the Ubuntu partition, you can not do this while Ubuntu is running.

If this sounds like your problem, then boot from the LiveCD, and launch GParted from there.

If this isn't the problem, please post the output of "sudo fdisk -l".

I tried it from the live usb key install I used to install Ubunto in the first place - booted from that and tried with the partitions mounted and unmounted but I didn't seem to get any extra options either way and I couldn't expand the main partition larger than it currently is - I could just make it smaller.

Here's the output (I did the fdisk from my regular boot into Ubuntu with the partitions mounted as usual.

-------------
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5fa38a47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2           14463       14593     1052257+  82  Linux swap / Solaris
/dev/sda3            1986       14462   100221502+   5  Extended
/dev/sda5            1986       14089    97225348+  83  Linux
/dev/sda6           14090       14462     2996091   82  Linux swap / Solaris
-------------

I've unmounted the partition I want to reclaim the space from, so it doesn't appear there. It's about 15 gigs.  From running gparted I can see that sda5&6 are part of sda3 - I guess you can tell that from the start and end values.


Thanks.

---

### Post by unutbu on 2008-10-04
Hm. To enlarge sda5, you must first enlarge sda3, the extended partition that contains sda5. That's a little tricky since you have to click on the thin colored border that encloses both sda5 and sda6.

An easier way to select sda3 is to click on the words in the text area below the graphics. Click on the line that says the Filesystem is "extended".

Then click on the Resize/Move button. Now it should allow you to enlarge the extended partition.

After you enlarge the extended partition (sda3),
you should be able to enlarge the logical partition (sda5).

---

### Post by poldie on 2008-10-04
> **unutbu said:**
> Hm. To enlarge sda5, you must first enlarge sda3, the extended partition that contains sda5. That's a little tricky since you have to click on the thin colored border that encloses both sda5 and sda6.

An easier way to select sda3 is to click on the words in the text area below the graphics. Click on the line that says the Filesystem is "extended".

Then click on the Resize/Move button. Now it should allow you to enlarge the extended partition.

After you enlarge the extended partition (sda3),
you should be able to enlarge the logical partition (sda5).

I've booted from my USB key again, so the hard drive is probably not being used at all (other than that I'm using gparted to look at it).

I can see what you mean about clicking on sd3 (the outer dashed line) or sda5 (the inner one) but only on sda5 does the resize option appear, and I can't exceed its current size.  

Meanwhile, an `unallocated 16.51GiB` is staying on the left of the sda5 in the bar chart (and at the top of the grid of text below), apparently preventing me from using the space. I can click 'new' on it, which then offers me a few options.  "Create as" is limited to `primary partition`, I have a choice of a few file systems, free space preceding/following, and new size.  Perhaps I have to do something with this before I can use its space.  Initially, like I said, it held the Linus OS (back when I only had, I think, one partition - at least, it had whatever the Aspire One came with).  I think it was in ext2 format.

I'm wondering if when I installed Ubuntu it created the extended partition for itself, and now there's no way of using the space left behind from the initial primary partition.

---

### Post by unutbu on 2008-10-04
Hm, poldie, you have me stumped. :confused:
I can't think of any reason why you should not be able to resize the extended partition.

> 
I'm wondering if when I installed Ubuntu it created the extended partition for itself, and now there's no way of using the space left behind from the initial primary partition.

As far as I know this should not stop GParted from resizing the Ubuntu partition.

I'll continue to think about this, but at the moment I'm out of ideas.

Edit: Well, okay, here is something of an idea:

If you have a partimage backup of your sda5 partition, then you can delete the sda5 partition, shrink the sda3 extended partition, and then create a new primary partition in the unallocated space, and then restore sda5 (into the new primary partition) from the partimage backup.

If you choose to take this route, we'll have to reinstall grub ([http://ubuntuforums.org/showpost.php?p=1308395&postcount=1](http://ubuntuforums.org/showpost.php?p=1308395&postcount=1))
and edit your menu.lst so that it uses the correct UUIDs and (hdX,Y)s to boot Ubuntu.

I suggest you play around with GParted some more, since if you can get it to work that will lead to a much simpler solution. 

If you decide to take this alternate route, post that you want to do so and I'll try to write up instructions to make the process as painless as I know how.

---

### Post by poldie on 2008-10-04
> **unutbu said:**
> Hm, poldie, you have me stumped. :confused:
I can't think of any reason why you should not be able to resize the extended partition.



As far as I know this should not stop GParted from resizing the Ubuntu partition.

I'll continue to think about this, but at the moment I'm out of ideas.

Edit: Well, okay, here is something of an idea:

If you have a partimage backup of your sda5 partition, then you can delete the sda5 partition, shrink the sda3 extended partition, and then create a new primary partition in the unallocated space, and then restore sda5 (into the new primary partition) from the partimage backup.

If you choose to take this route, we'll have to reinstall grub ([http://ubuntuforums.org/showpost.php?p=1308395&postcount=1](http://ubuntuforums.org/showpost.php?p=1308395&postcount=1))
and edit your menu.lst so that it uses the correct UUIDs and (hdX,Y)s to boot Ubuntu.

I suggest you play around with GParted some more, since if you can get it to work that will lead to a much simpler solution. 

If you decide to take this alternate route, post that you want to do so and I'll try to write up instructions to make the process as painless as I know how.

Thanks again for the help so far.


I have no backup.  I have no practical way of backing up gigs of data at the moment (no usb hard drive, only a 2gb usb key, and I've not got my Acer talking to my desktop pc on a local network yet - they're both on the same router (Acer = wireless, desktop = wired ethernet) but not on the same (or any) network.  I'm a bit nervous about playing around with gparted too much without a backup.  I think, unless there's some magic wand I can wave which will let me just format the unallocated space and then merge it into the main partition, that perhaps the best option is to wait until the end of the month when Ubuntu 8.10 is out, and then just reformat/repartition the whole drive to be the default Ubuntu design (ie what I have now, less the extra partition).  It's not like I have any data to back up - it's just it's taken me a while to install apps, configure the wifi, audio, compiz etc.

I've attached a screenshot of gparted in case my descriptions previously are inadequate.


[IMG]http://img361.imageshack.us/my.php?image=gp1gr9.jpg[/IMG]


Which isn't showing up for some reason. The url is:

[http://img361.imageshack.us/my.php?image=gp1gr9.jpg](http://img361.imageshack.us/my.php?image=gp1gr9.jpg)

---

### Post by unutbu on 2008-10-04
Hm. Without backups, I think the safest thing to do is not try to resize the Linux partition.

It is safe however to just make a new partition in the unallocated space. You could store data there for example. 

If you have say a lot of music files, you mount the data partition at /data, and move your music files to /data/music. If before you had your music at /home/user/music, you could make a symlink from /home/user/music to /data/music:
```

ln -s /data/music /home/user/music

```
By doing it this way, you can still read and write to files in /home/user/music, even though they are physically stored in /data/music.

Anyway, just a thought...

---

### Post by poldie on 2008-10-08
> **unutbu said:**
> Hm. Without backups, I think the safest thing to do is not try to resize the Linux partition.

It is safe however to just make a new partition in the unallocated space. You could store data there for example. 

If you have say a lot of music files, you mount the data partition at /data, and move your music files to /data/music. If before you had your music at /home/user/music, you could make a symlink from /home/user/music to /data/music:
```

ln -s /data/music /home/user/music

```
By doing it this way, you can still read and write to files in /home/user/music, even though they are physically stored in /data/music.

Anyway, just a thought...



I gave up.  Gparted cannot do what I want.  I've reinstalled Ubuntu from scratch, forming 1 large 120gb partition in the process.  I'm not sure whether there's a bug in gparted or whether there's a limitation on what you can do with linux partitions compared with what you can do on Windows ones (certainly I don't remember similar problems on W2K/XP using Partition Magic).

---

