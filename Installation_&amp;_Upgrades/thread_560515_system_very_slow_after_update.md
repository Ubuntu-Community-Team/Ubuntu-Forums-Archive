---
title: "system very slow after update"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by bikezilla on 2007-09-26
I have an hp nx9010 laptop (old stuff, celeron 2.6, 256 sdram, 40gigs), and looking for linux distro light and fast enough.
Today i installed ubuntu fiesty, right after installation everything  ran perfectly well, normal start-up times, fairly fast response times. 
It then showed up 117 updates, so installed all of them.  After restarting the system a very annoying problem appeared - login screen loading, gnome loading and application start-up times are UNBEARABLY slow.
Gnome menus and applications run fast and smooth, but start-up takes ages :(
So, what to do? I have little experience with linux.

I can post a log of what was installed during update, it's long though...

p.s. i thought of reinstalling ubuntu  right away, but that's so MS-like :(

---

### Post by reckless2k2 on 2007-09-26
well the updates that ran were update to newer kernel. you still have the old kernel. hit esc on boot when it prompts you to view the grub menu and pick the older kernel. the top and 2nd will be new kernel and 3rd and 4th will be older. you don't want to boot into recovery mode.

---

### Post by bikezilla on 2007-09-26
yep, telling grub to load the old kernel solved the issue. 10x a lot.

p.s. while having the new (2.6.20.16) kernel listed in GRUB's menu.lst,  it (grub) also loaded considerably slower, while after removing the new kernel entries it was fast again. Wierd stuff:confused:

---

### Post by Plastic on 2007-09-29
the same problem for me, but for me the kernel version trick didn't worked. and one more thing when i did the update i had this error something with fonts and it told me something about configuring (just can't paste it here because i don't coped it).  So anyone could help me? 

p.s. my laptop parameters: c2d T7300@2.0Ghz, 2Gigs RAM, sata 200Gigs, nvidia 8400M G.

---

