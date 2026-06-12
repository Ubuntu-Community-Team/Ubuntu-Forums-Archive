---
title: "Ubuntu 10.04 Boot from liveCD"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by Tobis84 on 2010-08-23
Need a little help here.

When I try to boot Ubuntu 10.04 64-bit it seems to load in a normal fashion untill the final menu where you select 'Install', 'Test CD' and the like.

This screen is only showing a really distorted image of the graphics meant to be on screen with no obvious chance of moving on.

My system is:
Intel T4300 64-bit Dual core 2.1GHz
Nvidia GeForce G102M
4GB RAM

Any suggestions?
Could be great to get this up and running this week.

---

### Post by lechien73 on 2010-08-23
Does the installation freeze at the menu? If you can still use the menu - but just can't see it properly, then press Escape and then Return. This will drop you to a boot: prompt.

Press the Return key again, and the text-based installer will start up.

To get it to start properly, you may have to press Tab on the first menu entry, and add the parameter **nomodeset** after 'quiet splash'

Hope this works for you :)

---

### Post by Tobis84 on 2010-08-25
I'm afraid this had no effect. It's like it just stopped at that odd looking screen.

EDIT: The same error occures with a 32-bit edition of Ubuntu 10.04

---

### Post by Tobis84 on 2010-09-02
I've downloaded the alternate CD and going through the text-based installer, but this got me quite uneasy with the partioning and the like.

Does anyone know about a tutorial on how to use the text-based installer to end up with the same result as the graphical installer?

Quick respons will be much appriciated.

---

