---
title: "Already The Latest? (But it's still Dapper)"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by rykel on 2006-11-02
Hi,

I tried to upgrade my Dapper to Edgy using the CD.

**[INDENT]$ gksu "sh /cdrom/cdromupgrade"[/INDENT]**

However, the upgrade never went through, and the dialog box said that my system was "up to date". The incredible thing is, I am still running Dapper!

Any ideas?

Note: I disabled ALL lines in sources.list other than the one about the Edgy CD.

---

### Post by rykel on 2006-11-05
Does anyone know about this issue? Is it a bug in the upgrade process?

---

### Post by aysiu on 2006-11-05
I don't know if that's a bug, but try this: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo apt-cdrom add
``` Put in your Edgy Alternate CD ```
sudo aptitude update
sudo aptitude dist-upgrade
``` If you don't have an Edgy Alternate CD, that's your "bug" right there. An upgrade cannot be done off a Desktop CD.

---

### Post by Linux&amp;Lizards on 2006-11-05
hope you get it fixed

---

### Post by rykel on 2006-11-06
> **aysiu said:**
> I don't know if that's a bug, but try this: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo apt-cdrom add
``` Put in your Edgy Alternate CD ```
sudo aptitude update
sudo aptitude dist-upgrade
``` If you don't have an Edgy Alternate CD, that's your "bug" right there. An upgrade cannot be done off a Desktop CD.

oic! Yeah, I could have the install (Desktop) CD... which means I have to re-download the Alternate CD all over again, at 20kB/s!!   ](*,) 

Hey, thanks a lot for the help, I will try your suggestion first, before any fresh downloads. btw, you are really a long-timer here, aysius...

---

