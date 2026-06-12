---
title: "installing multiple distros"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by edroid on 2008-02-12
I have an old 500MHz PIII with 500MB RAM, with 20GB and a 6GB HD's.  I
want to set-up this system as a test-bed of ubuntu distro's.  Would the
following partitioning scheme allow for installing version 7.10 of
xubuntu, ubuntu and kubuntu without confusing grub?

Filesystem            Size  Used Avail Use% Mounted on   Distrubution
---------------------------------------------------------------------------------
/dev/hda1             4.0G  1.9G  1.9G  51% /                      (xubuntu 7.10)
/dev/hda2             4.0G  2.1G  1.8G  55% /media/hda3    ( ubuntu 7.10)
/dev/hda3             4.0G  2.3G  1.6G  60% /media/hda4    (kubuntu 7.10)
/dev/hdb1             1.0G   n/a    n/a    n/a    swap
/dev/hdb2             100M  52M   48M  52% /boot
/dev/hdb3             2.0G  73M   1.9G   4%  /home

swap, /boot and /home will be shared by all distros.

If you think this would work, is it as straight-forward as I hope, or
are there pitfalls I need to be aware of?

edroid

---

### Post by jan quark on 2008-02-12
do you have considered the idea to install only ubuntu

and then to install the xubuntu-desktop and kubuntu-desktop 

and to change the session during the login to kde (kubuntu) or xcfe (xubuntu) or gnome (ubuntu)  to test them ?

---

### Post by DavidTangye on 2008-02-12
Jan Quarks suggestion has merit.

Plus...

What you are suggesting will not work. You cannot share a single home/YourCommonUsername like that, because each system will overwrite application, window and utility settings in common .hidden directories within /home/YourCommonUsername, creating a mess of apps that will give all sorts of odd problems. Instead do this:

Have /home/UsernameCommonOrNot within each installation/system/partition.
Automount /dev/hdb3 as /mnt/SharedStuff, in /etc/fstab of each system.
Link to it from each home/Username. Keep your stuff in there.

I found problems attempting to share /boot too. Dont bother, its not worth the trouble. There is almost nothing to be gained. Common kernels and boot images save little, as they are very small anyway compared to everything else that gets installed.

---

### Post by Pumalite on 2008-02-12
Delete.

---

### Post by edroid on 2008-02-13
Thanks jan quark!   I am going to try that.

---

