---
title: "Install prob on hp Pavillion"
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by mhodgo11 on 2011-08-11
Trying to install Ubuntu (tried several releases) on HP Pavillion Pentium 4 Proccessor 515 2.93 Gig 1M L2 cache 533mhz 90nm . Have 1 gig ram and 1Tb hd. Hangs on initial install screen  for ever. Tried versions from 8.10 (origional disk) to 11.01. Machine works perfectly on Windows XP but who wants that? Any help would be appreciated. I dont have much hair left to pull out. Please save me from total baldness before my time.
 Thanks The model is pavillion 1000 system number pl397aa

---

### Post by manzdagratiano on 2011-08-13
If you are trying the 32-bit installer, try using the 64-bit version - that has worked for me before when the 32-bit would hang for a long time.

---

### Post by steve11911 on 2011-08-15
Please post the Pavillion's exact model number.

---

### Post by mhodgo11 on 2011-08-15
hp pavillion 1000
 system number pl397aa

---

### Post by mhodgo11 on 2011-08-15
pavillion 1000.   system number pl397aa

---

### Post by YesWeCan on 2011-08-15
Do you get to the pink screen and the bizarre icons at the bottom, and if you hit a key it should ask you for a language and then show you a menu?

If so, run "Check disc for defects" first. This makes sure your CD is ok.

Then I'd hit F6 and select 'nomodeset'. This sometimes avoids grpahics card issues which seem a perennial problem with Ubuntu (but not Windows).

Failing that, I'd suggest using the alternate install CD. It won't let you boot into a live session, tho. But it has more drivers and stuff on it and sometimes will get you passed a sticking point.

In terms of RAM efficiency and such you are probably better off installing the 32 bit if you can.

---

### Post by steve11911 on 2011-08-15
I agree with Yeswecan on checking the bios settings and verifying the integrity of the install media.Failing that I would suggest trying several live cd's starting with 10.04LTS. There is evidence a Knoppix distro will work (see below) and considering the age of the hardware I wouldn't be afraid to try a knoppix version that is equally aged.
This dated post may help only a little but raises the question of HP possibly having 2 different mainboards with the same nominclature and also refers to a successful Ubuntu install but sadly,fails to identify the animal...

[http://www.howtofixcomputers.com/bb/ftopic153741.html](http://www.howtofixcomputers.com/bb/ftopic153741.html)

---

### Post by Mark Phelps on 2011-08-16
You should NEVER try to force an install of any Ubuntu version on untried hardware.  ALWAYS boot the CD in Try Ubuntu mode (known as LiveCD) and see how well it works, first.

That way, you can discover the problems and post here, and hopefully, get solutions to those problems -- BEFORE you do the installation.

---

