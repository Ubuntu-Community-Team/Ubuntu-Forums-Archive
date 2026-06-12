---
title: "removing windows"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by mardawi on 2007-04-10
hi guys,

i have a dual boot (ubuntu and xp) system
how can i remove xp? should i just reformat the ntfs partition to ext3?
wouldn't that cause any problems to GRUB?

i have one hd, with one primary partition (the ntfs), all the ext3 and swap partitions are logical. GParted used to cause problems. when i installed ubuntu, i had to create the partitions with PartitionMagic from windows.

how should i mount the new partition? i already have a /home partition.

thnx a lot.

---

### Post by zenwhen on 2007-04-10
This is easy since you only have one drive. Back up everything important in case something goes wrong.

What you will want to do is run...

```
sudo gedit /boot/grub/menu.lst
```

Edit out the reference to Windows in there. 

Then run....

```
sudo fdisk -l
```

This will tell you the partition name of the ntfs partitiion.

Then run...

```
sudo mkfs.ext3 /dev/hda#
```

(# = right partition number for your old windows partition)

Will probably be hda1, but you have confirmed what name you should use with fdisk -l already right?

Now create a mount point for your new partition.

```
 sudo mkdir /mnt/storage
```

Now you will need to add a reference to your new ext3 drive in fstab. 

Run this....

```
sudo gedit /etc/fstab
```

Add this line.....

```
/dev/hda#       /mnt/storage      ext3     defaults        0         2
```

(# = the partition number you found out in fdisk -l))

After a reboot, you should now have a nice storage partition.

---

### Post by mardawi on 2007-04-10
thanks a lot zenwhen, it worked as a charm!
:guitar:

---

### Post by delilahjed44 on 2007-04-10
[COLOR="DarkRed"]What if I wanted to remove the Ubuntu and re-install the windows, then what code and or path would be done? 

Thanks Sherri[/COLOR]

---

### Post by zenwhen on 2007-04-10
> **delilahjed44 said:**
> [COLOR="DarkRed"]What if I wanted to remove the Ubuntu and re-install the windows, then what code and or path would be done? 

Thanks Sherri[/COLOR]

1) Back up your data.

2) Insert windows disk.

3) Delete all partitions.

4) Format.

5) Install antivirus software. :)

---

### Post by zenwhen on 2007-04-10
> **mardawi said:**
> thanks a lot zenwhen, it worked as a charm!
:guitar:

You are welcome.

---

### Post by delilahjed44 on 2007-04-11
Hey, I guess I then need to do this in the bios then correct? because it does not boot on its own.  I though you had to get partition manager for this, erase partitions, then re-create one for windows to see, then put your cd in.  What you are saying souds pie rather to the latter expressed, which is right? do you boot from bios and go in and do as you say? for removal of Ubuntu then re-install windows? 

Sherri
Thanks, on the bottom of the newbie list of course.

---

### Post by delilahjed44 on 2007-04-11
Sorry, adding this, I read somewhere someone did this and they erased what was on the CD,took 30 hours to recover because all the files changes???

Sherri
Thanks, still on the bottom of newbie list.

---

### Post by RichBR549 on 2007-04-15
zenwhen - This is great!
  But in my case I've got two HDD's with XP on the Master, Ubuntu on slave.
hda1 = xp (master)
hdb# = Ubuntu (slave)

What additional info do I need to move completely to Ubuntu on this machine?

---

### Post by confused57 on 2007-04-15
> **RichBR549 said:**
> zenwhen - This is great!
  But in my case I've got two HDD's with XP on the Master, Ubuntu on slave.
hda1 = xp (master)
hdb# = Ubuntu (slave)

What additional info do I need to move completely to Ubuntu on this machine?

The first thing I would suggest is to download & burn a copy of the gparted live cd:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

Grub is probably installed to the mbr of hda, which you can leave it as it is and just repartition your Window's drive...this shouldn't affect your hda mbr.

Before you do this you might want to comment any Window's mountpoints in your /etc/fstab.

Once you repartition your hda, then you can create mountpoints for each partition to use as storage or to install other Linux OS.

You can also install grub to the mbr of hdb, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
doing it this way, you'd need to change your grub root from (hd1,x) to (hd0,x)

This should give you some ideas and I'm sure you'll get plenty of other excellent suggestions...just let us know what you might want to do and someone can give you more specific instructions on how to go about it.

---

### Post by RichBR549 on 2007-04-15
I'd like to boot to the hdb HD(27Gb) and keep apps there, then use the hda HD(160Gb) for storage(mainly photos).  Machine = Dell Dimension 4100 PEntium III 1Ghz, 512Mb.

If I need to keep grub to do this that's ok.  I was thinking I may need to change the HD's physical position on the IDE cable and change ID's, but I'll do whatever works best in the long run.

I'll read up on gparted and grub(only used it once for the dual boot install)  and keep looking for some great advice.
Thanks.

---

### Post by RichBR549 on 2007-04-15
> **RichBR549 said:**
> I'd like to boot to the hdb HD(27Gb) and keep apps there, then use the hda HD(160Gb) for storage(mainly photos).  Machine = Dell Dimension 4100 PEntium III 1Ghz, 512Mb.

If I need to keep grub to do this that's ok.  I was thinking I may need to change the HD's physical position on the IDE cable and change ID's, but I'll do whatever works best in the long run.

I'll read up on gparted and grub(only used it once for the dual boot install)  and keep looking for some great advice.
Thanks.

Forgot to add hda is NTFS, so I assume I'll have to reformat somewhere in the process.

---

### Post by confused57 on 2007-04-15
> **RichBR549 said:**
> I'd like to boot to the hdb HD(27Gb) and keep apps there, then use the hda HD(160Gb) for storage(mainly photos).  Machine = Dell Dimension 4100 PEntium III 1Ghz, 512Mb.

If I need to keep grub to do this that's ok.  I was thinking I may need to change the HD's physical position on the IDE cable and change ID's, but I'll do whatever works best in the long run.

I'll read up on gparted and grub(only used it once for the dual boot install)  and keep looking for some great advice.
Thanks.

Reinstalling Ubuntu would be the easiest way to set up a dual boot with 2 hard drives...see the 3rd link in my signature for doing this.  Make sure to check the hard drive jumper settings, if they're already set to "Cable Select", you should be good to go.  However, if they're set to master & slave, you'll need to change the jumper's accordingly.

If reinstalling Ubuntu isn't an option, you can try switching the physical positions of the hard drives, bootup your pc & at the boot grub menu, highlight your Ubuntu entry, press "e", then change root from (hd1,x) to (hd0,x) and in your kernel line change root=/dev/hdb1 to root=/dev/hda1, then press "b" to boot.  If this works, it's only temporary, but it's easy to make it permanent in your /boot/grub/menu.lst.  Your /etc/fstab will probably need to be edited as well.

There's some great info explaining grub in the first link in my signature.

---

### Post by RichBR549 on 2007-04-16
Got it!   It took me almost 5hrs, but I learned a lot today. 
I think I took the long route but everything is setup like I wanted.

1. Used "backup2l" to backup my Linux stuff and just moved data from XP to a external HD.
2. I always install my HD's Cable-Select, so I just switched their position on the IDE cable.
3. Used my 6.10 live/install CD to do a complete new install.
4. Setup Wifi, install "backup2l"(including adding my backup dir and edit backup2l.conf file like it was so restore will work.
5. Setup users.
6. Restore old files using "backup2l".
7. Install updates from Synaptic Pkg Mgr that were waiting(164!).  
8. install GParted and use to format the XP HD(now hdb1) to ext3.
9. Create mount folder in /media/ for hdb and change permissions to make folder accessible to everyone.
10. Edit fstab for the new hdb info.
11. Reboot!


Thanks for the help.   The links in your signature were really helpful as was this one: [http://www.smorgasbord.net/book/export/html/195](http://www.smorgasbord.net/book/export/html/195)

---

