---
title: "Error when installing ubuntu"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by Jacques Kleynhans on 2008-03-03
I get this error over and over i dont know what to do any more.

The ext3 file sysytem creation in partition #1 of SCS|1 (0,0,0) (sda) failed.

Pls help i realy want to give this a try

---

### Post by taurus on 2008-03-03
Are you trying to install Gutsy?  Is it x86 or x86_64?  Can you post the output of this command from a terminal while you are running from the LiveCD?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Jacques Kleynhans on 2008-03-03
No its not gutsy im doing a wireless projects which i needed a modded copy of xubuntu and now problems. 

When i type sudo fdisk -1 

message 

invalid option

the cd i got from 5 second fuse web page it should be for 32 bit

---

### Post by taurus on 2008-03-03
That should be lower case letter L, not number 1.

---

### Post by Jacques Kleynhans on 2008-03-03
hmmm my bad i quite noob still ok i can see my diffrent boot sectors.

---

### Post by Jacques Kleynhans on 2008-03-03
When i format the drive can i just make one big root directory and a swap file??
What will happen

---

### Post by taurus on 2008-03-03
You can format the drive as one partition and tell the installer to use the whole drive.  It would know what to do from there.  However, if you partition your drive to / and swap, then you need to pick the Manual when you get to the partition screen and tell the installer to use which partition as /.  I don't even think you have to tell it which one is swap because it should know but in case it doesn't, just point to it.

---

### Post by Jacques Kleynhans on 2008-03-03
Thanks alot it seems to work, i did the manual thing. The weird thing is when i use a normal ubuntu cd which mark shut send me hehe i just click on use whole drive no problems and it installs but this one has bells and whisles. But thanks again

---

