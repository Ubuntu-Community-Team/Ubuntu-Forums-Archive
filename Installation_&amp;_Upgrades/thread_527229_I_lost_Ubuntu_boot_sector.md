---
title: "I lost Ubuntu boot sector"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by mircione on 2007-08-16
I have two DD, one for Linux (Feisty) and one for Windows.
When I try to use Linux I receive an error 17  message. I installed Ubuntu on the same DD but in a different partition and now I can access my old configuration. My conclusion is: I lost my boot sector. I like to know how I can uninstall the new Ubuntu and keep my boot sector for the old configuration or how can I repair the boot sector.
Thanks.

---

### Post by logos34 on 2007-08-16
For error 17 try the suggestions here:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

Or boot from the ubuntu live cd, mount your linux root partition (and/or /boot if on separate partition)

Post the output from:

**sudo fdisk -l **(that's a lowercase L)

copy n paste your **menu.lst** file in /boot/grub

---

### Post by Herman on 2007-08-16
Yes, I agree with logos34, and I think you'll find that your problem has nothing at all to do with your Windows boot sector. Neither Ubuntu nor GRUB bootloader will touch your Windows boot sector, unless you force them to.

Ubuntu does have GRUB write some code to your hard disk's Master Boot Record though, to make the MBR 'point to' the rest of the GRUB bootloader in the Ubuntu partition.
Most likely, it a simple adjustment in the bootloader's configuration files in the Ubuntu partition will be all that is needed.

When you have Ubuntu booted up, can you please open up a terminal, (go 'Appliactions'-->'Accessories'-->'Terminal', and input the following commands please, sudo fdisk -lu,
```
sudo fdisk -lu
```sudo gedit /boot/grub/menu.lst
```
sudo gedit /boot/grub/menu.lst
```If you can post in the results from sudo fdisk -lu or a screen cap from Gnome Partition Editor so someone can check your partitions are okay and note your partition numbering, that will help someone help you.
If you can post here the bottom half of your /boot/grub/menu.lst file someone can look for a mistake in that and see that it corresponds with what your fdisk output says or help you edit it correctly. That should fix it.

If you're not sure about how to type terminal commands, remember you can copy and paste them from Ubuntu web forums code boxes into your own terminal instead of typing them. With some commands you need to check to see if they need a little adjusting for your computer, but the ones we just gave you will be fine for any computer, just as thay are. :)

You should be able to boot with [Super Grub Disk]("http://geocities.com/supergrubdisk/") in the meantime if you're in a rush.

Regards, Herman :)

---

### Post by mircione on 2007-08-16
> **Herman said:**
> 

You should be able to boot with [Super Grub Disk]("http://geocities.com/supergrubdisk/") in the meantime if you're in a rush.

Regards, Herman :)

Thanks Herman. My Ubuntu is back now. I used Super Grub Disk.
Thanks logos34 for your reply.

One more question: I like to do a copy (image) or something like that, to my Ubuntu. I mean, if my DD have a problem one day, just to put a image in the new DD and go. I use for example Acronis True Image for Windows.
Best regards

---

### Post by logos34 on 2007-08-16
> **mircione said:**
> One more question: I like to do a copy (image) or something like that, to my Ubuntu. I mean, if my DD have a problem one day, just to put a image in the new DD and go. I use for example Acronis True Image for Windows.
Best regards

Try Partimage or [Clonezilla]("http://clonezilla.sourceforge.net/gparted-clonezilla/") (they image only the used space rather than the whole disk or ppartition).

But I'm not entirely happy with Partimage for a variety of reasons and I'm beginning to wonder if the venerable 'dd' command is not the best way to go--it has the virtue of simplicity and reliability (even if it does copy used and unused sectors).  I've been using it to clone my ubuntu root partition by piping it through gzip compression:
[B]
sudo dd if=/dev/hda3 | gzip > /media/hda5/hda3root_backup.img.gz[/B]

See 'dd' entry here:
[https://help.ubuntu.com/community/BackupYourSystem#head-535f2fd341e44e59596908dd6e7bc7666f0aecc1](https://help.ubuntu.com/community/BackupYourSystem#head-535f2fd341e44e59596908dd6e7bc7666f0aecc1)

Everyone has their preferred applications.  That's mine.

---

### Post by mircione on 2007-08-17
> **logos34 said:**
> Try Partimage or [Clonezilla]("http://clonezilla.sourceforge.net/gparted-clonezilla/") (they image only the used space rather than the whole disk or ppartition).

But I'm not entirely happy with Partimage for a variety of reasons and I'm beginning to wonder if the venerable 'dd' command is not the best way to go--it has the virtue of simplicity and reliability (even if it does copy used and unused sectors).  I've been using it to clone my ubuntu root partition by piping it through gzip compression:
[B]
sudo dd if=/dev/hda3 | gzip > /media/hda5/hda3root_backup.img.gz[/B]

See 'dd' entry here:
[https://help.ubuntu.com/community/BackupYourSystem#head-535f2fd341e44e59596908dd6e7bc7666f0aecc1](https://help.ubuntu.com/community/BackupYourSystem#head-535f2fd341e44e59596908dd6e7bc7666f0aecc1)

Everyone has their preferred applications.  That's mine.

Thanks logos34.
I will try clonezilla today.
Best regards.

mike

---

