---
title: "Slow boot-up with Karmic"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mikeblah on 2009-10-09
I have just installed Karmic beta. It takes twice as long to boot (53secs) than Jaunty. Is this correct or could it be a bug?

---

### Post by xdemo on 2009-10-09
Well i would be pretty sure its to do with it being a beta still... It could be a temporary issue until it gets updated.

---

### Post by conorsulli on 2009-10-22
Mine takes nearldy 1.20 to reach the desktop, Jaunty used take 32 seconds..... Its that stupid swooshy xsplash I think and kernel mode setting but im not sure.... both my karmic installs are a lot slower to boot compared to jaunty to be honest.

---

### Post by Seren on 2009-10-22
> **mikeblah said:**
> I have just installed Karmic beta. It takes twice as long to boot (53secs) than Jaunty. Is this correct or could it be a bug?

If this is your first boot under karmic, sreadahead has not yet optimized the boot process, it should be slightly better in the following boots.

---

### Post by the.lost.one on 2009-10-22
true for me too. jaunty's boot was like linux. karmic is windows. in fact fresh windows 7 RC boots faster. and i hate it when i get two splash screens. but its shutdown is insanely fast. takes only a few seconds. faster than jaunty.

---

### Post by dino99 on 2009-10-22
hi guys,

the main problem is grub2 prefer (need) mbr of 1st disk. if it's installed on other places that work but it scan all the partitions of all disks.

---

### Post by CookieNinja on 2009-10-22
I have a similar experience. I've only got 1 HD and going on memory, my install is on the first partition.

My boot time has gone from around 35 seconds (according to bootchart) to somewhere between 90-110 seconds. The spec of the machine isn't a monster, but it's not poor either.

It's got:

3400+ AMD (?Athlon?) mobile CPU
2.5GB RAM
160GB 5400rpm SATA drive.

When I get the chance, I'm going to try a fresh install to compare the difference, and then go over the bootchart after that to see what's causing the dreadful performance.

For what it's worth, if grub2 has a major role in this issue, it's rubbish and needs removing until it's fit for purpose.

It's almost as if I've installed Vista by mistake :(

---

### Post by Ric_NYC on 2009-10-22
The slow boot is a "feature".


I noticed that same issue with the boot. I hope that's not the new oficial boot.
Jaunty has a faster boot. Two steps backwards?

---

### Post by JeyPeyy on 2009-10-22
In alpha 6 I think it was quite fast, but since they added that usplash thing before the xsplash, it slowed everything up. Great disappointment indeed. I don't think it will be fixed in final release because we're at the rc soon.

I hope 10.04 will get faster! This really s*cks

---

### Post by doomsword2001 on 2009-10-22
weird my boot time isnt that bad. or at least i havent noticed 0.o. but does it really matter if its 30s+ ? i believe that when a pc boots its time to go make a coffee, roll a cigaret or smth like that :)

---

### Post by MacUntu on 2009-10-22
Not changed for me.

---

### Post by philinux on 2009-10-22
Everybody should install bootchart to get a proper speed check and to see whats going on.

Mine says 1min 2secs.

---

### Post by kestal on 2009-10-22
> **doomsword2001 said:**
> weird my boot time isnt that bad. or at least i havent noticed 0.o. but does it really matter if its 30s+ ? i believe that when a pc boots its time to go make a coffee, roll a cigaret or smth like that :)

Thats a PC, what about laptops? I need to turn mine off a few times during the day, so waiting an extra 60-80 seconds to boot it back up is not fun, especially when jaunty does it in 30. So yes, it does matter. Its also part of the whole 'boot experience', as Jaunty booted up quicker. Not to mention with 1min+ for my boot, the live CD boots just as 'fast'.

---

### Post by doomsword2001 on 2009-10-22
i was talking about a laptop, but in the end, the same thing is less annoying for some people and more annoying for others.

---

### Post by kkkkdddd on 2009-10-22
I have already made a topic about slow boot of Karmic:

[http://ubuntuforums.org/showthread.php?t=1296468](http://ubuntuforums.org/showthread.php?t=1296468)

I attached bootchart there (it is compressed with tar).

Can you help me to make it at least a bit faster?

I do not use GRUB 2 and EXT4. Why it is so slow?

---

### Post by KrazyPenguin on 2009-10-22
my bootup after a fresh install and upgrades is now under 50 seconds.
I shed about 15 seconds from my previous install of Karmic.
With some tweaks i'm hoping for under 40 seconds.

This is better than Jaunty on my computer.

---

