---
title: "Transfering linux to my friends PC..."
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by POW R TOC H on 2008-03-31
My friend has installed Ubuntu a few days ago, but his system is rather worthless without a normal internet conncetion. He is unfortunate enough to have a dial-up modem (56k) and he barely made it work. Anyway, updating linux and installing important sruff like build essentials, restricted drivers (etc.) requires amounts of bandwith he just can't spare. So, I thought why not give him a copy of my linux :D ?

Now, here's the thing. My system is on a 8Gb ext3 partition, and I have another 150Gb (ext2) mounted on /home. Is it possible for me to simpy copy my 8Gb partition to his hard drive (provided that partition tables are the same), but unmount my /home directory? Will this give him a working system on his PC?

If not (and if I asked an amazingly stupid question, which wouldn't surprise me), do you have an idea of how I might copy my system onto his hard and make it work?

Thank you in advance...

---

### Post by process91 on 2008-03-31
That may work, but there are a number of problems which could go very wrong with it. Instead, take a look at [AptMove]("https://help.ubuntu.com/community/AptMoveHowto"). Basically you can download packages and dependencies to a cd, creating a local repository to install from on a machine with no internet connection (or a slow one).

---

### Post by POW R TOC H on 2008-03-31
This seems to be what I needed... Thank you very much!

---

### Post by twright on 2008-03-31
either that or apt-on-cd would do the trick :)

---

### Post by LeoSolaris on 2008-03-31
If you're feeling adventurous, there was something I fiddled with a while back to make a Live CD out of a working system.

To tell you the true, it's probably easier to make a repo DVD and just do updates to his system from the DVD. I never did get the Live CD creator to work properly. It always returned a bug, but that might have been because I was trying to do it from within the running system.

The one I used has appearently been updated and upgraded since I used it. 

[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

There looks to be a few others too. Try googling for them.

Leo

---

### Post by lswest on 2008-03-31
well, you can always make a liveCD from the system using [this how-to]("http://lifehacker.com/software/linux-tip/make-an-ubuntu-backup-live-cddvd-with-remastersys-330181.php") (not sure how up-to-date it is, i had it bookmarked from a while ago)  Oh, someone beat me to it XD

---

### Post by dstew on 2008-03-31
To do updates and installs without internet, you can use the [nonetdebs service]("http://nonetdebs.homeip.net/"). You upload the status of your system to them, and they prepare links for all the packages. You put them on a CD, and install them.

---

### Post by POW R TOC H on 2008-04-05
> **dstew said:**
> To do updates and installs without internet, you can use the [nonetdebs service]("http://nonetdebs.homeip.net/"). You upload the status of your system to them, and they prepare links for all the packages. You put them on a CD, and install them.

Thank you!

---

