---
title: "Directories requires to mount drives"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by elmosim2 on 2010-02-23
Since I never got an answer to my last question:
[http://ubuntuforums.org/showthread.php?t=1414231](http://ubuntuforums.org/showthread.php?t=1414231)
I'll ask something simpler.  

When Ubuntu is booting up, what directories are used for the boot process up until it mounts other drives (such as an SD card).  

I think that question makes sense, don't hesitate to ask for clarification, though.

---

### Post by doas777 on 2010-02-23
well, if you are asking what i think you are asking, you need /boot at a minimum, but probably most of the folders in root, other than /home. I don;t think moving system files elsewhere is a great idea, but you may be able to pull it off.

you can resize a partition but only in very limited circumstances:
[http://www.linuxquestions.org/questions/linux-newbie-8/resize-partitions-in-ubuntu-363639/](http://www.linuxquestions.org/questions/linux-newbie-8/resize-partitions-in-ubuntu-363639/)

---

### Post by elmosim2 on 2010-02-23
I just tried it with just /boot and sometime during the boot process the screen went black and that was it.  I do know that /usr and /usr/local can be put on a different partition.  

Is there somewhere else I should be asking these questions?

---

### Post by DGortze380 on 2010-02-23
> **elmosim2 said:**
> I just tried it with just /boot and sometime during the boot process the screen went black and that was it.  I do know that /usr and /usr/local can be put on a different partition.  

Is there somewhere else I should be asking these questions?

Build an Arch Linux installation. It will help greatly in understanding the linux boot process.

At least look the guide.
[http://wiki.archlinux.org/index.php/Main_Page](http://wiki.archlinux.org/index.php/Main_Page)

---

### Post by elmosim2 on 2010-02-23
I'll build an arch linux install.  Sounds fun.  Thanks for your advice.

---

### Post by oldfred on 2010-02-23
You only gave your other thread a few hours and gave up? Generally the forum asks that you not bump until 24 hours.

Please see my and particularly Herman's comments in this thread on system partitions:
Herman on advantages/disadvanges of separate system partitions
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

It is most common to have /home separate if space is at a premium. I prefer to have a separate /data partition.
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508With](http://ubuntuforums.org/showthread.php?t=1397508With) add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/) 
Data separate or on USB stick
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

---

### Post by elmosim2 on 2010-03-03
I built an install with /usr /usr/local and /var on a separate disk .  These are all 3.5GB partitions.  From the reading I've been doing I think my /var directory should be bigger.  I only have about another 4GB on that disk left that isn't partitioned.  Are these the directories everyone would recommend I put on other partitions and should I make my /var directory bigger?  I won't even use my /home directory, I'll just use an external disk for my personal storage.

---

