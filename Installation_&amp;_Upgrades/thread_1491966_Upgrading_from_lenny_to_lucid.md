---
title: "Upgrading from lenny to lucid?"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by spalm on 2010-05-24
I've some major pains with my Debian 5.0.4 ("lenny") installation and as "squeeze" is delayed I consider switching to "lucid".

Has anybody done this before? I'm not sure if should upgrade directly to "lucid" or do an intermediate step via "karmic". Any suggestions?

TIA,
Stefan

---

### Post by lisati on 2010-05-24
It might be easier to backup your data, then do a clean install of Ubuntu.

---

### Post by dino99 on 2010-05-24
lucid is a sid like, so you might try with sid first as you dont talk about your issues.

if you have room to install lucid on a dedicated partition, a clean install is always a best choice as ubuntu tuning is quite different of a pure debian distro

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by wojox on 2010-05-24
I vote fresh install. You may get trapped in dependency hell.

---

### Post by kerry_s on 2010-05-24
> **spalm said:**
> I've some major pains with my Debian 5.0.4 ("lenny") installation and as "squeeze" is delayed I consider switching to "lucid".

Has anybody done this before? I'm not sure if should upgrade directly to "lucid" or do an intermediate step via "karmic". Any suggestions?

TIA,
Stefan

you can't turn debian into ubuntu, there built very different underneath.
you'll have to do a fresh install.

---

### Post by cascade9 on 2010-05-24
> **lisati said:**
> It might be easier to backup your data, then do a clean install of Ubuntu.
+1. It might be possible to change all the repos to ubuntu, and then update (people have managed to pull of crazier things....IIRC somebody did this with Arch-> Gentoo). But its a bad idea, do a fresh install.

---

### Post by spalm on 2010-05-24
> **kerry_s said:**
> you can't turn debian into ubuntu, there built very different underneath.
Hmm, I did it once (sarge -> dapper) and it worked out pretty smoothly. But this was a long ago and on a desktop, not on a server...

Anyway, people here seem to agree that a fresh install would be the best approach. Thanks a lot for your replies. I guess I've to think about a "migration strategy".

Stefan

---

### Post by dino99 on 2010-05-24
look at the link into my first post

---

### Post by kerry_s on 2010-05-24
> **spalm said:**
> Hmm, I did it once (sarge -> dapper) and it worked out pretty smoothly. But this was a long ago and on a desktop, not on a server...

Anyway, people here seem to agree that a fresh install would be the best approach. Thanks a lot for your replies. I guess I've to think about a "migration strategy".

Stefan

yeah, back then ubuntu was still standard debian, now there more ubuntu specific built to work there way.

---

### Post by spalm on 2010-05-25
> **dino99 said:**
> look at the link into my first post

Thanks for that link but as I have to reinstall and configure everything from scratch I'll also use the chance to change my filesystem layout (I might even switch to OS as I would love to see ZFS on my disks).

---

