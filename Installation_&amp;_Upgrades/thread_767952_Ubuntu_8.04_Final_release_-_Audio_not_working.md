---
title: "Ubuntu 8.04 Final release - Audio not working"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by mig_l on 2008-04-26
For my surprise audio is not working :(

My motherboard is a Asus P5B-Plus Vista Edition, and the audio chip vendor is Analog Devices, [AC97Codec], it worked in gutsy... 
(i did not upgrade i did a clean install.)

I'm sure [alsa]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Analog_Devices") supports my audio card, but i dont know how to make it work...
Can you please help me?

---

### Post by mig_l on 2008-04-26
:(

---

### Post by rennen01 on 2008-04-26
have you tried alsamixer and seeing if anything is muted?

---

### Post by mig_l on 2008-04-27
This is the output:
```


alsamixer: function snd_ctl_open failed for default: No such file or directory


```

:(

Some more information:

asus p5b wich has a ICH8 chipset (using snd-hda-intel module for sound)

lspci:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

dmesg:
[   51.033806] HDA Intel: probe of 0000:00:1b.0 failed with error -16


the System->preferences->Sound devices list is empty.

...
Please help

---

### Post by gantellus on 2008-05-04
same hardware, same problems, same outputs... and no solution yet.. :(

---

### Post by chrisneedshelp on 2008-05-04
sorry I can't help at all, but I have the same problem, using a sound audigy card for my 5.1 and no sound with hardy

i'm a first time ubuntu/linux user, so i'm still learning, but I find that if i ran the hardware test the test sound I could hear, and the little jingle when it's loaded and waiting for my log in, but no sounds what-so-ever from any sort of music player:(

---

### Post by warhammerkid on 2008-05-07
Apparently there is something wrong with the kernel and ALSA not working in Hardy. I hope that within a week or two this issue should be fixed, as a lot of people are having problems. If you can't wait, I would suggest following the instructions here [http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/](http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/) . I haven't tried them though, so I don't know if they will work.

---

