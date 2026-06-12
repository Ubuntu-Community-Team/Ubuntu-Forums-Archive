---
title: "Upgrade tips for a roll-your-own ubuntu"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by eikenberry on 2006-10-28
I use a very stripped down installation. Started with the server install and added what I wanted. The only ubuntu-* meta package I have installed is ubuntu-minimal (just because there was no reason to remove it). I also don't have any of the other *-desktop meta packages installed.

Seems to me like the basic apt-get update/dist-upgrade should work but I wanted to see if others with similar setups have had any issues.

Thanks.

[edit]

Couple notes I thought I'd add.

This is dapper->edgy upgrade. :)

I have backports and one unofficial repository in my sources.list. I plan on commenting both of these out for the upgrade.

---

### Post by TheWizzard on 2006-10-28
mmm, i don't hink i understand your problem completely. 
why do you want to upgrade? with your minimalistic approach i can't see any benefits...

---

### Post by eikenberry on 2006-10-28
> **TheWizzard said:**
> mmm, i don't hink i understand your problem completely. 
why do you want to upgrade? with your minimalistic approach i can't see any benefits...

Just because I don't use all the software in ubuntu (does anyone) doesn't mean I don't want newer versions of what I do use.

---

### Post by TheWizzard on 2006-10-29
> **eikenberry said:**
> Just because I don't use all the software in ubuntu (does anyone) doesn't mean I don't want newer versions of what I do use.

i don't know how good the backports for dapper are, but in red hat / fedora the backports ensured i'd always had the newest versions of all packages while i was using older versions of the system. i only upgraded (clean) when my version of the system was no longer supported.

---

### Post by kerry_s on 2006-10-29
Back up your data just in case, alot of people are having problems with upgrading. I would recommend a fresh install, there have been alot of changes and i'm not surprised people are having problems upgrading. I just redone mine yesterday, i'm using edgy-server-install + xfce4.

Here's my sources just in case you want them->

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse 

deb [http://mrpouit.free.fr/plf-fallback/](http://mrpouit.free.fr/plf-fallback/) edgy-plf free non-free

---

