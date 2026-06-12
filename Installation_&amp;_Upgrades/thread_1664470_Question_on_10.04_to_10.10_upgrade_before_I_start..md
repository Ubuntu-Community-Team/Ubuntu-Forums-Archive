---
title: "Question on 10.04 to 10.10 upgrade before I start."
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by Dutch70 on 2011-01-11
Hi all, I have a few questions. 

 Last week I started to download the upgrade & then backed out. Now I want to go through with it. I began by making sure my system is currently "up to date" and got these messages (photo's attached) from update manager.

 So the problem is probably "an upgrade that didn't complete". I also just removed "ubuntu restricted packages" via Software Center and checked for updates again & got the same thing.

 How should I go about doing the upgrade? Should I complete the partial upgrade, then finish the upgrade? Also should I remove the Cairo Dock and advanced desktop effects or purge the system or anything like that?
Any help or advice would be greatly appreciated!!!

Note that the 2nd window is what showed up after selecting "Partial Upgrade".

---

### Post by nomko on 2011-01-11
Best thing to do is **_not_** to upgrade your running system, but to do a fresh/clean install. This will avoid many update/upgrade problems. 
 
This is what i uselly do:
- backup all files i needed (photo's,documents, etc.)
- reboot with the gparted livecd
- remove the partition with Ubuntu installed on
remove also the partition which contains the /home folder if it exist. Reason: many programs places their configuration files in hidden folders. Removing the /home partition also removes these files so that they will not conflict or cause problem during installation of the new version of ubuntu
- reboot with the ubuntu live-cd
- install the new version of ubuntu
 
Like this i never had any problems of files conflicting, never had problems with old configuration files or what so ever.
 
This is my idea and how i work.
It's up to you if you want do it this way or not.

---

### Post by Dutch70 on 2011-01-11
> **nomko said:**
> Best thing to do is **_not_** to upgrade your running system, but to do a fresh/clean install. This will avoid many update/upgrade problems.

Thank you! You obviously put some work into your post and it is greatly appreciated.

 However, I just did a fresh install from **8.04 to 10.04** about 3 weeks ago, That's what I'm trying to avoid by upgrading shortly after they come out. Instead of waiting 2 yrs for the LTS version.

---

### Post by alenis on 2011-01-11
I did the upgrade yesterday and it was smooth. One thing I did was to disable all extra repositories I had added to synaptic, followinf advice found somewhere in the forum. You might try that.

The only problem I have is that, although the system is 10.10, it says 11.04 in the about box. But I'm sure it's 10.10....

---

### Post by Dutch70 on 2011-01-11
> **alenis said:**
> I did the upgrade yesterday and it was smooth. One thing I did was to disable all extra repositories I had added to synaptic, followinf advice found somewhere in the forum. You might try that.

The only problem I have is that, although the system is 10.10, it says 11.04 in the about box. But I'm sure it's 10.10....

Here is a pic of what is in my repositories.

 I'm confused about the "Maverick Meerkat" stuff in there, and don't know which ones are "extra". Should I just select "revert" at the bottom of the page?(cut out of the pic)

---

### Post by Nightslay on 2011-01-11
> **nomko said:**
> Best thing to do is **_not_** to upgrade your running system, but to do a fresh/clean install. This will avoid many update/upgrade problems. 
 
This is what i uselly do:
- backup all files i needed (photo's,documents, etc.) 
........


Well it is correct it is the best way todo a fresh install
but i would advice to make a backup of important Data

then decide with either the partial upgrade, 
or fresh install
both does take about the same time maybe 5-10 min difference. 

ps. just did a up grade from 8.04 -> 10.10 and from 10.04 -> 10.10 without any problems.

Best Regard
Claus

---

