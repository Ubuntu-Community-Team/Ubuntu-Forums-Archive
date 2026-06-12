---
title: "Help me re-install Ubuntu 7.10"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by hspopoy on 2007-12-09
Yesterday, I successfully installed Ubuntu 7.10 on my computer.

Being a noob (new user) of the OS, I began downloading a lot of stuff.

Then came my problem. My movie files suddenly stopped playing, and other applications seemed to conflict with my new downloaded and installed apps.

So now I want my old/default Ubuntu 7.10 setup. Is there a way on bringing Ubuntu back to the way it was when I first installed it?

I tried booting with the Live CD installer, thinking that a fresh install would clear things up. But I always get stuck at the partition part of the installation.

BTW, I'm dual-booting Ubuntu 7.10 with a prior Windows XP installation. That's why I don't want to use guided partitioning (use entire disk).

What should I do?

other info:
Harddisk = 160GB
windows partition = 90GB
linux = 70GB
*When I use guided partitioning (auto resize), it states that 33GB would be used for the Ubuntu installation. So I'm having doubts on using that option.
*Also tried Manual, but I'm having a hard time figuring it out.

Please help me Ubuntu Gurus out there! ^_^
Many, many, many thanks in advance. >.<

:guitar::guitar::guitar::guitar::guitar:

---

### Post by Pumalite on 2007-12-09
Get Gparted Live CD. Boot from it. Delete Ubuntu partition. Make new partition (of the same space) formatted ext3. Now reinstall Ubuntu to that partition (only XP)
Vista: need to allocate space for Ubuntu from WITHIN Vista.

---

### Post by hspopoy on 2007-12-09
> **Pumalite said:**
> Get Gparted Live CD. Boot from it. Delete Ubuntu partition. Make new partition (of the same space) formatted ext3. Now reinstall Ubuntu to that partition (only XP)
Vista: need to allocate space for Ubuntu from WITHIN Vista.

WOW! Thanks for the very quick reply Pumalite!
I'm now downloading Gparted...
I'll keep you posted.
:guitar::guitar::guitar::guitar::guitar:

---

### Post by Pumalite on 2007-12-09
Go Manual ( point to your partition). A good scheme:
10 GB for '/'
2x RAM up to 1 GB for /swap
The rest for /home

---

### Post by hspopoy on 2007-12-09
> **Pumalite said:**
> Go Manual ( point to your partition). A good scheme:
10 GB for '/'
2x RAM up to 1 GB for /swap
The rest for /home

what's '/home' for?

---

### Post by PmDematagoda on 2007-12-09
The /home directory is where all you personal files and settings are stored.

---

### Post by Pumalite on 2007-12-10
You can put Videos, Movies, Images and Music if you want too.

---

