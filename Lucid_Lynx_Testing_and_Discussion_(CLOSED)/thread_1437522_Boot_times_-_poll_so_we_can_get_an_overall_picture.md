---
title: "Boot times - poll so we can get an overall picture"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by canter690 on 2010-03-24
Just wanted to start a poll so we can see the overall spread of boot times.  Other threads have people just posting which doesn't provide an overview.  Haven't posted a poll before - hope this works...

---

### Post by k3lt01 on 2010-03-24
Over 25 second in both Karmic and Lucid. Has been down to 32 seconds with Karmic on my little laptop which I think is ok considering its specs.

---

### Post by Uncle Spellbinder on 2010-03-24
Lowest since Beta 1, 10 seconds. Tend to hover around 15 seconds on a regular basis.

---

### Post by dcstar on 2010-03-24
> **canter690 said:**
> Just wanted to start a poll so we can see the overall spread of boot times.  Other threads have people just posting which doesn't provide an overview.  Haven't posted a poll before - hope this works...

What is the definition of a "boot time"?

Time to the Login screen, time to the completion of autologin and desktop loading, time to the end of the boot process according to syslog?

---

### Post by canter690 on 2010-03-24
> **dcstar said:**
> What is the definition of a "boot time"?

Time to the Login screen, time to the completion of autologin and desktop loading, time to the end of the boot process according to syslog?

As a lowest common denominator I am using the number off bootchart.  I know there is cropping and other methods such as pybootchartgui but figure bootchart standard is the simplest.  Happy for some one with more knowledge to suggest the standard and we can set it - its still early.

---

### Post by mdurham on 2010-03-24
Without a definition of 'boot time' as requested by dcstar, this poll is useless.

---

### Post by the_one(2) on 2010-03-24
Around 15 seconds with a SSD drive as boot drive. I'd guess my crappy speccs other than the SSD is the reason for my crappy boot time (for a vertex SSD)
Edit: scratch that... Got 09:35 with pybootchartgui today (with me inputting my password)

---

### Post by k3lt01 on 2010-03-24
Bootchart is probably the best definition. However some of us, like me, can't run bootchart in Lucid cause it stuffs around with the system but we know it is to a usable desktop anyway.

---

### Post by ElSlunko on 2010-03-24
I'm over 25 seconds but my bootchart improved from 55 to 30 seconds.

---

### Post by timosha on 2010-03-24
I don't know what the added value of this poll is, but anyway:

Boot times:
Thinkpad R51 - HDD0 80 GB - HDD1 160 GB = > 30 sec.

HP dx2400 miniATX - HDD1 1.5 TB = > 5 min (probably due to fsck)

---

### Post by ShadowDragon on 2010-03-24
As soon as my graphic issues are fixed, I can test-run lucid, but by judging the improvements that are made in lucid, like 50% less time to hardware detection, removal of hal, ... and since I already have 7.5 seconds on Karmic, I'm pretty sure I will end up under 10 seconds. :)

---

### Post by karthick87 on 2010-03-24
15 to 20 sec's

---

### Post by _h_ on 2010-03-24
18 seconds as of my last bootchart, am trying to get that lower though.

---

### Post by jaoc223 on 2010-03-24
My last boot time according to bootchart was 28 sec. My best boot time was
10 sec.

Seems like , and I know this is an issue with beta1, fschk runs for about 10 sec when booting up.
One of the devs said this would be hidden for the final release of Lucid. So I don't know whether or
not this is included in boot times. Maybe someone could clarify this for me.

---

### Post by VMC on 2010-03-24
I agree on the confusion over the term boot time. Maybe the OP can change the reading to "from Grub to desktop".

I used a stop watch yesterday nd from Grub to desktop it took 23 seconds, using P4, 2.6ghz.

I also think the bootchart times is misleading. bootchart itself takes time to capture the files being used. 

Also, its how you perceive your booting that matters and not what some program tells you.

Bootchart graphs are useful for developers to determine the order and length of boot. It does very little for our usage.

---

### Post by ingegnerlillo on 2010-03-24
pybootchartgui show a 1:24 seconds boot :o

But with a crono gnome is loaded in 46 sec.

Some ideas on how to make it better?

---

### Post by uRock on 2010-03-24
It is hard to time when it stops to offer the grub list, then again for the login. I know it is fast enough that I don't feel guilty for not hitting the power button before getting my coffee anymore.

---

### Post by arashiko28 on 2010-03-24
25 seconds including I had to type my password. :p nice timing!
<20 seconds to shut down! Very nice too!

---

### Post by sgage on 2010-03-24
I used my bootchart time for the poll: 19.8 seconds.

---

### Post by rockyjones on 2010-03-24
My Thinkpad T-60 (2.0Ghz Core Duo) with 128G Patriot Torqx SSD shows a bootchart time of 6.22 secs with beta and today's updates.  

Nice!

---

### Post by k3lt01 on 2010-03-24
> **VMC said:**
> I agree on the confusion over the term boot time. Maybe the OP can change the reading to "from Grub to desktop".So what do people who don't have Grub visually come up during boot do? My desktop certainly doesn't.

---

### Post by TrevT93 on 2010-03-24
Between choosing the right option on the GRUB menu and the Xubuntu GDM login screen showing up, about 19 seconds.  That's actually 4 seconds worse than Karmic was for me.  I was surprised.  Also can't seem to get plymouth to work, but that's another issue altogether.

Because of the upgrade to Lucid, my copy of Arch is now the faster boot (roughly 16 seconds).  But some of the issues regarding the boot are bound to get repaired before the final release, so I'm holding out hope that Xubuntu will be the winner in the end.

Specs: laptop running a 2 ghz Core Duo (NOT a Core 2), 2.5 GB of DDR2, 160GB hard disk partitioned into 5 partitions.  Graphics are an Intel 945 Express chipset (cheapo graphics might explain why plymouth won't load - I've heard something about it having to do with the graphics adapter itself).

---

### Post by Ellipsis on 2010-03-24
I am getting 12.84 seconds-

Which is awesome. 

Specs: AthlonII x2 @ 3.4 GHz, 3GB DDR2 Ram, 500GB WD Black Edition, ATI 4670 1GB.

---

