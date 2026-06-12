---
title: "[SOLVED] Question about Updates and boot menu"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by Vic! on 2007-09-05
I just installed the updates to ubuntu and when i restarted the computer i noticed i have two different ubuntu OS's to choose from one ends in 5 one in 6 i was wondering is there a way to just have the most recent one and get rid of the old one?.. also im dual booting with vista but i want to get rid of it completely how do i do that (delete vista partition) and just run ubuntu?


Much appreciated if someone can answer this THANK U! :)
u guys have been awesome when it comes to
 helping me solve stuff on linux

---

### Post by merlinus on 2007-09-05
You can format the vista partition to ext3 and use it for data storage.  Use gparted live cd, a small download:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Once you have done that, post back for assistance on how to make it available from ubuntu, and edit the grub file so it will not appear as a choice.

I would recommend keeping both the latest and last kernel.  You never know when something will go wrong, and can use the older one to boot from.

-merlin

---

### Post by Vic! on 2007-09-05
Thanx i made the live cd and booted from it to take a look... theres a few sections to my disk ...( now i just got to see which is which to go about erasing vista)when i look for which one is vista what should i be looking for.. i just got out of the live cd and am back on my ubuntu (latest) can i figure out which  is which from here?  THANX AGAIN merlin :)

---

### Post by merlinus on 2007-09-05
Look at results of

```

sudo fdisk -l

```

It should tell you which partition is/was vista.  It is probably the first one on your hdd.

-merlin

---

### Post by Vic! on 2007-09-05
alright so im guessing by these results :

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        5187    40122070+   7  HPFS/NTFS
/dev/sda3            5188        9544    34997602+  83  Linux
/dev/sda4            9545        9729     1486012+   5  Extended
/dev/sda5            9545        9729     1485981   82  Linux swap / Solaris

i have no clue other than sda 3 is linux and so is sda 5

---

### Post by merlinus on 2007-09-05
Looks like vista is sda2.  sda1 may be a recovery partition placed on the hdd by the computer mfr.

You can format that as well, and combine sda1 and sda2 into one partition.

If you do that, then you will have to edit a few files for ubuntu to work properly, and reinstall grub.

None of this is overly difficult, and you will learn a lot in the process.

-merlin

---

### Post by Vic! on 2007-09-05
Thanx alot merlin..alright il give it a go right now. thanx again!

---

### Post by Vic! on 2007-09-05
Ok i deleted sda 1 and 2 and combined them into new partition 1 the boot menu still says windows vista is a option but when i tried to boot it it said no such partition exists which is true so how do i edit the boot menu and get rid of the vista option and then make use of the 38 GB i have empty now? THANX :)

---

### Post by merlinus on 2007-09-05
Good so far -- congratulations!

You basically now have two choices.  You can reinstall ubuntu, if you have not created any data files nor done lost of installing of apps.  That is easiest.

Second is to format the new partition as ext3, which you can do from gparted.  Then you will have to create a mountpoint for the new partition, and edit /etc/fstab and probably /boot/grub/menu.lst.

You may also have to reinstall grub.

Let me know....

-merlin

---

### Post by Vic! on 2007-09-05
cool you mean boot from ubuntus live cd and install it like i did the first time except now i use the entire HD  instead of a partition?... i could do that since the only thing i had done for ubuntu was install audio drivers i could do that again since i already know how.... could i do that??:popcorn: lol thats awesome thanx

---

### Post by merlinus on 2007-09-05
Yes, reinstalling at this point, and using the entire hdd, is probably the best way.  One suggestion is to make a separate partition for /home, in addition to / (root) and /swap.

That way your data, preferences, configurations, email and bookmarks will not get overwritten should you reinstall or upgrade to the new version due out middle of next month.

If you tell me how much space you have, I can recommend partition sizes.

-merlin

---

### Post by Vic! on 2007-09-05
oh thats very very very convenient thanks a lot! does this mean during the live cd instalation process i will chose to manually decide what goes where? well i have a 80 GB hdd and so far no real configurations or programs that i installed i was kind of making a OS switch from vista which tottaly overwhelmed my 512 ram that came with this modest notebook.  one question will making separate partitions for /home, / , and /swap in any way make it difficult for me to install needed drivers or instructions in the future?

---

### Post by merlinus on 2007-09-05
If you have 80G, then I recommend three primary partitions, including one extended that will contain /swap and whatever remains after / and /home as logical partitions.  This will give you a lot of flexibility.

20G for / will give you plenty of room for applications.  20G for /home will more than suffice for your data files and application preferences and such.

Format the rest as ext3 as a logical partition with no mountpoint, and that will allow you to perhaps install another distro or operating system, if you so desire in the future.  You can of course place data files there as well, and even divide it up at some point.

You will be able to create a mountpoint for that partition (e.g. storage) after installation, and reference it in /etc/fstab.

The Manual option will allow you to specify all of this.

-merlin

---

### Post by Vic! on 2007-09-05
ok thank you ! i will be trying that now  thanx again! :)

---

