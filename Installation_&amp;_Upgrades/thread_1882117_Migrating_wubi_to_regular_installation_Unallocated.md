---
title: "Migrating wubi to regular installation: Unallocated partition"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by bentley4 on 2011-11-16
Hey guys,

I have windows 7(308,7 GB) and installed wubi 11.04(40GB).
Now I want to migrate everything to a new partition because I want to reinstall windows without losing my ubuntu partition.
For this i know I can follow this thread: [http://ubuntuforums.org/showthread.php?t=1519354]("http://ubuntuforums.org/showthread.php?t=1519354") 

This guide says: > The partition(s) must be created already. the examples shown below assume the target partition is /dev/sda5 and the swap partition (if required) is /dev/sda6.

1. Can I just type *unallocated *instead of */dev/sda5 *in my case? 
Here's a pic of my gparted screen:
[IMG]http://uploadpic.org/storage/2011/psSHpAOeMkbN9ph1oYLIaNbgU.png[/IMG]
2. What do I need to do here?

3. Also, when I complete the migration, will all installed programs in my current wubi installation be installed in the new regular partition?

---

### Post by bluexrider on 2011-11-16
Your sda5 is a swap file and so is sda7 and you only need one. Need some house cleaning before you begin.

---

### Post by bcbc on 2011-11-16
The unallocated space is unavailable because you have 4 primary partitions already and the unallocated space is not included in the extended partition /dev/sda4.

You need to extend /dev/sda4 to absorb the free space. Then you can create a logical partition from that space. Until then you cannot use it.

(The migration requires a real ext4 partition)

Yes the migrated install will be identical to the wubi install.

---

### Post by Mark Phelps on 2011-11-17
I don't know if GParted will let you expand the Extended partion to the left.  Last time I tried that, I seem to remember that it would not do that.

Since you're also running Windows, an alternative would be to download and install Partition Wizard (it's free).  You should then be able to use that to expand the Extended partition to the left.

---

### Post by bcbc on 2011-11-17
I was playing with gparted yesterday - it will move partitions to the left. It just warns you a lot if you move a primary partition and it can take a lot longer depending on the amount of data involved. However, in this case, you're just expanding the extended so it should be very quick.

There are always small risks associated with partitioning, so it's important to make sure your backups are up to date.

---

### Post by bentley4 on 2011-11-18
Thnx guys. Thnx bcbc for yr script btw!
I used partition wizard and created a ext4 partition of the 102.70 GiB unallocated space.
Then I used the script to transfer wubi to that new partition /dev/sda5. The terminal said it was succesful. 
But I'm still uncertain if it will work. I now have the following situation in Gparted:
[IMG]http://www.freeimagehosting.net/a5ee2[/IMG][IMG]http://www.freeimagehosting.net/a5ee2[/IMG][IMG]http://www.freeimagehosting.net/a5ee2[/IMG][IMG]http://www.freeimagehosting.net/newuploads/a5ee2.png[/IMG]
Gparted shows that /dev/sda5(my new part.) is a part of /dev/sda4 somehow.
If I reinstall windows and thus lose wubi, won't I lose /dev/sda5 as well?(because it seems to be a part of /dev/sda4.)
How can I make sure? How can I check the partition my pc is now running on?
When I restart my computer and get to the GRUB screen I don't see any other linux version to select than before. Is that normal?

---

### Post by bcbc on 2011-11-18
Great! Glad it worked out.

By the way - you are running the migrated install - you can see from the gparted snapshot that the /dev/sda5 is locked (the key) and that means it is in use. It can also be shown if you mounted it, but since that's the only one locked, you are probably booting from it. But you didn't use one of your swap partitions...

Anyway:
1. To confirm, drop to a terminal (Ctrl+Alt+T) and run:
```
cat /etc/fstab
```
It will say something like:
```
# root was on /dev/sda5 when migrated
UUID=35c7268f-3ac8-4a70-9eea-519b55db64f8    /    ext4    errors=remount-ro    0    1
```

You don't see any other Ubuntu install in the grub menu, because grub won't pick up a wubi install automatically. If you boot windows, then you'll see the windows boot manager, and then if you select Ubuntu you'll see the Wubi Ubuntu at the top, and the migrated ubuntu at the bottom of the (wubi install's) grub menu.

If you reinstall windows it will likely remove the grub bootloader, so you should be prepared to reinstall grub from an Ubuntu live CD after replacing windows.

---

### Post by bcbc on 2011-11-19
PS I realise you had another install on /dev/sda6 - to add that on your migrated install run "sudo update-grub". 

And also, after reinstalling windows you can follow the instructions here for reinstalling the grub2 bootloader:
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)

---

### Post by bentley4 on 2011-11-19
I did 'sudo update-grub' like you suggested, but now I can't resize any partitions again with Gparted just like the original situation. : (
[IMG]http://www.freeimagehosting.net/7eb8c[/IMG][IMG]http://www.freeimagehosting.net/7eb8c[/IMG][IMG]http://www.freeimagehosting.net/7eb8c[/IMG]_[[IMG]http://www.freeimagehosting.net/t/7eb8c.jpg[/IMG]]("http://www.freeimagehosting.net/7eb8c")_
Now there's a key symbol in front of my windows partition! How do I undo this?

---

### Post by bcbc on 2011-11-20
You have mounted it - so gparted won't allow you to modify it. Either unmount it from the command line ("sudo umount /dev/sda3"), or just click on the "eject" symbol next to the partition entry on the left of the from the nautilus browser window.

---

### Post by bentley4 on 2011-11-21
Works, thnx!!

---

### Post by LinuxFan999 on 2011-11-21
Next time you start a thread and post screenshot, please upload it as an attachment to your post (scroll down to additional options and you will see a button that says "attach files") because it is safer and faster.

Don't forget to mark this thread as solved.

---

