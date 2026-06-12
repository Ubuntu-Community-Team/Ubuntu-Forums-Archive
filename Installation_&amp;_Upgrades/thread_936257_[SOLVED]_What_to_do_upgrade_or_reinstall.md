---
title: "[SOLVED] What to do: upgrade or reinstall?"
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by rubenverweij on 2008-10-02
Hello everyone,

I have a question: when the new release 8.10 comes out, should I upgrade or reinstall Ubuntu? My problem is, that I like to get a 'clean' start, but I don't want to lose any data, not only files, but bookmarks, emails etc.

So, if I should reinstall, how can I keep those things? And if I should upgrade, how do I get a 'clean' start?

I've read something about a separate home partition, is this worth a try or is there another way to keep your data?

I hope you understand my problem and that you can help me! :D

Ruben

---

### Post by Pumalite on 2008-10-02
If you want to do a clean install of Intrepid, then backup your /home and data. You can also make a 'separate /home':
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
If you decide to upgrade; make sure your system is fully updated and remove all third parties prior to the upgrade.

---

### Post by sub2007 on 2008-10-02
As Pumalite said, making a separate /home partition is very good sense. Backup and then when you come to reinstall make a separate /home partition during the install.

---

### Post by .nedberg on 2008-10-02
I have planned to do a clean install since 7.10, but I have gone the updatg road because I haven't found the time to set the machine again.

I don't see a problem with upgrading, but I know reinstall would be "cleaner". If I get the time to reinstall 8.10 I will make a separate /home as instructed in the link above.

---

### Post by Sef on 2008-10-02
There are less problems with a clean install than upgrade.   Whatever you do, **back up **your data first.  There are no 100% guarantees that all will go well.

---

### Post by rubenverweij on 2008-10-03
Okay, thanks to you all. I think I'll go for the separate /home approach then. I have a few more questions about that: in my current /home, there are loads of pictures and mp3s, what would be a good way to backup? I can't put it on my usb stick, I don't have an external hard disk and cd's is not really an option. Is a backup really needed when creating the separate /home partition?
Also, the configuration files for applications are stored in home too. But I wouldn't like to keep them, just my mail and bookmarks. Can I delete those folders savely before installing Intrepid?

[edit]
And a last question: should I set up the /home partition during the installation progress or now?
[/edit]

---

### Post by sub2007 on 2008-10-03
If you have a enough free space on your hard disk then you can use GParted to create a new partition without making a backup. Ubuntu will then treat that as another hard disk until you come to reinstall (if you fancy you can edit fstab to make it mount that partition as /home but perhaps it's easier to do that at reinstall) so don't delete your current home directory. When you come to reinstall, copy everything from /home over to that new partition. Then when you come to set your mount points during your next install, select your new partition as /home but DON'T choose to format it.

Technically you should always make a backup of your data before a reinstall or any partitioning operation. So if you do this without a backup then you do it at your own risk.

---

### Post by rubenverweij on 2008-10-03
Can I just configure it to make a new partition in the unused space? I have a partition of 230 GB with loads of free space, can you just let it create a new partition in that space, whitout touching the contents?

---

### Post by Pumalite on 2008-10-03
If you have chosen to do a clen install; you can make your /home partition at install going Manual. Don't forget to save your photos, etc. If you want to save everything in /home during install; you have to make a separate /home before you install. Then at install; go Manual, point to your /home partition, but DO NOT FORMAT

---

### Post by rubenverweij on 2008-10-03
I want to do a clean install, in my home directory I want to keep all the music files etc. which are in it at the moment.
So, I reduced the current partition succesfully, but when I tried to create a new one the "Logical Partition" option was greyed out -- only "Primary Partition" was available... What should I do?

---

### Post by sub2007 on 2008-10-03
I think you would want a primary partition, not a logical partition. I can't see your disk so I don't know what your partition table looks like. A primary partition is used on blank space on your disk to create a brand new, standalone partition. A logical partition is used if you have an extended partition which you want to split to create multiple smaller partitions. They are both as good as each other, the only pro with an extended partition is that you can get more partitions (as your extended partition would show as one partition to the disk and you can only have four partitions on your disk).

[http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

---

### Post by rubenverweij on 2008-10-03
Ok, thanks! Than I will just use the primary partition type. I only thought I had to use logical because the how-to showed that...
Only one question left: when I reinstall, how do I configure Ubuntu to use the new partition as /home?
Sorry for my tricky questions...:)

---

### Post by Pumalite on 2008-10-03
Post a screenshot of Gparted
(boot your Ubuntu Live CD if you have to)
You have a rule that allows you only 4 primary partitions per drive.

---

### Post by sub2007 on 2008-10-03
> **rubenverweij said:**
> Ok, thanks! Than I will just use the primary partition type. I only thought I had to use logical because the how-to showed that...
Only one question left: when I reinstall, how do I configure Ubuntu to use the new partition as /home?
Sorry for my tricky questions...:)

Don't be sorry, you have to learn somehow and asking questions before is better than borking your install and then trying to sort it out :)

This guide should help:

[http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html)

Make sure you use GParted to write down the drives for which partitions do which. So if in GParted it shows your / partition as sda1 then make sure you write that down as you will need that later when setting the mount points (it won't show you your current mount points when installing).

Set the mount points as shown in the guide but also make a mount point for /home (as shown in the second diagram). So you should have mount points for /, /swap and /home. Then make sure you check to reformat / and /swap but do **not** put a check in reformat for /home.

---

### Post by rubenverweij on 2008-10-04
Thank you all for helping me, it's solved! I had some trouble when I wanted to login because I didn't own my home directory. Fixed that by going in console mode and executing "chown ruben /home/ruben". 
Now everything is working without a problem!

---

