---
title: "Wubi Upgrade 10.10 to 11.04 Compiz Issues"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by Derspankster on 2012-01-17
I recently did an upgrade of a wubi installation on one of my boxes from 10.10 to 11.04.  After the upgrade the machine tried to boot into Unity (which is default) but failed and left me with a desktop with no panels. I was able to alt f2 to create a launcher for Terminal.  I tried compiz --replace to try to enable metacity and panels to no avail.  

I then tried simply gnome-panel and got panels, logged out and then back in to Ubuntu Classic with no effects.

Try as I might, compiz will not run correctly. If enabled I have no controls on any windows. I am running the correct driver for my video card. I have updated, upgraded with and without -f and reinstalled compiz but nothing works. Can't find any "broken" files in Synaptic. 

The system runs just fine with metacity. Not the end of the world, just a bit aggravating.  Thoughts anyone?

---

### Post by Derspankster on 2012-01-18
Bump1***

---

### Post by Derspankster on 2012-01-19
Bump once more**

---

### Post by dino99 on 2012-01-19
i only do real install:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

wubi is not designed to be used , just to let you know what ubuntu is.

---

### Post by Derspankster on 2012-01-19
> **dino99 said:**
> i only do real install:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

wubi is not designed to be used , just to let you know what ubuntu is.
There may be some language issues involved here but I am a long time Ubuntu and linux user.  One particular machine that I've administered has a wubi install.  Unfortunately nothing your have said nor any of the links you provided have anything to do with this issue. 

I do appreciate the time you took to respond, however.

---

### Post by bcbc on 2012-01-20
Maybe this will help: [http://ubuntuforums.org/showthread.php?t=1801279](http://ubuntuforums.org/showthread.php?t=1801279)

If you had a custom video driver you might need to reinstall it (I've read somewhere that this might be required after upgrading).

---

### Post by mastablasta on 2012-01-20
yes that is correct and you also need to remove the old version first.

---

### Post by Derspankster on 2012-01-20
Thanks to both of you. I'll give it a shot. I've tried to talk the user into a dual boot (she still uses Windows too) to no avail. Perhaps this experience will win her over to my thinking.

---

### Post by Gstrazds on 2012-01-26
Hi there.. I posted on this previously.. 

At the login screen at the bottom switch to Ubuntu classic, or other version - no effects..will get your system aback..

If you want new ubuntu back - put the compiz incon on your classic desktop - logout relogin to new ubuntu fire up compiz  reset to default - explained in previous postings by me.

Good luck

---

