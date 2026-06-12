---
title: "two grubs - how to remove the first one"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by checkers1811 on 2010-05-12
I have been using 9.0 and have recently installed 10.04 using Wubi installer. 

When I boot up there is a grub loader that shows Win 7 and several Ubuntu 9.0 versions. 

If I choose Win 7 from that menu I get another grub loader with Win 7 and 10.04 Wubi Ubuntu. 

How to I PERMANENTLY remove the first grub boot loader?

---

### Post by darkod on 2010-05-12
Wubi is installed "inside" win7. When you select win7 in the first grub2 as you call it, you get the windows bootloader offering selection of win7 and 10.04 wubi, not a second grub2. A second grub2 might follow after selecting 10.04 in the windows bootloader but it's sort of "virtual" because the whole wubi is installed inside windows, it doesn't reside on its own partition and the bootloader is not on the hdd MBR.

You didn't mention if you plan using the 9.10 still, because the first grub2 on your MBR is the only way to boot it. Removing it will leave your 9.10 ubuntu unbootable.

Otherwise, in general you can remove the grub2 from the MBR by using win7 install dvd, or with ubuntu commands executed from the live mode for example. It can work from your 9.10 installation on the hdd, but I recommend the live mode.

However, as I said, removing grub2 from the MBR will make the 9.10 unbootable.

Do you want the commands?

---

### Post by checkers1811 on 2010-05-12
Thanks for the quick answer. 
I do not intend to use Ubuntu 9.10 an longer and will be removing that partition. 

So, sure. What are the live mode commands?

---

### Post by darkod on 2010-05-12
Not that I'm trying to change your mind, but just to remind you that wubi is not meant to be a long term installation. That has been confirmed by its developer too. People try to use it as a full install and it can work, but sometimes it leads to problems too.

It was meant to be a quick way to try ubuntu without having to repartition the hdd. Since you already installed 9.10 as full install and have some experience with it, I wonder why you would decide to install 10.04 as wubi. I would recommend installing 10.04 over 9.10 as a full install again.

However, the choice is yours. :)

You can remove grub2 from the MBR by using lilo to write generic mbr on the hdd. The commands will issue some warnings but since you don't plan to use lilo, ignore them.

Boot the live mode and execute in terminal:
(I assume your hdd is /dev/sda, if not change in the second command accordingly)

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Restart. Now you should see the win7 bootloader directly. After booting into win7 you can delete the 9.10 partition and create a new one in its place, for example ntfs that you can use with win7.

---

### Post by checkers1811 on 2010-05-12
Hmmm. I guess you have changed my mind. 

The reason that I started in this direction was because the 10.04 upgrade process did not work. I left me unable to boot any of the Ubuntus that were in the boot loader menu. I sometimes see the new Ubuntu splash screen, but is soon disappears leaving me with a black screen ... Uhh.

I have since found a way to get my files back (using the wubi install) and can start over with a CD install. So, I guess I'll go that way instead. 

Will the CD install remove all of the 9.10 Ubuntu boot menu items?

---

### Post by darkod on 2010-05-12
Unfortunately, upgrades to a newer version can go wrong often. Lot of people just upgrade from LTS to LTS (once every 2yr or similar) because of that.

Yes, the new install will not have the 9.10 kernels shown in the menu. But now it's the time to consider whether you want separate /home partition. It allows you to do a clean install instead of an upgrade because all your personal data, settings, etc will be kept in /home. You just format / and leave alone /home.

With the default install Home is just a folder in / and you can't do that.

Anyway, to install 10.04 over the 9.10 using the same partition, boot the installer but select Manual Partitioning. It will show you list of the partitions. The current 9.10 / will be marked Not Used. Click on it to select it, and the button Change at bottom.

Change Not Used in ext4, tick the format box, and select mount point as /.

That's it, if you want to keep going without separate /home.

If you want to use the situation and create separate /home partition, decide how to split the size of your current / into / and /home. Usually 10GB is plenty for / if you have separate /home. Give the rest to the /home partition to have space for your files.

In this case again you need to use the Manual Partitioning.
Delete the / partition (be careful to delete the correct one).
In its place, create the new / partition, filesystem ext4, mount point /.
Then create the new /home, filesystem ext4, mount point /home.

In both cases the swap partition should be reused automatically, but you might want to click on it, then the Change button and double check that the Swap Area is selected.

---

### Post by darkod on 2010-05-12
I forgot to mention specifically, but both of the methods will destroy your current 9.10 and the files in it. You mentioned you have them backed up right? Make sure you do.

You can also extract them using live mode. You should be able to open the 9.10 partition.

Once that is done, proceed as above.

---

