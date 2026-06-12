---
title: "installation nightmare"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by darth.k on 2008-03-14
hi

I decided to install ubuntu tonight to run on a dual boot with xp which I have been running for 6 months.

I used Gparted to partition 3 disks.  I left 220gb for xp, 58gb for ubuntu set to ext3 and 1.2gb set as linux swap.

However when I try to install unbuntu 7.1 both live cd and text install do not detect any hard drives!  The live cd dected my hard drive before I partitioned.  Xp is running fine so I'm totally bemused...

Any ideas?  Will I have to reinstall xp to get that 60gb of space back?

thanks

---

### Post by taurus on 2008-03-14
What happens when you run this command from a terminal from the LiveCD?

Applications -> Accessories -> Terminal
```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That would be lower case letter L, not number 1.

---

### Post by darth.k on 2008-03-14
nothing it goes to the next line just

---

### Post by taurus on 2008-03-14
Fire up gparted in System -> Administration and post the screen shoot of that window with your harddrive.

---

### Post by darth.k on 2008-03-14
I am actually posting from a different computer.  I do not have a net connection via linux on the other one.  I can tell you though that when I did this on the live cd  gparted scanned but didn't find any devices.

---

### Post by taurus on 2008-03-14
But didn't you use gparted to resize your harddrive before, ntfs (windows), ext3, and swap?

---

### Post by darth.k on 2008-03-14
yeah but for some reason it is not seeing them from the live cd or text install.  Windows is still running fine so I know that the hard drive isn't crrupt or anything.

---

### Post by darth.k on 2008-03-14
ok I just booted from my gparted cd, 3.4-11

it shows the 3 hard drives.

/dev/sda1          ntfs           total236.68       used 154.8
/dev/sda2          ext3          total60.18         used 1.12
/dev/sda3         linux swap  total 1.23         used   ---

Is this strange that installation isn't seeing them?

edit:: not sure why its saying sda2 has 1.12 used, I havent used it?

---

### Post by froy02 on 2008-03-14
What kind of motherboard and chipset  do you have also is your hard drive SATA?

---

### Post by nhutto on 2008-03-15
i am having the same issue on my little brothers computer and it is running windows and i want to set up linux on a second hard drive that hard drive and the windows one doesn't show up in the live cd grr it is frustrating

---

### Post by bhocay on 2008-03-15
same thing here bro.. but 
diff is..

ive part my drive in 2
1 for win xp and 1 for ubuntu
win xp was my first OS too

but strange happen was Part. Magic cannot detect my hardrive any more after i've installed ubuntu.. 
it was said "Bad Hardrive"
what in the name of Tux happened.. I can't Resize my partition :(

sory 4 the Grammars.. :P

---

### Post by Sef on 2008-03-16
> but strange happen was Part. Magic cannot detect my hardrive any more after i've installed ubuntu..
it was said "Bad Hardrive"
what in the name of Tux happened.. I can't Resize my partition 

Partition Magic and GNU/Linux do not get along well.  It is best to use another partitioning program.

---

### Post by darth.k on 2008-03-16
well i deleted the extra partitions i made but alas ubuntu live cd does not see my hard drive at all...

shame I was looking forward to switching to ubuntu, guess i'll have to stick with xp :(

---

