---
title: "Recommendations on designating WinXP+Ubuntu hard drive space for partitions?"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by Th3Professor on 2008-03-04
Let me know what you think of this...

40g drive...

The 1st install: 6g partition for WinXP Pro (or Home).
Then install: the rest (~<34g) into Ubuntu Studio.

On the XP side, all I want to do is play 1 game, space is 1.5g - 3g.
Considering that, then considering 3g - 3.5g for XP...
would it make a difference if I put XP on a partition "c:" and the game on a partition "d:"?
(Probably something like 3g+3g or 4g+2g?)
...or would it be better to just leave it at one partition of 6g?

On the Ubuntu Studio side, I'd like to minimize swap, though I'm guessing 256megs might be too low.
Would it still do well if I just did the "/" and "/swap" partitions (not several)...
putting 512MB into "/swap" and the left-over ~33g into "/"?

Here's my dmesg cpu info:
cpu0: Mobile Intel(R) Pentium(R) 4 - M CPU 2.40GHz ("GenuineIntel" 686-class) 2.40 GHz

(I know people say 2xRAM or something along those lines but honestly I don't think going over 1g is necessary, nor do I think that even going as high as 1g is necessary... the trick is figuring out how low I can go without sacrificing performance.) (And I'm trying to get away with the minimal WinXP install for that silly game ("wine" (and other like apps) is not an option) while still trying to squeeze in as much hard drive space as I can for Ubuntu Studio (aka recording and editing audio, aka eating up tons of space.))

Thanks for recommendations! :)

---

### Post by Rocket2DMn on 2008-03-04
Hey, first you should have at least as much swap as RAM, so if you have 1 GB RAM, have 1 GB at least of swap - this is necessary for the hibernate function as well.
I would keep all your windows stuff on one partition, but I'm not sure 6GB is enough with how bloated windows is (esp. with updates and service packs which you should install).  I would say 8GB or so would be safer.  The rest you can give to Ubuntu.
For recording and editing, an external hard drive might prove itself very useful so don't have to constantly worry about space restrictions, but that's just a suggestion :)

---

### Post by mozetti on 2008-03-04
Here's how I'd do it:

hda1 - XP, 6-8 gig
hda2 - Linux, 6-8 gig
hda3 - Linux-swap, 1 gig
hda4 - /home, the rest

---

### Post by rolnics on 2008-03-04
I would give XP a little more room, i think you'll run out of space rapidly if you only have 6gb for it, I would suggest at least 8gb like mention above or 10gb, and you will need the same amount for you swap as you have ram. As for your linux all looks good, I personally have mine setup with /(root) 10gb and the rest for home.

---

### Post by Rocket2DMn on 2008-03-04
> **mozetti said:**
> Here's how I'd do it:

hda1 - XP, 6-8 gig
hda2 - Linux, 6-8 gig
hda3 - Linux-swap, 1 gig
hda4 - /home, the rest

I like that setup except for having a separate /home partition.  While this is useful for many people, on a drive as small as this one, he would be unable to take full advantage of the available space because there will always be space left on each partition.  When all the linux stuff (/ and /home) are in one place, there is is just one chunk of free space which can be more easily maximized.

---

### Post by Th3Professor on 2008-03-04
If I could, I'd use Sun/Solaris' ZFS file system - pools and zones - then the partitioning wouldn't be a concern at all. Supposedly there's a way on fuse/linux, though I won't be going the route.

I'll definitely go ahead and simplify things with what I have (including throwing all non-swap space into 1 partition for Ubustu).

From past installs, 8g was more than enough for WinXP, and I had left-over (wasted) space. That's after installing XP, SP2, one anti-virus app, 2 anti-spyware apps, and 1 game (Maple Story). I have no use for that operating system otherwise. ;)

Maybe I will opt for 8g again (if anybody thinks 7g might work, I'm all ears).

Is 1g swap *really* necessary, as in *required*? My current swap on my OpenBSD Unix is only a few hundred megs and I have never had any problems. It runs fast, smooth, it's great. Also, I may not use "hibernation" on the laptop.

Could I get away with ~500MB (512MB) for /swap?

---

### Post by Rocket2DMn on 2008-03-04
It's not required, but it allows for increased performance, and if you ever want to hibernate your computer, you will need to match your RAM size.

---

### Post by Th3Professor on 2008-03-04
I won't be hibernating my laptop... I'll just stick to the old-school on/off boot/shutdown stuff.

How likely is the swap going to be used anyway?

Maybe there's a difference between the Ubuntu Linux system and, say for example, my current OpenBSD Unix system, in general memory usage. My "swap" space just sets there as wasted space.

Does Ubuntu let you increase/decrease the amount of swap space after install? Is there an app for that?

(I might go with 500m or 1g, and later decide to change it if Ubuntu lets me.)

Thanks!

---

### Post by Rocket2DMn on 2008-03-04
You can always resize partitions, but it's a bit of a hassle, it's better to get it right to start with.  If you really don't want that much swap, nobody is putting a gun to your head.  Swap will be used when you start using up your RAM which is likely to happen if you are doing serious video and audio editing, but you surely know this.  Go ahead and do as you see fit, it's your computer, we're just offering our suggestions, and it would be foolish to think we all feel the same way.
Happy installing!

---

### Post by Th3Professor on 2008-03-05
i'm on ubuntu now... i went ahead and put 1g in swap.
...my 7.10 cd wouldn't install, there was ONE faulty file. i had a 7.04 cd so i just installed that.
now to move it up to 7.10, definitely need to do that before i put studio on.

---

### Post by ferdostar on 2008-03-05
In fact you can put a smaller swap partition and tweaking your performance by reducing your swappiness values which controls the degree to which the kernel prefers to swap when it tries to free memory. On the other hand you can always add more swap, by making a swap file. But off corse like others said it's better to have a bigger swap on start, but it's not necessary. Your choice. You can look [https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq") for more information. Cheers!

---

