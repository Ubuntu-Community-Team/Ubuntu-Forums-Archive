---
title: "I really don't know what to do now."
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-08-20
I have written to the forum today and got very very good help

[http://ubuntuforums.org/showthread.php?t=895303](http://ubuntuforums.org/showthread.php?t=895303)
but the problem is now when I closed my computer then start it I can not get in to the Ubuntu desktop graphic, I am send direct to desktop loggin, in windows term in like dos prompt.
I have tried all I know wihtout any succes. i am able to loggin through desktop login, but no graphical interface.
I get the following errors
chroot : cannot excute  /bin/load_poliy :no such file or directory
mount: Mounting none on /selinux failed : no such device
chroot: cannot excute /bin/restorecom: no such file or directory

---

### Post by kaboodle_fish on 2008-08-20
Have you tried "startx"  (without the quotes) ?

---

### Post by hoboy on 2008-08-20
> **kaboodle_fish said:**
> Have you tried "startx"  (without the quotes) ?

I have just execute startx 
the result is /etc/x11/x is not excutable
giving up

---

### Post by kaboodle_fish on 2008-08-20
No need to give up 
 
I think that means there is something wrong with your xorg.conf 
 
Someone with more knowledge than me will be able to fix that for you I am sure

---

### Post by manishtech on 2008-08-20
Can you post the contents of **/etc/X11/xorg.conf** file
One way to read it is **nano /etc/X11/xorg.conf**

Or copy it on your flash drive using the command
**cp /etc/X11/xorg.conf /dev/sdb1**

if the drive is not mounted itself, you need to mount it also
[B]sudo mkdir /media/FLASHDRIVE

sudo mount -v /dev/sdb1 /media/FLASHDRIVE[/B]

---

### Post by hoboy on 2008-08-20
Thanks everybody for your input,
I have reformat my ubuntu installation, reinstalled it from scratch.
I will start to install vista.
tks.

---

