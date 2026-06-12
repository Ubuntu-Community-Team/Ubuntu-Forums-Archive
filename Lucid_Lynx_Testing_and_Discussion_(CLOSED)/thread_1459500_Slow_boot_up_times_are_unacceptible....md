---
title: "Slow boot up times are unacceptible..."
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by brucewagner on 2010-04-21
Call me anal. Tested 10 times: Ubuntu 10.04 Lucid Lynx. Avg Boot Time: 21.3 seconds, Avg Shutdown Time: 4.9 seconds incl Transmission start!

:)

---

### Post by Merk42 on 2010-04-21
First off, you do know that the "10 second boot time" is for people with SSDs right?

Second, install pybootchart and post the results here or preferably [here](http://ubuntuforums.org/showthread.php?t=1343305) to see what, if anything, can be done

---

### Post by cariboo on 2010-04-21
What are your specs? On this system:

[list]
[*] K9N6PGM2-V
[*] AMD X2 3800+ cpu
[*] 2Gb ram
[*] Nvidia 9400GT
[/list]

I get consistent 20 -21 second boot times.

On my system at home:

[list]
[*] K9N6PGM2-V
[*] AMD X2 240 cpu
[*] 2Gb ram
[*] Nvidia GT210
[/list]

I consistently get 15 -16 second boot times

My Compaq Mini 110 netbook, between 21 - 23 seconds, this one doesn't get rebooted very often though, the last time was last week, and I've done several updates since.

---

### Post by brucewagner on 2010-04-21
(1)   I was really just joking about the boot time being unacceptible.  I think it's AWESOME!!!  Only 20 seconds! 

(2)   I installed pybootchartgui  (the only thing that comes up matching pybootchart in synaptec)  but I don't know how to use it.  Where do I find it?

(3)   My system specs are:

"Gateway Phenom X4 64"
AMD 64-bit Phenom 9150e Quad-Core Processor
4GB RAM
ATI/AMD video  (not sure which)

---

### Post by tjeremiah on 2010-04-21
well ive been testing Lucid with Wubi and my boot up time is sometimes less than 10 seconds/no more than 15 seconds.

---

### Post by cariboo on 2010-04-21
Look in /var/log/bootchart, you should see several png files, depending on how often you have rebooted.

---

### Post by dyltman on 2010-04-21
Got 21 second boot and in 1-2 of those seconds plymouth is running.

---

