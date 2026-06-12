---
title: "dell optiplex gx270 boots to blank screen"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by terry_gardener on 2010-08-16
my next door neighbour has a dell optiplex gx270 and wanted ubuntu installing.

hardware: 
1gb ram 
p4 2.4 (i think)
intel 82865g onboard graphics. 
40gb HDD 

i tried the live cd and it froze on bootup, so i thought it might not be enough ram as the case sticker said 512mb ram.
so i booted the minimum install cd and installed ubuntu desktop on it and then rebooted, when it boots i get grub and then screen will either do 1 of 2 things.

1. i get another flashing cursor in top left corner and then cursor stops flashing and then nothing happens at all.

2. then screen will go black and nothing will show at all. 

i have tried updating the BIOS, adding i915.modeset=0 to grub, didn't work either. 
also couldn't find the xorg.conf under /etc/X11 to change driver to vesa. 

after several reboots atleast 30 since the check disk think showed and then it froze again. it booted correctly so i tried the latest intel driver from xorg edgers ppa.

rebooted and still the same thing happens. tried 2 different installs now and get same results.

i have had to put winxp on it so he can atleast use it, but this will run out in 30 days unless he decides to buy it.

any ideas

---

### Post by mörgæs on 2010-08-16
Does it boot with a 9.10 live CD?

---

### Post by terry_gardener on 2010-08-17
> **mörgæs said:**
> Does it boot with a 9.10 live CD?

no fails at the purging gdm session section (well this is the last line in the text that appears)
then doesn't do anything.
check disk for defects and no errors found.

---

### Post by mörgæs on 2010-08-18
In 10.04 there have been lots of problems with Intel graphics chips. It you don't mind experimenting you could also give 10.10 (alpha) a try. 

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

You know the warnings: This is a release in development and is likely to change without notice (and so on).

---

### Post by terry_gardener on 2010-08-18
i will try 10.10 tonight.
i did try 8.04 LTS and that worked ok, but would like to install something more modern.

---

### Post by terry_gardener on 2010-08-18
tried 10.10 alpha 3 and it also doesn't work, livecd doesn't load and the install section doesn't load either. 

i even tried upgrade from hardy to lucid but get same problem. 

i have also tried opensuse 11.3 doesn't work either. 

i have officially give up and installed win xp home sp3 30 day trial.

---

### Post by spcwingo on 2010-08-18
> **terry_gardener said:**
> i have tried adding i915.modeset=0 to grub

Have you tried:

```
i915.modeset=1
```

I have a Dell inspiron 1150 laptop that will give ZERO video output unless I use the above.

You could also try:

```
xforcevesa
```

---

