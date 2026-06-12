---
title: "perpetual reset after flawless install (6.06 and 7.04)"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by g[r]eek on 2007-07-21
hello all

i'm using an old school compaq presario 1200 laptop, purchase around 1998/1999.
- CPU: AMD-K6-2/500 (whatever that means. it's probably around a gig but i dont know)
- RAM: 128mb

also, i read on the dapper and feisty server docs that 128mb of ram is ample to get ubuntu server up and running. i tried installing both dapper 6.06.1 LTS and feisty 7.04.

both install perfectly. at the end of isntallation, my cd-rom drive is ejected (as per usual), and then i press ok to reboot.

however as soon as it passes the BIOS screen phase (and the 3 second long GRUB phase), it says "Starting up..." and then immediately reboots.

i am busy watching it reset perpetually as i type this post (drama). both dapper and feisty do this.

any ideas?

ps: a friend suggested i edit the command-line and set apci=off but that didn't do the trick.

---

### Post by rillip on 2007-07-21
Try editing the line and removing the quiet splash section so you can see what's happening

---

### Post by kvonb on 2007-07-21
It's the kernel, see my thread here:

[http://ubuntuforums.org/showthread.php?t=455884](http://ubuntuforums.org/showthread.php?t=455884)

The default one doesn't have support for some older CPUs :(.

---

