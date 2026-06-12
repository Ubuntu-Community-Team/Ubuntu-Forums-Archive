---
title: "Moving from ext3 to ext4"
date: 2009-01-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by davideotape on 2009-01-22
I am aware, that as of the release of 9.04, there is support for the ext4 file system. I have also heard that this new filesystem reduce fragmentation and boot times.

I have a 9.04alpha3 system that has been upgraded from 8.04 to 8.10, and then up to 9.04. Because I have been using ubuntu for a fairly long time, I have lots of extra packages installed, and have lots of personal files on my ubuntu partition.

If I want to move to ext4, I think I have two options;

1. Create a separate partition to store my home directory. This would have to be ext3 to work with [ext2 IFS]("http://www.fs-driver.org/"). I would then somehow re-install 9.04 on to a new ext4 partiton. 

The problems I have with this method are;

a. I would like a way to carry all my installed packages across to the new installation, to save me having to download and install lots of new packages again.
b. I would also like to carry across my current configuration files, to save me having to configure all my programs again.
c. I don't really want to have to download a live CD to install the new OS.

2. Simply copy everything across to the new partition.

The problems I have with this method are:

a. There is no way I would be able to access my files from windows.
b. I'm not sure if this is possible at all

That is all I can come up with at the moment.
All help appreciated :D

David

---

### Post by Gina on 2009-01-22
AFAIK there is no ext4 filesystem driver available for Windows (anyone please correct me if I'm wrong).  Other versions of Ubuntu (including earlier Jaunty) do not have ext4 support and therefore cannot access ext4 filesystems.  In view of this and that ext4 is still young yet, I would recommend sticking with ext3.  Although ext4 has been tested for some time in another distro, several testers of Jaunty have had extreme data loss when running ext4 filesystems.

In conclusion... I would not advise installing or converting to ext4 unless you have no important data on that machine and will not worry if you lose everything.  That also applies to a development system generally.  Don't be fooled into thinking you are safe testing on a separate partition - or even a separate hard drive.

---

### Post by ShokTHX on 2009-01-22
I think I am wondering about converting to ext4 along the same lines.

Could you clone (I think Parted Magic has the tool to do this) a current installation to a new partion, boot to the new partition, reformat the old partition to ext4 and then boot to that partition? Or would the file system also be cloned?

---

### Post by Gina on 2009-01-22
The cloning copies the partiton bit for bit.  A copied and restored image is an exact copy.  It's a good way of backing up as long as you have the room on your backup device but it takes a long time over a LAN.  An external USB2 hard drive or memory stick is faster but you're still copying a lot of data.  Yes, you could make a backup copy of your partition(s) and then convert to ext4.  Be sure to disconnect your backup device when running on ext4 to avoid the possibility losing the backup copy as well.  Another point is that converting doesn't produce all the benefits of the new filesystem - it just makes it compatible.  Only new files are given the extended attributes available in ext4.

Partimage will make a backup copy of a partition and you can choose to compress the data to take up less room on your backup medium.  Of course, compression adds to the time taken.  I have used partimage several times to backup whole partitions and even to move whole operating systems from one hard drive to another.

---

### Post by ian dobson on 2009-01-22
Hi,

Have a look here [http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)

Regards
Ian Dobson

---

### Post by mariuz on 2009-01-22
here is the way a moved from ext3 to ext4 on jaunty 
using the alpha live cd

[http://mapopa.blogspot.com/2009/01/ext3-to-ext4-migration-on-ubuntu.html](http://mapopa.blogspot.com/2009/01/ext3-to-ext4-migration-on-ubuntu.html)
but i would make an backup first , it might delete all your data

---

### Post by gjoellee on 2009-01-22
NOTE: If you get a kernel panic, try booting in recovery mode

---

### Post by inportb on 2009-01-22
> **mariuz said:**
> here is the way a moved from ext3 to ext4 on jaunty 
using the alpha live cd

[http://mapopa.blogspot.com/2009/01/ext3-to-ext4-migration-on-ubuntu.html](http://mapopa.blogspot.com/2009/01/ext3-to-ext4-migration-on-ubuntu.html)
but i would make an backup first , it might delete all your data

This could be done in the recovery root console as well... just make sure the drive is not mounted before you start.

And... if you don't enable extents, I reckon you could still use the generic ext2fs driver for Windows.

---

### Post by caryb on 2009-01-22
If I could offer some advice, I decided to rebuild my machine as it had been upgraded from Gutsy through to Jaunty (& all stops in between) I found on my laptop it actually installed some new features of KDE4 that were not there. In upgrading all the time I feel you sometimes miss getting new features & also during the intrepid install I had a legacy KDE4 folder because of the transition from 3.5 to 4. Sometimes it is good to start with a clean slate. 

I also am concerned with some of the posts of data corruption in ext4 I cant quantify it but I believe that some of this could be due to the ext3 -> 4 upgrade. I did a fresh install of alpha 3 & built a fresh ext4 mount for my whole drive & have not experienced any problems at all.

Cary

---

### Post by Gina on 2009-01-22
I've done a clean install in ext4 and have had no problems so far either.  But I am being extra cautious this time as it seems a fundamental upgrade.

---

### Post by Archmage on 2009-01-23
If to answer the topic-starter.

If you have the place I would suggest setting up extra-partitions with ext4 and than move every linux-stuff there.

If you don't have the space, I would suggest converting ext3 to ext4, although it may miss some features on the old files.

For sharing your data between Ubuntu and Windows, I would suggest to share it over NTFS. This way Windows and Linux can acces it.

---

### Post by Radomir on 2009-01-23
I asked a question like this in general discussion, but got no replies. I've compiled 2.6.28 kernel in Intrepid successfully, with ext4 support enabled as module. I have only one partition - swap is in a file. Would like to convert it to ext4, and I see no problems with that, except grub...
As I've read, you need updated grub to boot from ext4 in intrepid, and also rootfstype=ext4 in menu.lst as a workaround. How can I update grub in my existing install? I could download latest jaunty's grub deb package, but I suspect that there is more to it than just installing it. Any help appreciated. I know I could move to jaunty, but I would like to try this...

---

### Post by davideotape on 2009-01-23
Thanks for the replies guys! In the light of everything said, I think I will hold off for the moment. I am gradually moving from windows to ubuntu, over the period of about half a year, and am about half way there. I therefore think it will be to risky to change for a small performance increase. I also have an old hard drive which I have ubuntu on a.t.m., so I don't think it will make much of a difference. Maybe when I am done with windows, and move over on to my newer hard drive I will use ext4, but for now I think I'll stick with ext3.

---

### Post by Gina on 2009-01-23
Wise decision IMV :)

---

