---
title: "upgrade frustrations from jaunty to karmic"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by harrismh777 on 2010-05-19
Greetings,

   I never upgrade. Its always a bad idea. Well, I upgraded to karmic Koala last night (the high speed download took 30 minutes, the upgrade took almost (4) count them, hours), and the system is functioning. But there are irritating issues I hope to understand |resolve.
   The upgrade ran flawlessly-- it just took forever. I don't understand that. I can load from the disk in much less time... why does the upgrade take so long?
   Following the upgrade the machine would not boot. Very frustrating. I received a tiny white ubuntu community logo in the center of the screen (the trinitarian symbol) and then many many many messages about partitions waiting (that(!) is new, what is that all about) and some of the partitions not mounting etc etc with options to drop into a root shell to recover!!!.
   I dropped into a root shell to "recover" and checked out the partitions (all of which were fine) and all of which can be mounted....  what is going on here in Karmic?   So, I rebooted and just decided to wait and watch... eventually (and I mean several long minutes) the partition wait messages ceased and the machine finally booted up. This is very strange behaviour. I have been using linux since RatHat 2.0.52 kernel and never have I seen this kind of silly-ness. 
   As the machine booted up (very cool Karmic splash screen, by the way) I received two errors continuously... 1) can not update /var/lib/gdm/.ICEauthority and 2) configuration server error 256. Somehow the permissions got honked in /var/lib/gdm.   I was able to get around this stupidity with   sudo chown -R gdm /var/lib/gdm    On my past systems root owned /var/lib/gdm, gdm was the group, and the sticky bit was set:
  drwxrwx--T   root gdm       /var/lib/gdm
I do not understand why the permissions are getting clobbered, but from the other updates on this forum seems very common.
   Now the system is running stable for several hours (even with the screen-saver running, yeeaah). BUT, and this is the BIG BUT, the system is running sluggishly; particularly the desktop responsiveness. Everything is just slow to respond. This is very frustrating. Things are becoming bloated (and granted my laptop is older--nine years old--R30 1ghz ThinkPad 1gig mem, 1ghz pentium copermine) so that the system just crawls along. Jaunty was very responsive on the same machine even with the cpu speed held back to 700mhz.
   I like the fact that the Karmic Koala ships with the latest 3.5+ Firefox, and that the ar9170 drivers for the wn111v2 usb wifi adapter work well out of the shoot. Other package updates seem to be helpful, and so far I have not found anything totally "broken". Well, except for the gnome system monitor.
   The gnome system monitor is just plain wrong. The cpu percentages are wrong and do not match TOP percentages. (they are close, but far enough off to be irritating) When the system monitor is running the cpu jumps to over 50%--- it never did that before! So, the baseline cpu percentage is 50%...     hmmm   TOP shows that xorg is taking 33.4% and gnome-system-mo is taking 12.8% consistently...  on jaunty these would be 5.7 and 3.0 respectively... what happened?
   The gnome system monitor is reporting only 157 MiB used when in fact it is over 456 MiB (according to TOP) out of a total of 994 MiB when in fact the system has 1018432 K installed (and correctly reported by TOP).
Seems like there is a bug to report here, but not sure where to send it first.
   The network stuff seems to be running well, except for the wifi speed is still at the "g" level instead of the "N" level--- an issue I suppose for the Otis ar9170 driver(s).  
   The audio and video are running fine, except for the x desktop being sluggish. 
   
Thanks for allowing me to send some feedback.

:shock:

---

### Post by tommcd on 2010-05-19
> **harrismh777 said:**
> 
   I never upgrade. Its always a bad idea.
You have 2 options:
 (Hint: you have already answered your own question):
1. Spend many days, weeks, or more ... trying to fix this mess.
2. Do a fresh install of Ubuntu 10.04 LTS and be done with it.
The first option will take, well, who knows how long it will take to solve your problem(s).
The second option will fix your problems in less than 30 minutes.
It is your choice.
Note that there is no such thing as an Ubuntu install that is "so highly customized" that no mortal user could never do a reinstall of Ubuntu... as I read on these forums so many times.

I also never upgrade. I always do clean installs.
I never bother with those far too ubiquitous ppa repos either.
I never have problms with Ubuntu.
It is your choice though, as always.

---

### Post by wojox on 2010-05-19
What type video card/chip are you running?

---

### Post by harrismh777 on 2010-05-19
> **tommcd said:**
> You have 2 options:
 (Hint: you have already answered your own question):
1. Spend many days, weeks, or more ... trying to fix this mess.
2. Do a fresh install of Ubuntu 10.04 LTS and be done with it.


I know. The deal here is that my laptop has only a very old almost first generation cd  (sony); and it has issues... sometimes it reads reliably, and sometimes it doesn't. So, I went with the upgrade on this box because I really don't think I'm going to be successful from disk. The other option I have is a clean install from disk using a network connection from one of my lab machines. What a pain... but, maybe better than an upgrade. 

Mere mortals can restore my ubuntu custom system... but the issue is time. I have many packages and backup folders and special permissions (for four different users of this notebook) and I could probably take two-three days to get it back to normal after the reload... so I've been resisting that. 

<sigh>

---

### Post by harrismh777 on 2010-05-19
The video is the Trident Ciberblade chipset with the 13.3" TFT.

uses trident_drv.so

The chipset is the cyberbladeAild


Why?

---

