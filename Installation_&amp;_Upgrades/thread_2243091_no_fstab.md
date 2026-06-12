---
title: "no fstab"
date: 2014-09-06
forum: Installation &amp; Upgrades
---

### Post by Thomas_E._Haynes on 2014-09-06
Greetings...

I had a user count before, but this is my first time to log in with the Ubuntu One login.

I have a fresh install of 14.04 LTS on a Chromebook. I have upgraded this with an SSD, and I wanted to adjust a few of the settings in fstab for the SSD. 

# UNCONFIGURED FSTAB FOR BASE SYSTEM

is all I have in /etc/fstab

Thanks...   Tom

---

### Post by Vladlenin5000 on 2014-09-06
> **Thomas_E._Haynes said:**
> I have a fresh install of 14.04 LTS on a Chromebook. 

Depending on how you installed it it may not have the same elements one would expect in a normal installation.

---

### Post by Thomas_E._Haynes on 2014-09-06
I think it was a standard network install via a script at Chrubuntu. Initial searches on the web seemed to indicate other folks were getting the same empty fstab, and it was not just a Chrubuntu thing. 

My last install was 12.04 LTS, and it had a standard fstab.

---

### Post by sisco311 on 2014-09-07
> **Thomas_E._Haynes said:**
> Greetings...

I had a user count before, but this is my first time to log in with the Ubuntu One login.


Please check out: [http://ubuntuforums.org/showthread.php?t=2230004](http://ubuntuforums.org/showthread.php?t=2230004)
If you want to get access to your old account, then start a thread in the  [Resolution Centre]("http://ubuntuforums.org/forumdisplay.php?f=123").

> **Thomas_E._Haynes said:**
> 
I have a fresh install of 14.04 LTS on a Chromebook. I have upgraded this with an SSD, and I wanted to adjust a few of the settings in fstab for the SSD. 

# UNCONFIGURED FSTAB FOR BASE SYSTEM

is all I have in /etc/fstab

Thanks...   Tom

Not sure what is your question? Do you need help with adding an fstab entry for the partition(s) on the SSD?

Upstart's mountall daemon uses both /etc/fstab and its own fstab file /lib/init/fstab to mount your filesystems during boot.

  /lib/init/fstab contains the filesystems that are always mounted on boot, like root `/' and the virtual filesystems. But you can still use /etc/fstab to override the entries from /lib/init/fstab or add your own ones.

---

### Post by Thomas_E._Haynes on 2014-09-07
I would like to have an fstab file I can edit. I will take a look at /lib/init/fstab to see if I can copy contents to /etc/fstab...

---

