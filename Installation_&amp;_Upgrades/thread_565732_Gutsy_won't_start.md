---
title: "Gutsy won't start"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by pauwl on 2007-10-02
OK, admittedly should've tested the live CD first but....

I've a Gateway MT3421 with AMD Turion64.
Feisty was working just fine, but I had to download the latest ALSA stuff to get the audio working, even then the built-in speakers didn't work.

Of course excited about the new ALSA in Gutsy, so I upgraded...

There are 4 Gutsy entries now in Grub, the first 2 (.22. version) don't work. The first just immediately hangs, the second (sometimes) gets me to the prompt, but dpkg-reconfigure xserver-xorg won't help het gdm running again.

The (.20.) other version works. However... can't get my NDISWRAPPER version of net8185 running, the hardware is no longer detected.

So here's the question: How can I (in .20. version) get NDISWRAPPER to recognise the net8185 hardware again like feisty did?

I know putting feisty back is a solution, but what else can I try?


Pauwl

---

### Post by Pumalite on 2007-10-02
Wait 2 weeks for Stable and do a clean install after saving your data.

---

### Post by soaro77 on 2007-11-04
Yeah good luck with that. I also thought Gutsy would have been tested well with laptops and upgraded my Gateway MT3421. Same thing. Nothing will start using the newer kernels. When I try in recovery mode I get kernel panics. Booting into the second kernels isn't an option either because half the hardware doesn't work, including the network. Just for grins I burned the Gutsy CD and tried booting it to see if I could do a fresh install. It won't even boot at all. The orange bar bounces back and forth a little bit then just stops and nothing else happens.

So I'm going back to Fiesty until I see that Gutsy has been tested better and is working with laptops.

---

### Post by Pumalite on 2007-11-04
It seems it depends on hardware. I have Gutsy in 5 computers working fine.

---

