---
title: "How can I change the updates to NOT use /boot"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by DAE51D on 2007-10-30
I tripple boot my system with XP, Gentoo and now Ubuntu 7.04. Everything was working fine. I share the /boot between the two Linux. 

Now I'm trying to update and Ubuntu wants to dump all these files into /boot !!

WTF!?!

Why would ANYONE think it was smart to use /boot (which is typically a very small read-only partition on most other Linux flavors). Why not use /tmp or /var/tmp or some other sane location? OR how about the standard /var/cache/apt/achives -- where apt get puts EVERY OTHER FREAKIN .deb FILE! Or better still, why wouldn't your updater PROMPT me to pick a location to save the files to, and then work from there? 

:confused:

So, I download the 'alternate' .iso, make a CD, and try to upgrade using that. I tell it to NOT download updates from the internet, and the stupid thing STILL can't install as it needs 52.4MB on /boot. UGHHHH! 

I can't umount /boot (so I could just relink it to / or something) as "device is busy". So basically I'm screwed.

I'm new to Ubuntu and was thinking of switching to it from Gentoo, but this kind of assinine logic makes me have second thoughts.

Help?

---

### Post by dabl on 2007-10-30
> **DAE51D said:**
> 

 can't install as it needs 52.4MB on /boot. UGHHHH! 



I would never argue with your view of "the way things ought to be", but gee-whiz, hard drive space is 28 cents per Gigabyte, so my calculator says that you're letting 1.5 cents' worth of disk space be an impediment.  How is that logical?  :confused:

---

### Post by DAE51D on 2007-10-30
That's all fine and dandy to say NOW, but the fact is that is how the partitions are set up. Therefore, without resizing partitions, I have no way of upgrading this Ubuntu. Furthermore, as mentioned, most distros only use /boot as a read only tiny partition to simply do what it says "boot" the system (hold vmlinuz, grub, etc).

---

### Post by dabl on 2007-10-30
I realized after I posted that your time to change the partitioning is probably a million times more valuable than the 1.5 cents.  Sorry.

Can you just install Gutsy over 7.04?  You'll lose your custom settings, of course. :(

---

### Post by psusi on 2007-10-30
Because it is upgrading things that go in /boot, like the kernel.  

Try removing some old kernels to free up space.

---

