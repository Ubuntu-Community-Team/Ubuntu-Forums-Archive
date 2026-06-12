---
title: "Going from 6.06 to 7.04 - Upgrade or Clean install?"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by mrwooster on 2007-04-22
Hi,

I am running 6.06LTS and would like to upgrade to 7.04 - from my research I can see that either I can upgrade to 6.10 and then on to 7.04 - or - download 7.04 and do a fresh install.

I am running XP - Ubuntu on a dual boot (Dell inspiron 9400) and I have my home directory on a separate partition so a new install is possible.

What would you suggest to be the safest way to upgrade? I want to be very careful not to damage my windows partition.

Thanks

Guy

---

### Post by old_geekster on 2007-04-22
Personally, I would recommend the "upgrade" method.  It worked twice for me and with no problems.  Beryl is even running like a champ.

Here is the command that I used:

sudo update-manager -c -d

Some use "gksudo" instead of "sudo", but sudo worked for me.

I have also seen many good comments on the forum about upgrading.

---

### Post by Mochtroid-X on 2007-04-22
I always do a clean install whenever I switch to a new OS, mainly to make sure that the new OS has nothing from the old one causing problems as I have experienced in the past (98SE -> XP had problems and 6.10 -> 7.04beta also had problems). That's just my personal preference though, yours may be different.

---

### Post by mrwooster on 2007-04-22
Hmmm - one of each - I think I am going to try to go with the upgrade as it means I can keep all my settings.

---

### Post by gabrielp on 2007-04-22
I had serious problems while leaving the home partition ,only once I did clean install every thing went ok ,
So pls backup your old home and do clean install

---

