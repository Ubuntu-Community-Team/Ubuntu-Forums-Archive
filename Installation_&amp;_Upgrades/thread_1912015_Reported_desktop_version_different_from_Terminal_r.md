---
title: "Reported desktop version different from Terminal report"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by DougEllis on 2012-01-19
I was running 10.04 without incident until last week.  At that time I started the process of upgrading Ubuntu in order to be ready for the next LTS (12.04).  The last time I did this it took several days of downloading to upgrade from v7.04 to 10.4 (generally with my internet connection it takes about 6-7 hours to complete an upgrade).  I started the process last week and after a fashion upgraded to v10.10. I ran into 2 problems:
1. I started a distribution upgrade on the update manger, but cancelled due slowness of connection.
2. I procured a copy of the alternate install cd (ISO). I mounted the ISO and ran ```
gksu "sh /media/cdrom/cdromupgrade"

``` I answered no to use internet to obtain latest stuff.  However, this response was ignored and (another) 6 hours later the grade was completed.
3.  Everything was fine (I thought, except "About Ubuntu" states I'm using 11.04) but ```
douglas@douglas-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick

```Subsequently, I have the next 2 alternate install ISOs for install in order (from a very fast connection - about 10 minutes each).

I tried to install v11.04-it failed due to "can't upgrade ubuntu-desktop," seemingly because I already have v11.04 desktop. I then made the "mistake" of "use internet" which allows upgrading the desktop, but taking the sloow downloading of more files.

My questions are: 

1. How do I sync the desktop and underlying operating versions.
2. How do I revert the ```
gksu "sh /media/cdrom/cdromupgrade"

``` to the original default setting (don't connect online)

---

### Post by DougEllis on 2012-01-30
I found that a system restart (cold) reset the parameters for the cd update routine.  Ultimately,
I let the system go online to retrieve the stuff it needed (1.5x the CD itself) and 14 hours later it was done (to 11.4).  The update to 11.10 went much smoother (no online files needed), although I wound with Unity desktop (which is another issue in itself):o

---

