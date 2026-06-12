---
title: "Cannot Boot after installing 11.04"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by forpulse on 2011-04-29
Hello guys

I just installed ubuntu 11.04 on a separate partition on my hard drive so i can have dual boot for window 7 and ubuntu. I have done this in the past with 10.10 and it use to work fine. But now after installing 11.04 I am not able to boot it. I have recorded a video of what happens. here is the link. [http://www.youtube.com/watch?v=oLr2LqS0cEQ](http://www.youtube.com/watch?v=oLr2LqS0cEQ)

I have written my laptop spec in the description of the video. Please someone help me out. Thanks in advance.

---

### Post by cariboo on 2011-04-30
Select recovery mode from the grub menu, then select failsafeX from the menu to get to the desktop. Once at the desktop, make sure the i915 driver is loaded. To check open a terminal and type:

```
lsmod | grep i915
```

---

### Post by Rubi1200 on 2011-04-30
Is this a Wubi install? The boot screen suggests this is a Wubi install or are you using a boot manager?

For options at boot time, see here:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by forpulse on 2011-04-30
yes this is a wubi install... i had window 7 and i installed using wubi. I have dual boot now. I got rid off the i915 problem.. but im still not able to boot. I get that very last error page you see in the videos.

---

### Post by MAFoElffen on 2011-04-30
||Confused||  Just a question... Okay, but Part 2 of your video on YouTube shows you running in a Natty graphical api okay ready to browse the web in Firefox 4?  Am I lost somewhere with that?

---

### Post by forpulse on 2011-04-30
lol what? really.. my account only has one video uploaded. I am not sure which video you are referring to.  I think you are mistaken. I only have one video uploaded.

---

