---
title: "Black screen instead of login after Hardy upgrade"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by 99of9 on 2008-07-10
I've just upgraded my desktop from gutsy to hardy (8.04 LTS), but am unable to log in because when the login screen should appear, I get only a black screen (most of the time... apparently slightly random).  At that point, pressing ctrl-alt-f1 doesn't do anything, so I just have to do a hard shutdown.

When I use the Live CD, I often have the same problem, but am ok if I use the safe-graphics mode.  So I figure it's something to do with my graphics driver / xorg.config / something like that.

I have an "Intel corporation 82 Q963/Q965 Integrated graphics controller", and I think that means I have to use the "intel" driver (I think I was in gutsy).

I've tried dpkg-reconfigure xserver-xorg.  Same problem. (xorg.conf now just has very generic stuff in it, and doesn't seem to specify intel)

I also stripped back my gdm.conf-custom (some web searching suggested that might help), but no change.

I would appreciate any help, and am happy to answer questions.

---

### Post by Partyboi2 on 2008-07-10
What happens if you boot into recovery mode and choose xfix?

---

### Post by drahmin on 2008-07-10
Hi.I've tried xfix but nothing happened again, still have the same problem.The writing on my screen says; cannot display this video mode please change the resolution to bla bla..
I hope this ain't a real-noob question :confused:
Everything was allright with my "perfect" sis video card as 2d.But i guess i made something wrong :confused:
But someone please help, i can log in but i'm totally blind :(

---

### Post by candtalan on 2008-07-10
With one of my machines I get something rather similar to this. It is a dell inspiron 1100 laptop, and I tried a lot of things, with no good result. The display woul dcome up normally on many occasions, in this case, however, there were also many occasions when it did not. 
Playing tunes on ctrl alt F1 (or F2, 3, 4, 5, 6) was sometimes useful and shoewd that the xserver was running, and then ctrl alt F7 would sometimes give a display.
Sometimes ctrl alt backspace restarted and configured ok, sometimes not. It also uses intel graphics chip, th etraditional driver would have been i810.

I gave up eventually an dcopy pasted an entire (old) xorg.conf into it which works :-)  however this i sa file which I have continually used in this particular machine for a long time, because of graphics problems

fwiw my working file for this laptop is attached

---

### Post by 99of9 on 2008-07-10
It turned out I had hit a bug in the kernel or intel graphics card driver.  I think it is the same as this one:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223870](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223870)

In the end, what fixed my black screen was switching from using the "intel" driver to using the "vesa" driver, a one word change in my xorg.conf.

I'm not sure the others on this thread have the same problem as I did.  I didn't get any error "writing on my screen".  I also couldn't use ctrl-alt-F1 ... it didn't do anything, the whole computer was frozen.  Good luck finding your fixes too.

---

