---
title: "Triple-boot: partition advice"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by randell6564 on 2007-11-04
hello again!
I'm getting ready to hopefully end up with a triple-boot scenario.  I have a 120G IDE master that I want to split in order to house Ubuntu 7.10 and WindowsXP while keeping my exsisting Ubuntu 7.04 on my 20G IDE Slave.
My question is how to partition Ubuntu 7.10 in order to get the best results.  In other words, how many partitions would be ideal for Ubuntu, how much space should I give to each etc...
Thanks!

---

### Post by jerrylamos on 2007-11-04
Well, I defragged XP and then set the paging space to zero and defragged again, resized the XP partition down to leave room for Ubuntu following.  After a  couple bruises I use stand alone live CD for partition resizing and creating.  Watch carefully for XP storing files way out in its partition - XP seems to use "scatter" file allocation.

I have a triple boot and also a quad boot.  I usually use about 20 GB for an Ubuntu, unless I'm doing a bunch of iso image downloads (of the next Ubuntu) then I use 30 GB.  I use only one swap space for the triple and for the quad since whichever Ubuntu is booted will use the same one.  If I just want to play around with the Ubuntu then 10 GB will do.

With three Ubuntu's on the same system, every time I install it changes the UUID of the install partition, then I have to edit the /etc/fstab on each of the others so they will boot....

If you plan on using a bunch of GB for applications, allow for that.  

Jerry

p.s. yes, after doing the partitions, rebooted XP and gave it a comfortable paging size.

---

