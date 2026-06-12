---
title: "Grub error"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by eric.reynolds on 2010-12-17
I set up a dual-boot system with Vista and Kubuntu.  The system configured Grub with:

Windows Recovery Environment /dev/sda2

Windows Vista (loader) /dev/sda1  




The entries above are backwards.  The correct entries are:

/dev/sda2 loads Vista

/dev/sda1 is Vista recovery

---

### Post by sikander3786 on 2010-12-17
Yes that seems to happen too often. Don't know why.

You can edit and correct the titles following this thread.

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
courtesy of forum member *drs305*

---

### Post by oldfred on 2010-12-17
I use drs305's instructions for a lot of grub issues. And he has useful info in several different posts on grub2.

But for your type of problem I just brute force new entries into 40_custom and edit them. Then turn off osprober. Details on how some of all this works together is in drs305's posts.

Specifically.

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom
Then do (after any change to grub you have to do this):
sudo update-grub

All you should change is titles but, Test that then new entries work, they will be below your current entires, then:

In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true

sudo update-grub

---

### Post by eric.reynolds on 2010-12-17
Thanks folks.  

I can't help but wonder if Ubuntu is going in the wrong direction.  Grub2 looks like it's become unnecessarily complex.

Is there any benefit to v2?

---

