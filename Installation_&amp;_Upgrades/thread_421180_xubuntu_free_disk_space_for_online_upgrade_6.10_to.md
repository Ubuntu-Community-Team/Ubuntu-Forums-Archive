---
title: "xubuntu free disk space for online upgrade: 6.10 to 7.04"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by alpage2 on 2007-04-24
I am running xubuntu 6.10 on an old laptop, with about 1.5GB of free disk space.

Is this enough to do the online upgrade to 7.04?  What would be the absolute minimum?

Can I delete any unnecessary package directories if I need to recover some disk space, after the upgrade? And which ones?

Thanks in anticipation
Alan

---

### Post by dannyboy79 on 2007-04-24
do a 

man aptitude

to see that you can use 

sudo aptitude clean
or
sudo aptitude autoclean

and this will clean out a bunch of unneeded packages. Also clean out your apt cache. i would think that 1.5 would be enough but just in case, can you backup your install using tar to an external device as a fail safe if during the upgrade it gets full. this way you can reformat your drive, and simply un tar the tar you made onto your partition. don't forget to backup your mbr as well. i have used to tar to backup my entire Xubuntu install. I did it thru Puppy livecd. i mean you can pretty much use any livecd that has tar. then you just mount your xubuntu install and then also mount the external device (usb drive, etc).

The tar option is just a fail safe as I can't tell you how much the min install requires. does it say anywhere on the internet hwo much Fesity Xubuntu uses? good luck.

---

### Post by alpage2 on 2007-04-25
Thanks dannyboy79 for those very useful tips. I'll get started.

Alan

---

### Post by dougleduck on 2007-04-28
Same question but I've only 544MB on my linux partitition. I've got more storage elsewhere but doubt this will do.If it could be a problem ill just wait until ive got time for a clean install.

---

### Post by dannyboy79 on 2007-04-30
544 isn't even large enough for xubuntu! the iso image is larger than that. You're going to need a minimum of 1.5, I think??

---

