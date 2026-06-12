---
title: "not enough space error  upgrading to 7.04 but I've 1.2GB ?"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by alanmzifa on 2007-04-20
Hi, as the title says I get a warning going through the upgrade process that says I need to free up 41Mb on /usr and suggests I clear deleted items folder. (which is empty).

My / partition has 1.2GB free. Can someone suggest what steps I could/should take or is this a software bug in the upgrade process?

I have to do an upgrade rather than fresh install as the laptop has no CD drive. Went from 6.06 to 6.10 last night but keep getting this error when I try to upgrade.

thanks in advance

---

### Post by Jussi Kukkonen on 2007-04-20
The install may require a *lot* of space...  Some things you could try:
* run *sudo apt-get  clean* to get rid of unneeded package files
* Are there any applications (not part of default ubuntu-desktop) you could remove temporarily? 
* take a look at how much stuff is in /tmp, remove if needed

---

### Post by alanmzifa on 2007-04-20
I'd already ran the clean command. I went into synaptic and marked some items for removal and that seems to have done the trick.

It's just started to download, so 20 minutes plus installation time and I'll know if all has been a success.


Can I ask one more question? I want to avoid this cramped space causing this again at next update.
[I][B]
 How can I resize the partitions (I've no CD drive, laptop BIOs can't be set to boot from USB so it'll have to be some way of using a floppy I'd imagine. [/B][/I]

---

### Post by rennen01 on 2007-04-20
> **alanmzifa said:**
> [I][B]
 How can I resize the partitions (I've no CD drive, laptop BIOs can't be set to boot from USB so it'll have to be some way of using a floppy I'd imagine. [/B][/I]

Try using the GParted LiveCD to resize your partitions

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by eentonig on 2007-04-20
Good luck using a LiveCD on a system without system tray :mrgreen:


I'm afraid you wont be able to resize without a Live CD, because the volumes that need to be resized, need to be unmounted if I'm not mistaken.

---

### Post by neerajadsul on 2007-04-23
Hey now it says free 6034 KB on /boot. How it is possible?
There are only few files on /boot. Totally 1.67 GB free space is available.

---

