---
title: "Live CD won't start... the caps and scroll lock lights are flashing"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by gwu777 on 2008-04-27
Hi I try to upgrade as most people here yesterday, but it sayd the instalation failed...

I have decided to start a new instalation with HH. When I start with the live CD, it doesn't load. It has loaded once yesterday without any problems, but today it hangs after a while, I can still see the ubuntu bar but it is stuck, plus the caps and scroll lock lights are flashing, it has been like that for the last 20 min, I don't think it is going anywhere!!!

---

### Post by ssam on 2008-04-27
flashing capslock means that the kernel has panicked (ie crahsed bad). can you choose check disk from the boot menu of the live cd.

---

### Post by NightwishFan on 2008-04-27
1)Reboot with ctrl+alt+delete.
2)When the menu loads move over the install ubuntu option you want.
3)Press f6 and delete the lines quiet and splash.
4)Press enter and see if it boots or what it gets stuck on.

---

### Post by gwu777 on 2008-04-27
There were reading errors on the CD, I have tried to reburn it several time, but still the driver has difficulty to read it, I don't understand why, the MD5sum is ok though...

I have formatted everything, installed 7.10 again, and I am now doing a clean upgrade, it is not very pretty, but it seems to work so far!!!

Thank you for your help

---

### Post by MongooseCage on 2008-05-02
WOW, samething happened to me but instead I had already installed it... that is scary... So supposedly I can use a good live cd to extract all my data out right?

---

### Post by NightwishFan on 2008-05-02
It likely has something to do with the burn, optimally use cd-r memorex is good, and burn with something reliable like k3b or brasero at slowest possible speed and check for errors if there are none and the problem persists install with the alternate install cd (i always use alternate anyway its just as easy) And yes you can copy files from a live cd if you mount your other drives.

---

