---
title: "Problem after recent kernel update"
date: 2014-11-27
forum: Installation &amp; Upgrades
---

### Post by bjorn-lisper on 2014-11-27
Hi all,

I run Xubuntu 12.04 on an old desktop. Yesterday (Nov 26) I received an update of the kernel trough the update manager, and I installed it. However, after rebooting I now have a problem. First the machine seems to boot allright, and the Xubuntu startup screen shows, but then it bails out and I get a black screen with a login prompt. The machine will however not take any keyboard input at this prompt.

Otherwise it seems to run as it should. I can login via ssh from a remote computer, and run different commands and applications on the machine from there.

I might have screwed something up during the update. I went away for some time after having started the update, when I came back I had been prompted for authentication, and after authentication a window appeared saying that the installation of the update was waiting for something. After a few minutes I pressed "cancel", and was returned to the update manager that seemed done with the update. I wonder whether I might have interrupted the installation of someting important?

Some more info that might be relevant. uname -r says that I'm running  3.2.0-70-generic. This kernel version was installed Sep 24 on my system, in /boot I have this:

-rw------- 1 root root  4885632 sep 24 22:53 vmlinuz-3.2.0-70-generic

However, there is a newer version of the kernel there, that I apparently have been using for some time without problems:

-rw------- 1 root root  4884960 nov  6 16:30 vmlinuz-3.2.0-72-generic

During my update attempt, these files seem to have been written into /boot:

-rw-r--r-- 1 root root        0 nov 26 10:00 initrd.img-3.2.0-72-generic.new
drwxr-xr-x 3 root root    12288 nov 26 10:00 grub/
-rw-r--r-- 1 root root 14181419 nov 26 10:00 initrd.img-3.2.0-72-generic

In /boot/grub, the following files have been written:

-rw-r--r-- 1 root root    1024 nov 26 10:02 grubenv
-r-------- 1 root root    2527 nov 26 10:00 grub.cfg.new

I use the standard graphics driver (no Nvidia stuff). It's Xubuntu 12.04 right out of the box.

Any help is appreciated!

Björn

---

### Post by mörgæs on 2014-11-27
An interrupted kernel upgrade can get messy and you might need to invest many hours cleaning it up.

As 12.04 has less than half a year of support left are you sure it's worth the effort?

---

### Post by bjorn-lisper on 2014-11-28
Is there no simple way way to roll back the failed update and redo it? The alternative is to reinstall from scratch, but I would be happy not having to do that. For various reasons I need to run 12.04 for still some time on this machine.

Björn

---

### Post by mörgæs on 2014-11-30
I don't know of a roll back.

Why do you need 12.04? If 14.04 has a problem then it's better to try to solve that than sticking to an old release. 

Please be specific. People can't help you based upon a post mentioning 'various reasons' - as you can see there's not much activity here.

---

