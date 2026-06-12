---
title: "I did an Intrepid -&gt; Jaunty upgrade. And it still works."
date: 2008-11-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2008-11-19
I installed a fresh copy of Intrepid on a spare partition (7GB) and used 'update-manager -d' to upgrade to Jaunty.

Shockingly, everything works. I don't understand. Every other time I've tried this with an earlier development release it broke after the second update.

Having said that, every x.04 release I can remember has been brilliant from the outset (I used Feisty as my main OS from Alpha 3).

---

### Post by xebian on 2008-11-19
> **jfernyhough said:**
> I installed a fresh copy of Intrepid on a spare partition (7GB) and used 'update-manager -d' to upgrade to Jaunty.

Shockingly, everything works. I don't understand. Every other time I've tried this with an earlier development release it broke after the second update.

Having said that, every x.04 release I can remember has been brilliant from the outset (I used Feisty as my main OS from Alpha 3).

Because at this time the jaunty repo is still intrepid for the most part.  I wasn't happy with intrepid so upgraded to jaunty as soon as the repo was open. So far I have the 27-9 kernel, nv 180.08, kde 4.2.  Quite snappy.  No hard numbers but the fact I could notice is significant enough.

BTW I used the hard(?) route - change intrepid to jaunty in sources.list.  aptitude update && aptitude safe-upgrade.  Easy as 123.

---

### Post by plun on 2008-11-20
> **jfernyhough said:**
> I installed a fresh copy of Intrepid on a spare partition (7GB) and used 'update-manager -d' to upgrade to Jaunty.



Yup... forced to do the same...:)

No problems except broken sound. I have my home brewed packages.

---

### Post by Gourgi on 2008-11-20
yep , i 've done it yesterday and the upgrade from intrepid to jaunty was successfull

---

### Post by Eclipse. on 2008-11-20
The major breakage will come, dont worry.:P

---

### Post by MacUntu on 2008-11-20
Did it two times today, no problems but no big changes either. Time will tell. ;)

---

### Post by klange on 2008-11-20
We're through the first big Debian merge, and things have fixed up. My X was broken last week, and various other things didn't work. Now everything is working fine.

---

### Post by CalaverX11 on 2009-02-02
Latitude E6400. So far the only thing that STILL doesn't work natively is my Sprint Novatel 5720 internal mobile broadband card. I continue to have to add the modprobe usbserial line to my modules on startup, and use KPPP to connect. network-manager 0.7 was supposed to fix that...I see the device IDs are in all the proper config files, but my card still isn't recognized.

All in all, though, everything else works, so far. We'll see what breaks over the next few weeks as more packages get updated.

---

