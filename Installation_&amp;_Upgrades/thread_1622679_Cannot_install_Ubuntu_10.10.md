---
title: "Cannot install Ubuntu 10.10"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by dstrout on 2010-11-15
I downloaded and burned the Ubuntu 10.10 ISO today, and booted it on a PC I wanted to install Ubuntu on. The CD booted successfully, and the desktop came up, but when I double-clicked "Install Ubuntu 10.10", *nothing happened*. I clicked it a few more times, but still nothing. I then tried rebooting, and clicking the Install icon again. Still, nothing. Any ideas as to what is causing this?

TIA,
D. Strout

---

### Post by shadowofblood on 2010-11-15
When the Live CD boots up, and you reach the first screen (Purple with some icon at the bottom), press f6.  You should get a menu asking if you want to try Ubuntu, install it, test the cd, etc.

Select the Install Ubuntu option from that menu and see if that works.

---

### Post by oboedad55 on 2010-11-15
> **dstrout said:**
> I downloaded and burned the Ubuntu 10.10 ISO today, and booted it on a PC I wanted to install Ubuntu on. The CD booted successfully, and the desktop came up, but when I double-clicked "Install Ubuntu 10.10", *nothing happened*. I clicked it a few more times, but still nothing. I then tried rebooting, and clicking the Install icon again. Still, nothing. Any ideas as to what is causing this?

TIA,
D. Strout

Sounds like a bad burn. Try burning it at slower speed, failing that download it again and retry.

---

### Post by dstrout on 2010-11-15
> **shadowofblood said:**
> When the Live CD boots up, and you reach the first screen (Purple with some icon at the bottom), press f6.  You should get a menu asking if you want to try Ubuntu, install it, test the cd, etc.

Select the Install Ubuntu option from that menu and see if that works.

Thank you, am trying as I write.

> **oboedad55 said:**
> Sounds like a bad burn. Try burning it at slower speed, failing that download it again and retry.

I thought that too at first, but usually if it's a bad burn, it won't work at all, or many things won't work. This is the only thing that won't work.

EDIT: No dice on the F6/install option. The OS came up, but the same as always, no installation dialog. Maybe it is a bad burn. However, there is one thing I forgot to mention in my last post. Every time I boot up and select install, then shut down, I get a notification that a program, gnome-keyring-daemon, is not responding, and do I want to lock screen, cancel, or shut down anyway. The first boot, I clicked the install button a bunch of times, and there was a bunch of gnome-keyring-daemon processes running. The second time, I clicked Install fewer times, and there were fewer gnome-keyring-daemons. I think I will try starting it up and shutting it down without clicking install, and see if there are *no* gnome-keyring-daemons.

EDIT 2: I was right! If I don't try to install, the gnome-keyring-daemon not responding alert doesn't show on shutdown! So somehow and for some reason, gnome-keyring-daemon is blocking the installer. Any idea why? What *is* gnome-keyring-daemon? Anything I can do to fix this?

---

### Post by oboedad55 on 2010-11-15
> **dstrout said:**
> Thank you, am trying as I write.



I thought that too at first, but usually if it's a bad burn, it won't work at all, or many things won't work. This is the only thing that won't work.

Odd. I've had this happen and it turned out o be a bad burn. Then try what a previous poster suggested. When the live cd boots up you'll have a choice to try Ubuntu or install it. Try installing it without booting up to the desktop. It's the same installer in any case.

---

### Post by dstrout on 2010-11-15
> **oboedad55 said:**
> Odd. I've had this happen and it turned out o be a bad burn. Then try what a previous poster suggested. When the live cd boots up you'll have a choice to try Ubuntu or install it. Try installing it without booting up to the desktop. It's the same installer in any case.
As I said in the edit, I tried directly installing, but still nothing. It appears to be a problem with gnome-keyring-daemon, whatever that is. Perhaps I've uncovered a bug?

---

### Post by dazman19 on 2010-11-15
You should do an md5 check on the image file you downloaded. Theoretically There is a 99.9999999% chance that TCP can get a few bits wrong and they can pass error detection.

---

### Post by oboedad55 on 2010-11-15
> **dstrout said:**
> As I said in the edit, I tried directly installing, but still nothing. It appears to be a problem with gnome-keyring-daemon, whatever that is. Perhaps I've uncovered a bug?

Sorry, I missed that. I have no other bright ideas.

---

### Post by shadowofblood on 2010-11-15
You may want to try using the Alternate Installation CD.  It works for me when the Live CD gives me problems.

---

### Post by dstrout on 2010-11-15
> **shadowofblood said:**
> You may want to try using the Alternate Installation CD.  It works for me when the Live CD gives me problems.
I think it's a bug of some sort, or maybe some issue with gnome-keyring-daemon and the computer I'm trying to install on. Also really don't want to download the Alternate CD if it's a bug, and since it's another 700MB download.  As to checking with MD5, I deleted the file :sad:

---

### Post by shadowofblood on 2010-11-15
Do you already have an older version of Ubuntu on the HD?  If so, you should be able to just update it.

If it's a fresh install, I don't think there are many options left :(

As I said before, you can try the alternate CD.  If you have a flash drive with enough space, you can put the alternate install iso on that instead of risking another CD.

Since you can't verify the MD5, it's hard to tell if it's a bug or an error on the disc.

---

### Post by dstrout on 2010-11-15
There is no older version of Ubuntu on the HD; it's a fresh install. I have tried the Alternate CD though, I couldn't figure out how to get through the install, with partitioning and networking, I got a bunch of weird issues. If I did get it, though, I wouldn't be risking CDs, I'm using a CD-RW. Anyway, is there an error log I could like at for GKD (gnome-keyring-daemon, for future reference)?

---

### Post by dstrout on 2010-11-16
Well, I suppose I will download the install CD again and burn again at a slower speed. If that doesn't work, and I have the same problem, I'll file a bug report.

---

### Post by dstrout on 2010-11-17
I'm trying Kubuntu now; I downloaded it and checked the MD5, which was correct. I then burned the CD with ImgBurn and verified it successfully. So, in theory, I have the same file I downloaded from the web on the CD, and the file I downloaded from the web is the same file that was hosted on the Ubuntu servers. If I *still* have the same problem, I'll file a bug report.

---

### Post by dstrout on 2011-06-05
For future reference of anyone who has this problem, it wasn't a bad burn, it was a bad disc! Kubuntu wouldn't install either off that disk, and I had other troubles later. If all else fails, try another disc.

---

