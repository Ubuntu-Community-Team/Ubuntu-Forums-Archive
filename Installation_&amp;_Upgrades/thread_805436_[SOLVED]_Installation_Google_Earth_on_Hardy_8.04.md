---
title: "[SOLVED] Installation Google Earth on Hardy 8.04"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by DeMus on 2008-05-24
I have installed Google Earth 4.3 from the earth.google.com site.
Installation went well, only starting the program is a bit of a problem:

The launcher on my desktop is owned by root, so when I start it nothing happens. (I am not root)

When I change ownership to me I can start the program and all I get is a dark sky with stars, no earth, no left column.

When I start it by typing "sudo googleearth" in a terminal it works fine.

How to make it start from the launcher to make things a bit easier? How to change the contents of a launcher, I mean which program to start,where to to find it, etc?

DeMus

---

### Post by adityakavoor on 2008-05-24
executable google earth might be in /bin or /usr/bin

---

### Post by Steve413z on 2008-05-24
delete the following folders

~/.config/Google
~/.googleearth

i had the same exact problem (everybody is)

---

### Post by DeMus on 2008-05-24
> **Steve413z said:**
> delete the following folders

~/.config/Google
~/.googleearth

i had the same exact problem (everybody is)

Was this an attempt to help me or to have a laugh? When I delete the ~/.googleearth folder the whole program is gone. Once thing's for sure: then it won't run at all.

DeMus

---

### Post by DeMus on 2008-05-24
> **DeMus said:**
> Was this an attempt to help me or to have a laugh? When I delete the ~/.googleearth folder the whole program is gone. Once thing's for sure: then it won't run at all.

DeMus


After deleting the ~/.googleearth folder I installed the program again, now as root. It is now installed in /opt/googleearth. It does so automatically, no questions asked.
I had to use chown to become owner and now it runs. Strange way of doing things, isn't it?

DeMus

---

### Post by Steve413z on 2008-05-24
> **DeMus said:**
> Was this an attempt to help me or to have a laugh? When I delete the ~/.googleearth folder the whole program is gone. Once thing's for sure: then it won't run at all.

DeMus

usually if you run the google earth installer as sudo, it automatically installs it to /opt/
the ~/.googleearth folder should be only configuration files

---

### Post by Steve413z on 2008-05-24
> **DeMus said:**
> After deleting the ~/.googleearth folder I installed the program again, now as root. It is now installed in /opt/googleearth. It does so automatically, no questions asked.
I had to use chown to become owner and now it runs. Strange way of doing things, isn't it?

DeMus

and usually after deleting those files and running google earth again, the permissions are set correctly the second time

---

