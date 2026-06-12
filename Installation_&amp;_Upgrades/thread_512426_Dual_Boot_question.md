---
title: "Dual Boot question"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by edu2004eu on 2007-07-29
I am currently using Windows XP and Ubuntu 7.04 as a dual boot. Thing is, I want to reinstall my windows (because it's got viruses -- typically) but I can't because of the following reason: as soon as I reinstall windows, the windows boot manager overtakes GRUB and will boot directly on windows and the only solution for that is to reinstall Ubuntu also... but I don't want to do that... So is there any way to reinstall windows and keep my current Ubuntu installation & settings?

Thanks, GB.

---

### Post by manndani on 2007-07-29
If you look at this thread (compliments to "Catlett") 
[http://tinyurl.com/2kmugw](http://tinyurl.com/2kmugw)
Great instructions for re-doing grub from the live CD, really good instructions & easy to follow.
I've used it and I'm greatly in "Catletts" debt, saved me a heap of hassle.

---

### Post by edu2004eu on 2007-07-30
Yup, exactly what I needed. Million thanks :D

---

### Post by MQMike on 2007-07-30
And another one

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(by yours truly)

and the classic:
Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)


Your problem is very easy to fix -- just need to re-install GRUB using three GRUB command, root -- setup -- quit.  See How-To's.  Write back for help if there's a glitch.

--Mike

---

