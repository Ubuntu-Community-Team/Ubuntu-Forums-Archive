---
title: "Computer keeps rebooting instead of installing"
date: 2005-07-07
forum: Installation &amp; Upgrades
---

### Post by etorres on 2005-07-07
Hi, I just got ubuntu today. I can't get it to install. The computer just keeps rebooting 
over and over again.The cd won't load at all. I think it is a ram problem but that computer has 50mb of ram and ubuntu needs at least 35mb. Anyway thats my problem. I hope someone can help. Just in case here is more info on my pc.
 pentium 133mhz 
 I don't know what else to put   Thanks

---

### Post by javiadip on 2005-07-07
Yea it could be your RAM, even if it worked, your linux is gonna run slow coz Desktop environment will take up so much RAM specially gnome. I would suggest you upgrade the RAM if you are planning on installing ubuntu.

---

### Post by etorres on 2005-07-07
Thanks

---

### Post by mingus on 2005-07-07
With that age of hardware, it could be other conflicts, as well . . . try using a kernel arguments to disable the most common problems:

:linux acpi=off noapic nolapic debian-installer/framebuffer=off

or

:linux nodma pnpbios=off pci=bios nousb noapm noscsi

To give the installation more RAM, use a live-cd to pre-partition the disk.  Create a swap partition.  The kernel should find and use it.

You won't be able to use Gnome or KDE with that amount of RAM.  Even XFCE would be slow.  But you might be OK with Windowmaker or Fluxbox.

---

### Post by RJARRRPCGP on 2005-07-08
An unstable processor overclock can cause this symptom, too!!!

If you're overclocking, it's not a good idea to do so, unless you know that it's stable.  [-X

---

### Post by WildTangent on 2005-07-08
alright, dude, wtf is with all the !!!'s? i see them in all your posts. i dont think hes overclocking, based on the low amount of RAM he has...stop trying to act like you know what youre talking about, the !!!'s ruin your credibility

-Wild

---

### Post by etorres on 2005-07-08
I think I'll just keep using rh7.0 till I get a better computer. kde and gnome run just fine with that computer. Thanks

---

### Post by mingus on 2005-07-08
[QUOTE=etorres]I think I'll just keep using rh7.0 till I get a better computer. kde and gnome run just fine with that computer. Thanks[/QUOTE]

Well, can't beat that!  That's great.

---

### Post by RJARRRPCGP on 2005-07-08
[QUOTE=WildTangent]alright, dude, wtf is with all the !!!'s? i see them in all your posts. i dont think hes overclocking, based on the low amount of RAM he has...stop trying to act like you know what youre talking about, the !!!'s ruin your credibility

-Wild[/QUOTE]

Stop flaming me. Now I see that you're going to turn this post to a flame thread.  :mad:

---

### Post by WildTangent on 2005-07-08
Im not flaming anyone, im only suggesting how you might display a more professional image, because as is, i would take any advice you give with a grain of salt.

-Wild

---

