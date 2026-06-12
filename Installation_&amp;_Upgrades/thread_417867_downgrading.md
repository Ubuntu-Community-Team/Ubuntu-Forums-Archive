---
title: "downgrading?"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by stickperson on 2007-04-21
Is there a way I can downgrade from Feisty to edge?  I'm having a lot of problems with my ati x1400 video card that I don't think I'll have in edgy.

---

### Post by tc101 on 2007-04-22
Someone told me there is but I don't know how to do it.

---

### Post by Mongoose on 2007-04-22
I suppose you could edit the /etc/apt/sources.list then apt-get update and then *manually pull down packages and force/pin downgrade as needed -- but that's very extreme and you'll have to worry about incorrect dependencies.  I can't recommend you trying it.  It's like "if you have to ask you likely can't do it yourself".

I'll give you a hand grenade showing you how it's done with pinning and take no responsibility.  This shows you how to do it for debian, and you'd have to make adjustments for ubuntu.  I'd suggest a backup of /home and your /opt or what have you.  This way if it fails you can just install edgy and keep your old /home.   =)

[http://linuxmafia.com/faq/Debian/downgrade.html](http://linuxmafia.com/faq/Debian/downgrade.html)

---

### Post by stickperson on 2007-04-22
hm, maybe I'll just remove Feisty and then install Edgy.  First of all, would that solve my problems?  I have an ATI x1400 card and I can't get Beryl to run correctly.  I *think* it's only messed up on Feisty.  So say using Edgy would work, how would I go about getting rid of Feisty and putting Edgy in its place?

---

### Post by Landser on 2007-04-22
> **stickperson said:**
> hm, maybe I'll just remove Feisty and then install Edgy.  First of all, would that solve my problems?  I have an ATI x1400 card and I can't get Beryl to run correctly.  I *think* it's only messed up on Feisty.  So say using Edgy would work, how would I go about getting rid of Feisty and putting Edgy in its place?

Why would you want to do like that?. What's causing the problem, is it the fglrx driver?

---

### Post by stickperson on 2007-04-22
I think so.  I can't get direct rendering to work.  I've followed soo many guides on how to get Beryl to work and none of them are working.  I have a T60 with trackpointing that I use for scrolling a lot and I can't get that working either.  I've been on thinkwiki.com looking up stuff and nothing seems to work.

---

### Post by punkinside on 2007-04-23
Beryl won't work with an X1400, downgrading to edgy won't solve your problem because AIGLX just won't work with an ati X1400

If you already got direct acceleration, then go and install XGL if beryl is a must have.

---

### Post by stickperson on 2007-04-23
I actually just got it working but it makes everything run reallllly slow.

---

### Post by zvacet on 2007-04-23
If you are still interested in downgrade here it is 

[https://help.ubuntu.com/community/DowngradeHowto]("https://help.ubuntu.com/community/DowngradeHowto")

---

