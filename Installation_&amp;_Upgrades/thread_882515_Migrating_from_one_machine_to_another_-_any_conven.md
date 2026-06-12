---
title: "Migrating from one machine to another - any convenient way?"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by Versusnja on 2008-08-07
Hi!

I'm running an Ubuntu Hardy server.
LAMP + samba + proftpd + mailserver + some other stuff

Is there any convenient way to migrate from one server to another more powerfull machine?

Can I simply put a HDD into another box?

I will appreciate any bit of information.

---

### Post by dileepm on 2008-08-07
Of course you can but make sure of the hardware compatibility of both(old and new) boxes are same...Because you may experience problems with installed software/drivers...And also hardware plaforms like i386 and amd must be same...

---

### Post by cdtech on 2008-08-07
You can use the dd command to transfer the image. here is a link on how to do the command:
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by Versusnja on 2008-08-07
Thanks a lot. This is VERy helpful and exactly what I need.

But what I'm worried about is shouldn't I recompile kernel or do something additional hardware configuration for image to work on a new machine?

Do you think this will work "out of the box"?

---

### Post by cdtech on 2008-08-07
The only thing you will need to change are your block id's on the new system. I would remove the block id's used in your fstab file and use the standard /dev/sd? configuration until you can boot off of the new system and then update them. You can find the block id using "blkid" on the new system.

---

