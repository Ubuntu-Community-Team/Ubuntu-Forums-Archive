---
title: "Do I need a clean install for upgrading to 10.4?"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by AlessandroV on 2010-03-19
Hello!

I'm a relatively new user of Linux, I use Kubuntu 9.10, and I would like to know whether I need to make a clean install for upgrading to 10.4 (I know, stable isn't ready yet, but I'm impatient :p, and I want to prepare in advance) or I could do it in some way without losing everything I have installed? Or maybe it would be better to only upgrade to the newest version of KDE (I'm using 4.3.2 now)? Which one is easier and/or better? How is it done (Note: using KDE)? thank you in advance

---

### Post by lindsay7 on 2010-03-19
Just keep getting the updates and when you are ready for 10.4, hit the alt + f2 key and type update-manager -d on the command line. that will upgrade you to 10.4 version at that moment. If you do this before the final release date for 10.4 you will get the beta version.  You will not loose anything that is on you system.

---

### Post by AlessandroV on 2010-03-19
Ok, thanks! First I got to love Windows and hate Linux, which made me begin hating Windows and loving Linux!

---

### Post by markbuntu on 2010-03-19
Upgrades can be very troublesome unless you take a few precautions.  

First, make sure you have all the latest updates.
Second, back up your /home. 

Third, remove any proprietary drivers before upgrading, proprietary ati and nvidia and broadcomm drivers can cause huge headaches in an upgrade.

Just so you know, if you have other packages from outside the repositories these can end up with unmet dependencies and may not function properly or need to be reinstalled after an upgrade. If you have the original packages, put them someplace safe and make sure they will work with the upgraded libs/kernel etc before reinstalling them.

If you have added repositories like Launchpad PPAs make sure they are still needed and are pointed at the proper version repository. You can also just remove them and add back the ones that you want later.

If you wait a few weeks after the release you will not be so bombarded with daily updates which tend to come thick and fast right after a release. Instead you will get one huge update and then fewer and fewer as time goes on. If you have a limited internet connection you should seriously consider this.

---

