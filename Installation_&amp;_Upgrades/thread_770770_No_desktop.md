---
title: "No desktop"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by darco on 2008-04-27
My ancient pc froze up in the middle of the last major upgrade. On reboot it takes me to a blank desktop. Anyone can tell me what I need to do to recover I would much appreciate it....thxs
darco

---

### Post by Pumalite on 2008-04-27
How much memory do you have? What were you running before?

---

### Post by darco on 2008-04-27
I have 1 gig memory (not sure what this has to do w/anything)...I was updating my system when it froze up. On reboot it allows me to enter my login/pw but then it just takes me to a blank desktop...
thxs
darco

---

### Post by Pumalite on 2008-04-27
Update or upgrade? And what is your actual OS?

---

### Post by darco on 2008-04-27
It was an update of HH....it was that last major update from 2-3 weeks ago?

thxs


**EDIT** just booted it up...since I have it on auto login, it goes right to the blank desktop. Doing a crtl+del+bkspace allows me to enter my login/pw but it just goes back to a blank desktop...

---

### Post by Pumalite on 2008-04-27
Maybe they changed your kernel. If you have another OS that owns the Grub, that menu.lst still holds the previous kernel, which at this point does not have a video driver. If that is the case, you have to edit the menu.lst that owns the Grub and change the kernel to the present one.

---

### Post by darco on 2008-04-27
I just effed up my system...I ran the sudo apt-get -f update thinking I needed to finish the install, it did d/l some updates but now on reboot I get a kernel panic,,,not syncing VFS unable to mount root fs on unknown block (0,0)
darco

*edit* I was able to drop down to the previous kernel (.14) and no longer get the kernel panic but still a blank desktop....No other OS's present.

---

