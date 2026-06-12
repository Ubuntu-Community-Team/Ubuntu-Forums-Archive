---
title: "Suggestions for Ubuntu install"
date: 2016-11-02
forum: Installation &amp; Upgrades
---

### Post by kg4muc on 2016-11-02
I would like to have one drive containing the Ubuntu OS and maybe very limited storage and I would like to add an additional drive for file storage mainly audio at this time..maybe additional drives later on for video and stills if possible.  What format would be best to partition the drive to?  Multiple partitions?  Just one large partition?
Not 100% sure of best way to go with this project.

Thanks for any suggestions!

---

### Post by kevdog on 2016-11-03
I always partition my drives with a /boot, /, /home and /swap.  You may want another want to just mount your other drive as a directory.  In terms of format type -- are you asking like ext3 versus ext4? I usually just stick with the basic ext4 type since its very reliable.  I'm contemplating zfs as trial run.

---

### Post by kg4muc on 2016-11-03
Thanks for the reply. I was mainly concerned with EXT3 vs EXT4.
I have a few Linux based satellite receivers and most all but one seem to do good with EXT3
I 'm guessing the safest way to do the format would be while running Ubuntu from DVD ?  I have another drive that has a boot problem I'm hoping I'll be able to see when I get the proper adapters in since it has quite a bit of files I should try to archive.

Thanks again for the reply!

---

### Post by Bucky Ball on 2016-11-03
Ok. Ubuntu must be installed on an EXT filesystem. EXT4 is the most recent and the most used. I'd go for that. A basic set up would be:

/ = where the OS goes, EXT4 and you need, say, 20Gb say (although you could probably get away with considerably less but depends what you're planning)
/swap = 2Gb or the same size as your installed RAM if you are thinking about hibernating.

There are LOTS of options for how you go about things. I give a reasonably comprehensive description in the second post of the thread you originally posted on if you'd like to take a look there, but basically, as for the storage partitions, if you're wanting to use them with Windows, then NTFS they should be. If not, EXT4 is fine.

Another setup would be

/ = 20Gb, the OS
/home = as big as you can get it, your personal data
/swap = 2Gb

And there are others. For the record, I have never created /boot partitions or any other partitions apart from / and /swap when installing, but that is just me an by no means the way it *should* be done (I used to have /home partitions years ago but dropped that in favour of linking my installs to data folders in one main, big data partition).

I always advise a pen, paper, beverage and draw a rough plan of exactly how your partitions are going to be on that drive *before* you dive into the digital. If you can't create that mud-map, you're not ready to roll yet. :)

---

### Post by ian-weisser on 2016-11-03
Over the years, your preferences will change. And you will reinstall again someday.
Since your partitioning scheme is not permanent, your initial choices in this area are not critical.

Your idea of keeping data separate from /home and system is a good idea.
If your data is valuable to you, plan on external backups also. Hard drives fail. Backups also make future reinstalls and repartitions easy.

Bucky Ball's advice on how to plan, how to tell if you are ready to plan, and minimum size suggestions, is excellent. Listen to it!

---

