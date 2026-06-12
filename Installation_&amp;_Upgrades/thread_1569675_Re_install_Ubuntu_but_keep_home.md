---
title: "Re install Ubuntu but keep /home"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by chamber on 2010-09-07
I made a massive cockup when installing Windows 7 to a seperate partition on my hard drive and as a result of my attempting to fix GRUB I can now no longer boot into anything apart from the live cd.

I was wondering if there was a guide I could follow to show me how to reinstall Ubuntu but keep my /home folder which is on a seperate partition?

Failing that what is the best way to make a backup of my home folder and then wipe /home and /root and start again?

---

### Post by Elfy on 2010-09-07
If your /home is on a seperate partition, start the installer - pick manual at the partition stage.

Select the existing / partition - Edit partition - Use as ext4,format and Mountpoint - / then save/close that window

Select the existing /home partition - Edit partition - Use as whatever it was previously, DO NOT FORMAT and Mountpoint /home - save and close that window

Check that the only partition that is going to be formatted is the existing / partition.

Carry on - that will install over the existing installation and use the old /home.

Use the same username though.

Always good to have backups though ;)

---

### Post by doihavetodothis? on 2010-09-07
how to back up your home folder, at least - it worked for me:
[http://ubuntuforums.org/showthread.php?t=1560044](http://ubuntuforums.org/showthread.php?t=1560044)
the only thing I haven't discovered yet is how to save my mail and bookmarks... but I'll get there :)

---

### Post by doihavetodothis? on 2010-09-07
> **forestpiskie said:**
> If your /home is on a seperate partition, start the installer - pick manual at the partition stage.

Select the existing / partition - Edit partition - Use as ext4,format and Mountpoint - / then save/close that window

Select the existing /home partition - Edit partition - Use as whatever it was previously, DO NOT FORMAT and Mountpoint /home - save and close that window

Check that the only partition that is going to be formatted is the existing / partition.

Carry on - that will install over the existing installation and use the old /home.

Use the same username though.

Always good to have backups though ;)

aha - I just replied to this thread as well. Will this method keep my mail and bookmarks too? haven't wanted to re-install without checking that. I have Xp and Ubuntu on separate partitions. Thanks.

---

### Post by chamber on 2010-09-07
> **forestpiskie said:**
> If your /home is on a seperate partition, start the installer - pick manual at the partition stage.

Thats parfait! Will have a go at that tonight.


> **forestpiskie said:**
> 
Always good to have backups though ;)

I usually do a backup before something like this, in my haste to get it over with I dun goofed. 

Lesson learned.

Muchly appreciated.

---

### Post by chamber on 2010-09-08
worked a charm and were all good to go.

forestpiskie, you are a legend. :)

---

### Post by Mutikasa on 2011-12-19
SO. what happens if I choose only / folder to format and install but leave /home as it is?
Will the Ubuntu then install on / partition and there make a new folder /home?
so I will have two /home folders? one on install partition and one from before?

what about swap and NTFS partition?

---

