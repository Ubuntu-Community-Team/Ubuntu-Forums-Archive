---
title: "/home not mounted"
date: 2008-08-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by aamukahvi on 2008-08-21
Hi,

I have a weird problem. It took me a while to figure out what is going on.

Sometimes when in gdm, trying to log in I get a message that my home folder could not be found (i.e. /home is not mounted). Dropping to the shell I confirmed that this was indeed the case. I then tried to mount it manually, but it said the volume was busy. Busy?

Indeed, the HDD led was flashing wildly. 'top' confirmed that
```
fsck.ext3 /dev/sda2 
``` was running.

So what was happening is that gdm would be loaded while fsck was still running, leading to /home not being mounted. Waiting about 13 minutes, manually mounting /home and restarting gdm I could login to my desktop. Rebooting is easier though.

I cannot imagine why the usual fsck message is not being displayed. Ideas?

---

### Post by SorryGoFish on 2008-08-21
It sounds like your services are starting in the wrong order. There may be some debian way to reconfigure something to make it run at the right time. I'd search for that. Keywords like "service start order ubuntu" ??

In the mean time, you can check out /etc/rc3.d which contains ordered symbolic links to the scripts in /etc/init.d (3 is the default run-level). 

I think there's a GUI for tweaking services in Gnome and KDE, maybe they have the ability to control order. Have you played with these before?

Anyway, you can rename the symbolic links to re-order them manually. I would try to avoid this, but if your searches don't lead you to anything more useful than this suggestion, that's what I'd resort to. I believe lower numbers run first. 

Please post back here if you find something better.

---

### Post by SorryGoFish on 2008-08-21
Or maybe you can just re-order the lines in /etc/fstab so that home gets mounted before /

---

### Post by ronacc on 2008-08-21
isn't it normal for gdm to wait to start until fsck has completed ?

---

### Post by aamukahvi on 2008-08-21
> **ronacc said:**
> isn't it normal for gdm to wait to start until fsck has completed ?
Yeah it's supposed to show that usplash screen "Routine fs check, press esc to skip" or something.

I found
/etc/rcS.d/S30checkfs.sh
/etc/rc2.d/S30gdm
/etc/rc3.d/S30gdm
/etc/rc4.d/S30gdm
/etc/rc5.d/S30gdm

If I remember correctly, rcS is the one that precedes everything else, so these should be ok, right? For some reason gdm doesn't wait until fsck is done.

My volumes are 
/dev/sda1 / (jfs)
/dev/sda2 /home (ext3)

---

### Post by ronacc on 2008-08-21
see the post by RAOF at the bottom of page 1 of this thread. 
[http://ubuntuforums.org/showthread.php?t=894747](http://ubuntuforums.org/showthread.php?t=894747)
the bugs he references are probably causing this .

---

### Post by FFuser on 2008-08-21
I had the same problem, and I commented on a bug

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/82617](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/82617)

---

### Post by aamukahvi on 2008-08-21
Ok, it seems it will be taken care of in time for alpha5.

---

