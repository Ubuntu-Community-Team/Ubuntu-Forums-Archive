---
title: "Need help auto mounting hdb1 on start up"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by buckweat420 on 2007-02-06
First off I would like to say hello to all the ubuntu users out there....and I need your help. I have a server i am setting up that has 2 hard drives. 40GB(Master) Hard Drive and a 320GB(Slave) When i do a "fdisk -l" it shows "/dev/hdb1" Which is the 320 and I can mount it using "mount /dev/hdb1 /mnt/hdb". The 320GB Drive is using file system "reiserfs". But i can not figure out how to mount automatically on reboot using fstab. Does anyone know how to do this or are there any other ways to mount this drive. I googled and found a few things and i herd that maybe a script can do it? 

Thanks For Reading,
Chad

---

### Post by WW on 2007-02-06
Add this line to /etc/fstab
> /dev/hdb1  /mnt/hdb reiserfs defaults 0 2

---

### Post by buckweat420 on 2007-02-06
WW you are a god among men.

---

