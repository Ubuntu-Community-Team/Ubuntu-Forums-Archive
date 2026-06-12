---
title: "installing ubuntu..anyone with knowledge of partition can help"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by thousandpimps on 2007-12-05
ok this is my problem...i have been using Ubuntu for few months now and i love it and i don't want to use anything else ...but in the past 3 experimental months i have installed a lotta things and messed around with it....so now i know what i want on my system and i want a fresh new install...and then ill put whatever i want ...

i just want to know how could i partition my hard drive so i can save like my music that i downloaded or my documents...so after i install Ubuntu i can copy it on Ubuntu hard drive again..because my music is like 7 to 10 GB and i don't want to download it again...
thanks a lot guys

---

### Post by elite_angel on 2007-12-05
I suggest that you should just save all your mp3 files to a DVD, or even in an external HDD, before having your fresh install. At least, you already have your files at hand for safety.

---

### Post by thousandpimps on 2007-12-05
thats true that would be easy but i don't have a dvd burner or an external hdd...maybe i do but i have to look for it...if i could save it to a different partition and copy it after it would be easier i think

---

### Post by elite_angel on 2007-12-05
As you said, you don't know how to partition a HDD, then I'm sure you just keep on clicking the install wizard of the ubuntu installer, until it is done.

The default install will be using the entire HDD, so you don't have any space for you to make it.

I think, my suggestion above will be the best solution.

---

### Post by thousandpimps on 2007-12-05
yea but i want to know how to save it to a different partition ...or if thats not possible...cuz i dont have a dvd burner and i dont know where my other hard disk is...so that is the only option i have

---

### Post by logos34 on 2007-12-05
You could transfer your /home folder to [a separate /home partition]("http://www.psychocats.net/ubuntu/separatehome") (which by the way is the ideal setup)...all your files will then be safe and you can reinstall over the existing root partition (just be careful during install--you want a indicate the new home mountpoint as '/home' but DO NOT format, only format the root and swap.

Note: i did just this a few days ago and I recommend you also use gnome-reset to save your nautilus and various panel settings, bookmarks, etc...mine got lost in the transfer and I forgot to use gnome-reset (no biggie but I wish I still had some of my file notes and emblems).

---

