---
title: "Trying to dual boot ubuntu onto current xp.. problem?"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by jamienos on 2007-03-06
I'v been trying out the livecd and decided to install it, so i use the first option in the installer ( Resize IDE master partition #1 (hda1) and use freed space) but it come's up with a error along the line's of 'cannot find needed space for installation) no matter what i choose in the partition scroller

I'm useing about 30 gig harddrive, and have around 22g of that free is this not enough? would i be best off just chooseing the erase option and forget about xp?

the only real reason i want it is just incase i mess up ubuntu, plus i like to have photoshop and a few other programs i know cant be used on linux


Edit: and beside's i havent fully installed it yet - useing the cd the screen is off balance and the trashcan and poweroff button is nudged off screen and on the other side theres a black line going down any ideas on that?

thanks

---

### Post by chewearn on 2007-03-06
> **jamienos said:**
> I'v been trying out the livecd and decided to install it, so i use the first option in the installer ( Resize IDE master partition #1 (hda1) and use freed space) but it come's up with a error along the line's of 'cannot find needed space for installation) no matter what i choose in the partition scroller

You could manually resize your XP partition, leaving a large empty space on your harddisk.  Then choose option 2, which is install ubuntu on the largest continuous space.

> Edit: and beside's i havent fully installed it yet - useing the cd the screen is off balance and the trashcan and poweroff button is nudged off screen and on the other side theres a black line going down any ideas on that?Seems like you are using CRT monitor?  Then, its simply because you have the VGA at a different frame frequency (when you are in XP), than the default used by ubuntu LiveCD.  Most modern CRT monitor should be able to keep separate horizontal shift settings for different scan rate.  So, it is simply a matter of changing the horizontal shift from the monitor setup.

---

### Post by jamienos on 2007-03-06
> **AstalaVista said:**
> You could manually resize your XP partition, leaving a large empty space on your harddisk.  Then choose option 2, which is install ubuntu on the largest continuous space.

Seems like you are using CRT monitor?  Then, its simply because you have the VGA at a different frame frequency (when you are in XP), than the default used by ubuntu LiveCD.  Most modern CRT monitor should be able to keep separate horizontal shift settings for different scan rate.  So, it is simply a matter of changing the horizontal shift from the monitor setup.

I'm useing a LCD monitor (Belinea)


I will go and try do it manually and see how i get on. thanks :)

---

### Post by chewearn on 2007-03-06
LCD monitor should have an auto-adjustment button, but only for VGA; if you are using DVI, then I don't know what's wrong.:(

---

### Post by jamienos on 2007-03-06
tryied it.. no luck manually trying it just says something like cannot resize /dev/hda1 and when i make new partritions and the swap etc they just end up being named like 'new partrition \1' while on other peoples screenshots of it its like dev/hda5 and such.. i dont know

i feel like just tossing the cd right now.. this should of been installed in a hour

---

### Post by confused57 on 2007-03-06
> **jamienos said:**
> tryied it.. no luck manually trying it just says something like cannot resize /dev/hda1 and when i make new partritions and the swap etc they just end up being named like 'new partrition \1' while on other peoples screenshots of it its like dev/hda5 and such.. i dont know

i feel like just tossing the cd right now.. this should of been installed in a hour
Did you defrag your XP before trying to resize?  If not, you probably should run defrag a couple of times to get files to the front of the partition.

---

### Post by jamienos on 2007-03-06
> **confused57 said:**
> Did you defrag your XP before trying to resize?  If not, you probably should run defrag a couple of times to get files to the front of the partition.


defragged two times, first time it failed at 35%

---

### Post by confused57 on 2007-03-06
You could try resizing your XP partition with the gparted live cd:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

It's only a 30 mb download, it's a later version of gparted than the Ubuntu live cd and does a better job with resizing XP filesystem...worth a shot, may or may not work.

---

### Post by jamienos on 2007-03-06
i may just use the erase/format option to install and get rid of windows.. nothing seems to be working for me and if that doesent work.. then well im screwed.

---

### Post by jamienos on 2007-03-06
i just used the erase option go tget rid of xp and install ubuntu, all went fine

i put the topic as solved, even tho my specific problem wasent done because i decided to just foget a dual boot.

thanks everyone

---

