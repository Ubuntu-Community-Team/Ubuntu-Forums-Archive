---
title: "Dell Latitude D830, upgraded from Hardy, won't boot"
date: 2008-09-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by SnowPunk98 on 2008-09-18
I have a Dell Latitude D830 (Intel video, Intel 802.11n WiFi, Intel Core 2 Duo, bluetooth, SATA HDD) and upgraded from Hardy and after that it won't boot. It gets to the loading screen with the Ubuntu logo and the video is all messed up and hangs.

---

### Post by autocrosser on 2008-09-19
Try changing your menu.lst--replace "quiet splash" with "nosplash" (without the quotes) & you will be able to see where the boot fails---then give some info here. Sounds like another Usplash problem.

---

### Post by SnowPunk98 on 2008-09-19
I actually did a update from the recovery console and was able to boot, thanks though.

---

### Post by dro0g on 2008-09-20
I just upgraded from Hardy on a D630 - It was hanging with all kinds of flashing lines on the screen just after putting in the encryption key for the HDD. I do have the boot resolution set higher than the default, I suspect that was the cause. 

I booted into recovery mode and then did "continue as normal" and was able to get in. I don't think it updated anything since I haven't gotten networking working yet, but I rebooted again and it booted up normally.

---

