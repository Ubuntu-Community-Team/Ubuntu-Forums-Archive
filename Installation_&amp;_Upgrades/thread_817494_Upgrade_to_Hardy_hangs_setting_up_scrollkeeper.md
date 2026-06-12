---
title: "Upgrade to Hardy hangs setting up scrollkeeper"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by pawood on 2008-06-03
I have been trying to upgrade from 7.01 to 8.04. During the upgrade my computer re-booted so I am attempting to resume the upgrade.
 
After reading a few posts on the forum I ran
 
apt-get install -check
 
and then 
 
dpkg --configure --a
 
The upgrade resumed, completed a number of steps until it reached
 
Setting up scrollkeeper (0.3.14-15unbuntu1) ...
Rebuilding the database. This may take some time
 
and it did .... 
 
after half an hour I rebooted and ran through the above steps again and this time I left it running overnight (11 pm to 8 am) before giving up and turning off the computer.
 
What should I do to finish off this upgrade?

If I now run 

apt-get install -check
 
I am immediately prompted to run
 
dpkg --configure --a

which then immediately starts

Setting up scrollkeeper (0.3.14-15unbuntu1) ...
Rebuilding the database. This may take some time

and then nothing appears to happen.
 
I have been a happy Ubuntu user under 7.04 and whilst happy to have a play on the command line, I am a techno newbie to this sort of thing, so I will need step-by-step help - please!

---

### Post by Slim Odds on 2008-06-03
scrollkeeper updates can take a LONG time, hence the "This may take some time" message

Be patient and see if it completes (how long did you wait?   how fast if your machine?)

---

### Post by pawood on 2008-06-04
I waited 9 hours

Machine is 2400 AMD Athlon (2 GHz) with 1 Gb Ram

---

### Post by pawood on 2008-06-04
After a few more attempts

apt-get check

found some disk errors which were fixed. 

Then had to run 

dpkg --configure -a

and the upgrade continued until the sequence stopped because too many other packages that haven't been successfully upgraded (libgnome and others) so it looks like a mess!

Is there a way to re-start the whole upgrade without wiping the HDD, settings and data?

---

