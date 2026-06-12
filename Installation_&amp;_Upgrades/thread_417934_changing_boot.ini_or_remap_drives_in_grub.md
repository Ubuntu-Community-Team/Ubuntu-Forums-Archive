---
title: "changing boot.ini or remap drives in grub?"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by fokuslee on 2007-04-22
This is the scenario 
I install winXP on a box with only one harddrive.   ofcourse the boot.ini will contain this line 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn /usepmtimer
rdisk(0) b/c the only harddrive is the primary (master) drive
now i put in an additional harddrive  and set the winxp harddrive as secondary (slave) and i install linux on the newly put in harddrive (master).
ofcourse linux boots fine but windows will not boot
so i have to remap the drives 
with such an entry
title winxp
rootnoverify (hd1,0) 
map (hd1) (hd0)
map (hd0) (hd1) 
savedefault
makeactive 
chainloader +1 

so now windows still think its the primary drive and boots OK 

Here Is My Question 
if i leave grub alone meaning no remapping 
but instead change boot.ini in windows from rdisk(0)partition(1) to  rdisk(1)partition(1) will that work too?

---

