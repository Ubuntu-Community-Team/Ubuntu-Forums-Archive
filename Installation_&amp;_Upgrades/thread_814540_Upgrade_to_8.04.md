---
title: "Upgrade to 8.04"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by mavuashire on 2008-05-31
I have updated my system and wanted to upgrade from 7.10. however, the cd method described on the upgrade web site does not work. Using update manager also fails saying "Authentication Failed"

Because of some comments on the release notes, I commented out some lines inserted by automatix in "sources.list". Is that the problem?

---

### Post by Rocket2DMn on 2008-05-31
This is one reason why automatix is the devil.  If you had it installed, I would not try upgrading your system since it has a serious potential to completely brick the system.  Because of automatix, your best option is to backup all your data and do a fresh install of Hardy.  Afterward, stay away from automatix.

---

### Post by Pumalite on 2008-05-31
Remove ALL third parties from your sources.list

---

### Post by zvacet on 2008-06-01
There is no Automatix for Hardy.As **Pumalite**  adviced you remove all third parthy repos before upgrade.

---

### Post by mavuashire on 2008-06-01
I get your point. I had automatix installed from ubuntu 6.10 thru other upgrades and have not used it with this version(7.10). Yeah, it is a bad thing, but how do i get around it. I have many programs I want to keep, more especially the drivers are hard to get for some devices.

---

### Post by PmDematagoda on 2008-06-01
> **mavuashire said:**
> I get your point. I had automatix installed from ubuntu 6.10 thru other upgrades and have not used it with this version(7.10). Yeah, it is a bad thing, but how do i get around it. I have many programs I want to keep, more especially the drivers are hard to get for some devices.

From what I know of an upgrade, all third-party applications and such are removed before the upgrade. And you can't get around it unless you want a very badly broken system.

---

### Post by Bubba64 on 2008-06-01
When I started with dapper I used automatix as well but after a while I figured out what to install for my needs without it. When you remove anything installed by automatix there are dependencies that are left and not removed, so the fresh install is great advice.

---

### Post by mavuashire on 2008-06-01
Is it possible to replace the sources list with a new one. I have since removed automatix. Also how do i get new authentication keys coz I think they are the ones stopping me from upgrade.

---

### Post by Bubba64 on 2008-06-01
> **mavuashire said:**
> Is it possible to replace the sources list with a new one. I have since removed automatix. Also how do i get new authentication keys coz I think they are the ones stopping me from upgrade.

Is the CD upgrade you tried the desktop CD. If it was me I would get the daily alternative and backup what you want to save and do an install from the bootup, there you can confirm the CDs integrity and partition. What your asking seems like trying to jury rig and will take you more time and probably not work. if your system was in good order the auto upgrade would get all the repository and keys you needed and turn off the 3rd party stuff and upgrade and install. Just so you have it here is the daily alternative link.
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)
Make sure you know how to save what you want and partition before you do anything if you want to save anything. Personally I don't ever have anything on my computers to really save except music which I will transfer between two different computers I own so I can do a clean upgrade so I can't really tell you the saving process or partitionong stuff.

---

### Post by mavuashire on 2008-06-01
Thank you everyone for your help. I guess I will have to do a clean install.

---

