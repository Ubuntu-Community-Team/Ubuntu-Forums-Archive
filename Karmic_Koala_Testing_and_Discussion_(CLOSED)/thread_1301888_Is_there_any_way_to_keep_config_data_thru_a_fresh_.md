---
title: "Is there any way to keep config data thru a fresh karmic install?"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 11010110 on 2009-10-26
Good afternoon all,

With the up and coming release of Karmic I have a couple of questions. I have Jaunty currently and I want to go to grub2 with the upgrade to Karmic. Now talking worst case scenario; if for some reason installing grub2 ends up fragging my box, would it be at all possible, assuming I made backups of my /home folder and such, to somehow copy all of the configs and data from my old programs to the new fresh Karmic install so I won't have to go and reconfigure everything? Could I just copy over my old /home folder and such and then reinstall everything and would it all just recognize and use the old data? I hope I am conveying my ideas well enough. I have been wondering this for some time. Also should I upgrade to grub2 before or after going to Karmic? I hear there are some glitches when doing it through Jaunty (and yes I am planning to chainload it to test first just to be sure).

Thanks for the help in advance everyone.

---

### Post by ctc26 on 2009-10-26
Hi,

The easiest and safest way to perform a system upgrade without losing your home directory and config files is to place '/home' on a separate partition to '/' (the Ubuntu system files).

As long as you are confident in the backups you have made, follow these steps:

1. Boot to a Karmic LiveCD, and enter GParted (partition editor).
2. Make a partition for both the system files and swap space, as per usual, as well as an additional partition for /home. (The root partition needs a minimum of 3GBs, your home partion should be the largest as it will hold all of your personal data, and the swap space should be twice the amount of RAM you have but no more than 3GBs)
3. Navigate to your newly created /home partition and copy over ALL of the data that you have backed up. Make sure you sudo or gksu before doing this so that all of the data is transfered.
4. Start the Karmic install. When you get to the partition setup select manual. Here you want to identify the filesystem for each partition and identify how it will be used. For the home partition select /home and do not tick the format box. For the root partition select / (the root partition must be formated). For swap simply identify the filesystem as swap.
5. At the personal information step make sure you input exactly the same details as you have for previous installs of ubuntu, including password (this can be changed after the install).

Once you have done this you will be able to do a fresh install of Ubuntu with every release and retain all of your config files as well. All you have to do is manually select your home partition (remembering not to format it) and ensure that you don't change your username or password during the install.

After that all of your customisations and configs will remain. But you have to reinstall applications that are not default in ubuntu. After they are installed they will retain any UI changes you had made.

Oh and Karmic has GRUB 2 by default so there is no need to update before going to Karmic as long as you do a fresh install.

Sorry for the long post.

---

### Post by bkratz on 2009-10-26
> **11010110 said:**
> Good afternoon all,

With the up and coming release of Karmic I have a couple of questions. I have Jaunty currently and I want to go to grub2 with the upgrade to Karmic. Now talking worst case scenario; if for some reason installing grub2 ends up fragging my box, would it be at all possible, assuming I made backups of my /home folder and such, to somehow copy all of the configs and data from my old programs to the new fresh Karmic install so I won't have to go and reconfigure everything? Could I just copy over my old /home folder and such and then reinstall everything and would it all just recognize and use the old data? I hope I am conveying my ideas well enough. I have been wondering this for some time. Also should I upgrade to grub2 before or after going to Karmic? I hear there are some glitches when doing it through Jaunty (and yes I am planning to chainload it to test first just to be sure).

Thanks for the help in advance everyone.



From what I have read updating to Karmic does not take advantage of Grub2 or the newer file structure of EXT4, but retains the old. So a full install is probably in my future.

---

### Post by forumache on 2009-10-26
> **bkratz said:**
> From what I have read updating to Karmic does not take advantage of Grub2 or the newer file structure of EXT4, but retains the old. So a full install is probably in my future.

Not so. You can upgrade to GRUB2 without problems, whenever you want, without reinstall.
You can also convert your filesystems from ext3 to ext4 after that, you will loose nothing. You'll get the benefits of ext4 only for the files newly created though (easy to solve, for example copy Music folder to Music.new (it will take advantage of ext4), delete Music, rename Music.new to Music, done).

You can, of course, do the full install, but you are not forced. Your choice :)

---

### Post by 11010110 on 2009-10-26
Thanks for all of the help everyone. How large should the root partition be then considering that the majority of my data will be stored in the home partition? How large is just large enough so it will not run out of room yet still leave as much to the home partition as possible? I only have about 100 gig to allot to Ubuntu sadly lol. That is great that all of the programs will just automatically use the old config files. I will definitely consider this!

Thanks again!

Oh and to ctc26, go All Blacks! lol

---

### Post by FuturePilot on 2009-10-26
> **11010110 said:**
> Thanks for all of the help everyone. How large should the root partition be then considering that the majority of my data will be stored in the home partition? How large is just large enough so it will not run out of room yet still leave as much to the home partition as possible? I only have about 100 gig to allot to Ubuntu sadly lol. That is great that all of the programs will just automatically use the old config files. I will definitely consider this!

Thanks again!

Oh and to ctc26, go All Blacks! lol

I usually give 20GB to / and the rest to /home. Of course I squeeze the swap partition in there too.

---

### Post by ctc26 on 2009-10-26
It depends on the number of third-party programs you usually install, but I usually dedicate 10GBs to "/" and have a separate partition for swap.

---

### Post by drumsticks on 2009-10-27
> **ctc26 said:**
> 
5. At the personal information step make sure you input exactly the same details as you have for previous installs of ubuntu, including password (this can be changed after the install).


My understanding is that the on-disk data structure for file ownership is simply the uid and gid.  So, when you reuse the /home partition on a new installation, whichever user you create with the same uid and gid will inherit the old file permissions.  Ubuntu's first user (created during install) has uid=1000, and gid=1000 regardless of username and password, so that helps with data continuity across installations.

Remember, file and folder permissions are only meaningful to the operating system that created it in the first place.  It means nothing when you take the HDD/partition and put it into another system.  That's why you need encryption if you're concerned about privacy, but that's a different topic ;)

---

