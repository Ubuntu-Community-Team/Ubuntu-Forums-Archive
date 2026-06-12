---
title: "[SOLVED] Upgraded to Gutsy and now have 1 CPU instead of 4"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by bretto_40 on 2007-10-28
Hi,

I recently upgraded to Gutsy from Feisty (and Edgy earlier on).

I've always been able to see my 4 CPUs (Core 2 Duo Quad Core) in the System Monitor; but after the upgrade I now only see one CPU. I came across another thread where a guy had lost one of his dual core CPUs and fresh installed using the AMD64 version.

I don't want to have to re-install, and I'd rather stay on the x86 version.

Surely this must be some kind of bug with some kind of fix somewhere? It was working before OK, after all.

Any help would be muchly appreciated! :confused:

---

### Post by reyasuk on 2007-10-28
I'm only a newbie but I had a similar problem with my dual core and with a bit of googling I found these solutions.  Editing the menu means I now boot to generic without having to think about it! I hope this will be helpful for your too.

[http://ubuntuforums.org/showthread.php?p=3567198](http://ubuntuforums.org/showthread.php?p=3567198)
[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/) source/hal/ bug/149881

jen

---

### Post by bretto_40 on 2007-10-28
Thanks for the tip, however this isn't working for me either, well it is, but it isn't.

Problem is that if I boot into the generic version of the Kernel I have display problems, and no matter what I do to fix these (fixed them with my i386 version of Kernel), I can't fix them.

So basically, when I boot up into the default i386 version of the Kernel everything works fine, but only 1 CPU.

If I boot up into the generic version it has display problems, runs in low graphics mode, I have to use the Vesa driver to get in, and great 4 CPUs, but Open GL doesn't work and can only get max 800 x 600 resolution.

My usual fix of copying my known good xorg.conf file doesn't work, yet it works perfectly on my i386 install.

I don't know.  ](*,)

Anyone have any other suggestions?

---

### Post by Handssolow on 2007-10-28
It seems the upgrade to Gutsy defaults to -386 so only one cpu becomes active. I had to alter Grub to select generic to use both my AMD Athlon 64 x2 cpus. I suggest the resolution / graphics problem requires a different solution.

---

### Post by bretto_40 on 2007-10-29
Problem now solved.

Solution was of course to boot up into the generic kernel.

I managed to solve my display issues after extensive fiddling around and some investigation on the Nvidia website.

Thanks everyone for the help.  :)

---

