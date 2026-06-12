---
title: "Problem with starting newly installed Ubuntu"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by ccaazz on 2007-09-23
I just installed ubuntu to a partition on my hard disk, the live cd booted up without a problem and the install seemed to go smoothly enough.  However, after completing the install and restarting my machine i have a problem.

I can log into my account, but once in, i get a blank screen for a long time, and then get an error message (shown in the attatched picture).  My mouse stays responsive, but no further loading of the os occurs.

my pc specs are as follows: dell, pentium 4, 3.4 gigahertz processor speed with hyperthreading, 1 gig of ram, and a 256 meg x600 series ati graphics card.  (basically its more than powerful enough to run ubuntu!).

thanks for your help!

---

### Post by Pumalite on 2007-09-23
Alternate CD would be better, but before we go that route, reboot and let's see what happens. I would have suspected a lack of xserver,but you error message is misleading at least to me.

---

### Post by ccaazz on 2007-09-23
well, ubuntu installed without a hitch, so the alternate install disc isn't needed is it?

this is the message i get whenever i try to start using ubuntu now though, i tried rebooting too, but keep getting this message.

---

### Post by Pumalite on 2007-09-23
Go into Recovery Mode and at the command line:

sudo apt-get install gnome-desktop

---

### Post by ccaazz on 2007-09-23
didn't work, i don't have internet access right now, until i manage to get into ubuntu to install my wifi card drivers.  I don't seem to be the only one with this problem, infact seems to be rather common, yet i havent found a single solution to it?

---

### Post by Pumalite on 2007-09-23
Get wired to Internet and try what I told you. Configure your wireless later.

---

### Post by ccaazz on 2007-09-23
sorry, but im afraid thats not possible, will have to try another way then

---

### Post by Pumalite on 2007-09-23
Re-install then and cross your fingers. I would follow this first:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

