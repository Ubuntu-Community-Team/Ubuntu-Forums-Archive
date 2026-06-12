---
title: "Lubuntu fails to boot after applying upgrade  (13.04 -&gt; 13.10)"
date: 2013-12-02
forum: Installation &amp; Upgrades
---

### Post by edburns on 2013-12-02
I had a perfectly fine Lubuntu system on my olp Dell Inspiron2650 laptop.  I was feeling 
adventurous today so I said yes to the "Upgrade to Lubuntu 13.10" dialog.  I regret
this decision.


Now the system does not boot.  Thankfully, the GRUB config saved aside the old kernel,
so I am able to type this, however, I would like to complete the upgrade successfully.


Here is what I observe.


The system freezes after the "Loading ramdisk" line when left to boot with the new,
default, configuration.  Here are some specifics.


Hardware: Dell Inspiron 2650 Laptop


New Lubuntu version: 13.10
New kernel version: 3.11.0-13-generic


Old Lubuntu version: 13.04
Old kernel version: 3.8.0-33-generic


Any ideas?  I am always suspicious of GNU/Linux OS upgrades, and this experience
reminds me why.


Thanks,


Ed

---

### Post by sudodus on 2013-12-03
I would suspect that there is some hardware driver, that does not work or is dropped in 13.10. Please specify your

- graphics chip/card
- wifi chip/card/dongle

I can understand that you want to upgrade from 13.04, because its end of life is January 2014. If your system works with 12.04 LTS, you can try that (but you need to re-install because there is no automatic way to downgrade the version number). Lubuntu 12.04 has passed end of life, but

Xubuntu 12.04 has LTS until April 2015 (three years).

There are also several tweaks, re-spins or distros based on Ubuntu 12.04 that promise LTS until April 2017 (five years),

Precise Gnome Classic Tweaks
LXLE
Bodhi linux
Bento Ubuntu-Remix

See also the beginning and end of this Ubuntu Forums thread [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

---

### Post by edburns on 2013-12-03
Thank you for your reply.  Here are the answers to your questions:

Graphics: [COLOR=#39434D][FONT=Helvetica]AGP 4x - NVIDIA GeForce2 Go 100
Wifi: none, just using the built in ethernet.

I hope this helps you help me!

Ed[/FONT][/COLOR]

---

### Post by sudodus on 2013-12-03
According this link [https://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units](https://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units) it is a very old graphics card, which makes me think that you have the best chances with a system based on Ubuntu 12.04 LTS (see post #2). It also depends on the RAM available. I would say you need at least 512 MB.

---

### Post by mörgæs on 2013-12-03
Have you tried Lubuntu 13.10 in a live boot?

---

