---
title: "your installation cd rom couldn't be mounted"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by bcntu on 2006-09-08
I've found this problem when trying to install Ubuntu Server 6.06.

the CD boots fine, and I go through some previous LAMP installation steps, such as chosing keyboard and location, until i get this
"your installation cd rom couldn't be mounted"

I've seen some other people have had this problem and the solutions they report are:
- set linux pci=off (continued getting inst problems at some further step)
- set linux ide=nodma (continued getting inst problems at some further step)
- change the CD ROM drive (worked fine but, come on, is that THE solution? )

Of course, none of these seems acceptable, as it shouldn't be that hard to mount something as common as a CD drive. Can anyone provide any help on this issue?

The HD contains a previous installation of win 2003 server, to be completely erased. I'm assuming that should give no problems, is it so?

---

### Post by wpshooter on 2006-09-08
Is it possible that your CD drive just needs a good cleaning ?

---

### Post by bcntu on 2006-09-12
I finally succeeded in mounting the CD-ROM.

what worked for me was related to the ide=nodma solution posted before, in my case:

hdparm -d0 /dev/cdroms/cdrom0,

which turned dma OFF. 
After this, I retried mounting and it mounted just fine.

---

