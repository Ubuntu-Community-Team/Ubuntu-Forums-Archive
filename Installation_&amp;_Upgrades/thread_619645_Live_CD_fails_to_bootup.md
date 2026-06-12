---
title: "Live CD fails to bootup"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by iphail on 2007-11-21
Ok I just got the 7.10 live CD in the mail or w/e and I tried to boot up through it and it tries to load but eventually when the progress bar stops moving back and forth and starts to just go across like a loadin bar usually would (I cant explain this well) after about 3 1/4 blocks it freezes, CD stops spinning and if i leave it there it still wont go. I read around the forums but I couldnt find much to help.

Some of my system specs:
System Manufacturer:       HP Pavilion 061
System Model:              PS583AA-ABA a1020n
System type:               X86-based PC
Processor(s):              1 Processor(s) Installed.
                           [01]: x86 Family 15 Model 4 Stepping 1 GenuineIntel ~3066 Mhz
BIOS Version:              A M I  - 1000623
Total Physical Memory:     1,527 MB

---

### Post by anton_pm on 2007-11-21
I get the initial menu where you select to start the live CD, kernel loads, then nothing. I'm running a Dell GX240

---

### Post by Rev60073 on 2007-11-21
Try booting with Safe Graphics mode :popcorn:

---

### Post by anton_pm on 2007-11-21
I gave that a go, no joy either :( Just get the flashing cursor either way

---

### Post by Pumalite on 2007-11-21
Try the Alternate CD.

---

### Post by anton_pm on 2007-11-21
Still get the same thing from the alternate CD: flashing cursor

---

### Post by Pumalite on 2007-11-21
Find out if you have an Intel 965 chipset because that could be your problem.

---

### Post by anton_pm on 2007-11-21
It's a Dell GX240, so looks like it's 845

---

### Post by Pumalite on 2007-11-21
Try your CD's in a different computer, clean the lens of your burner, do md5sum on your iso before burn, check you CD for integrity before install, use good quality CD-R media.

---

### Post by anton_pm on 2007-11-22
Just used the same disk to install on another machine, worked ok

---

### Post by tomcullpepper on 2007-11-22
Having the same problem on HP 6000 series notebook with AMD processor X2 Turion 1.8 GHZ, what the hell?  I have two copies of ubuntu burned at different speeds, and one officially tested version of Sabayon, Ubuntu does the same as this guy, but Sabayon freezes after the bar completes and it says "Initializing Kernal"

---

### Post by Pumalite on 2007-11-22
Try a different distro and see if you are incompatible with Linux or just Ubuntu.

---

### Post by anton_pm on 2007-11-23
Think this could be something to do with it:

[http://ubuntuforums.org/showthread.php?t=543148&highlight=gx240](http://ubuntuforums.org/showthread.php?t=543148&highlight=gx240)

I've heard about these acpi issues before. Stops a shutdown finishing on 7.04 which is installed at the moment

---

