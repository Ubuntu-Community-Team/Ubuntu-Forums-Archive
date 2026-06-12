---
title: "GreenHorn here, need to resize my boot partition ?"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by jbg123 on 2008-03-28
Ok what's up peoples of freeware land !  First of all I'm about new as new can be to Linux in general but I'm self studying for the LPIC Jr sys Admin exam and I've been reading a lot.  I installed Ubuntu on this older box and it's got 2.4Ghz processor and a 40gb HD but the 1.8Gb boot partition is at 100%, so it crawls and take minutes for things to open, the mouse to catch up to movements, etc, you get the picture.  How do I fix this ?  Is there an inherent utility within Ubuntu already I have and don't know about or do I need something like Gparted to install and then try to increase the size, and what should I increase it too ?  Thanks a ton guys, learn something new everyday right !  Later,, jon

---

### Post by buntu_Geek on 2008-03-28
Yeah!!!.. you can resize the partition.. provided you have unallocated space below your partition....

You can do great things with System-->Administrator-->Partition Editor ... this is nothing but GParted...

btw... here are some prelminaries...
You have to unmount the partition before deleting it..

Note: Playing with GParted== Data Loss.. :D

If you have any doubts or probs with GPart.. Post here....

---

### Post by jbg123 on 2008-03-28
ok cool man let me try and wake this thing up and see what I get, thanks buddy.

---

### Post by jbg123 on 2008-03-28
is that under the menu options up top, did you mean System Monitor ?  sorry im retarded man !

---

### Post by buntu_Geek on 2008-03-28
No... If you dont have "Partition Editor" Option in the System--> Administrator menu... then... you dont have gparted installed,,

So apt-get it down to your sys...

```

sudo apt-get install gparted

```

If it is says that gparted is the latest install then... You have to check... System--> Preferences-->Main Menu ...to check the Partition Editor..

---

### Post by forestpixie on 2008-03-28
The partition editor is in the livecd - boot that and run it from there - in system >admin menu - you can't run the partition editor on a mounted partition.

Or get a copy of the livecd - gparted or parted magic [http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads)

---

### Post by jbg123 on 2008-03-28
ok I'll give it a shot man, stay tuned~  haha  :popcorn:

---

### Post by jbg123 on 2008-03-28
ok Pixie, link no worky ?  I'm loading the LiveCD now

---

### Post by jbg123 on 2008-03-28
ok got the liveCD booted up and I'm in Gparted, should I remove the /dev/sda1 partition completely first or use Move/Resize and double or triple it's used space, from the 1.8Gb that's crawling to say 5 or 6Gb?

---

### Post by forestpixie on 2008-03-28
The link works here? Th eorder to do this is 

gain space by resizing one partition
add space to the boot partition 

If you're not sure which is which - either post a scrnshot - and please use the attach button in 'Post Reply' or open a terminal and do

```
sudo fdisk -l
```

---

### Post by jbg123 on 2008-03-28
ok well Im about to find out if what I did worked, I opened up the Partitiion editor and increased the space to double the original size and seems like it's working a little faster no doubt but maybe I should add more room and have it even better. I'll see, Im trying to recover my first Base attempt but its doing the recovery now !   lol

---

### Post by jbg123 on 2008-03-28
ok I hstill had some jump mouse action so I increased it again to 6.8GB so I hope that will do the trick, it's not on a network or connected to the internet so I 'd have to dump a shot, put it to USB, then load it here,. it's my last resort ok !

---

