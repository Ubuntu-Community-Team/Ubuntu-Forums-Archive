---
title: "Can't re-size XP partition"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by kidob on 2007-06-12
I'm trying to install Feisty with the Alternative installation CD and have been unable to shrink the XP partition. It's a 40 GB drive with 25 GB free. I want to shrink the XP partition to about 20 GB. I defragged twice and still the same problem: after I enter the new partition size of 20 GB (I've also tried larger sizes, up to 27), I get the following message:

"An error occured while writing the changes to the storage devices. The resize operation is aborted."

Don't know what to do :o Is there a way to pre-partition with XP and then install with the free space already available? or any other ideas? Thanks!

-kidob

---

### Post by psiu on 2007-06-12
I haven't tried with any of the Ubuntu discs yet--I have used the Gparted CD for it, and it worked perfectly on both my laptop and my wife's computer.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by hotani on 2007-06-12
mine will not resize either. It does not give an error, just ends with nothing changed.

This is a shiny new Dell optiplex 740. I really don't care about the windows partition so may end up just wiping it out if I don't find a nice fix.

EDIT: Ok, I'm having a "special" moment now. The disk I used was 6.06 and not 7.04. However, it is still disturbing that it would not work. When I did try the partitioning process with the installer, it mucked up the windows partition so now it is just an ubuntu machine. Better that way. :)

---

### Post by jonward0690 on 2007-06-12
Well when I bought my pc from Dell they somehow lock the Win XP partiton where I could not resize it with nothing I tried it all just to make my pc dual boot I had to reinstall Win.

---

### Post by Pumalite on 2007-06-12
> **jonward0690 said:**
> Well when I bought my pc from Dell they somehow lock the Win XP partiton where I could not resize it with nothing I tried it all just to make my pc dual boot I had to reinstall Win.

I ended up TrueImaging XP and packing it in an external drive. Now I have all boxes Linux.

---

### Post by kidob on 2007-06-12
> **jonward0690 said:**
> Well when I bought my pc from Dell they somehow lock the Win XP partiton where I could not resize it with nothing I tried it all just to make my pc dual boot I had to reinstall Win.



You see, this is why I hate Microsoft! :mad:


Now I can't even boot into XP, I'll have to wait till I get home where my Windows CD is. I may just whipe Windows for good myself. The only reasons I hesitate are:

a., I can't use Photoshop w/o Windows and

b., I'm don't know Linux well enough yet to deal with all those issues without a familiar fallback. But this sort of thing gives me an incentive to speed up the learning process! ;)

---

### Post by hotani on 2007-06-12
> **jonward0690 said:**
> Well when I bought my pc from Dell they somehow lock the Win XP partiton where I could not resize it with nothing I tried it all just to make my pc dual boot I had to reinstall Win.

Wow, that must be what it was. I suppose the 7.04 disk would not have worked either. :(

---

### Post by kidob on 2007-06-12
> **jonward0690 said:**
> Well when I bought my pc from Dell they somehow lock the Win XP partiton where I could not resize it with nothing I tried it all just to make my pc dual boot I had to reinstall Win.


Come to think of it, when I was defragging I noticed there were two blocks of "unmovable files", one at the very beginning of the disk and one a little over halfway in. Since partitions have to be continuous, maybe these unmoveable files prevent you from freeing up enough space to creat a new partition. My computer's a Gateway btw. Maybe I'll just have to wipe Windows, install Ubuntu as primary, then reainstall Windows in a paltry little 10 GB block at the end! :D

---

### Post by merlinus on 2007-06-12
Windows wants to be in the first partition.  Use gparted live cd to do your partitioning, and save the first for your windows re-install.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

