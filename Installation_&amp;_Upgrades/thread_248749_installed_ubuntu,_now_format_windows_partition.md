---
title: "installed ubuntu, now format windows partition"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by bloah on 2006-09-01
hi,

i managed to install ubuntu via windows with instlinux since the cd drive wouldn't work.

now, how do i get rid of the windows partition ?
can i just format it and grub will automatically detect that windows xp is no more ?

thanks in advance...

---

### Post by bloah on 2006-09-04
anybody ?

---

### Post by bloah on 2006-09-11
alright, perhaps this really is a stupid question...

but i don't know it, so could someone pls help me ?

thx...

---

### Post by The_Tankengine on 2006-09-22
Hi.  If you just use gparted or your favorite partitioner, you can just delete the partition.  GRUB *SHOULD* detect that it is no longer there and remove it.  But, if it doesn't, it is very easy to fix.  Just go type this into the terminal ```
sudo nano /boot/grub/menu.lst
``` 
(You can use gedit also, if your not a hardcore hacker like me:rolleyes: ) and remove the references to XP. It will probably look like this - ```
title Windows XP Home
        root (hd0,0)
        blah
        blah.blah
```
Just remove that and you are good to go.

---

### Post by The_Tankengine on 2006-09-22
Now I've got a question for you.  I am having the same problems you were, with the install not recognizing the drive.
After you ran instlinux, did you just pick the 6.06 installer from grub and put the cd in?  Any info is greatly helpful.
Thanks!

---

