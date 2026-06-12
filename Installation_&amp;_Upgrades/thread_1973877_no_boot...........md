---
title: "no boot.........."
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by Carl G on 2012-05-05
Hi, I'm a newbie here so please be gentle.......My other half was loading ubuntu  and it stopped on the keyboard selection page. It sat there for about 15 minutes or so with the wheel revolving and doing nothing else. So, the machine went to sleep (or crashed....). Now it won't do anything whatsoever. On trying to restart it shows nothing but a black screen the lights on the front of the machine are on but no one is at home. 
Machine is a HPCompaq DX2200,Pentium4 ht, ATI Radeon x300 or x1300 graphics.,160Gb HDD(plenty of space not sure of ram think 1Gb. Install was alongside of windowsXP pro.
Any help would be gratefully recieved. Complete novice with Ubuntu so as simple as possible please.  :-)

---

### Post by darkod on 2012-05-05
Can you boot with the ubuntu cd into live mode (Try Ubuntu)? Does it work correctly?

If it does work, open terminal and post the result of:
sudo fdisk -l (small L)

---

### Post by Carl G on 2012-05-05
Thanks for the reply.
No getting nothing, powers on then just sits there then screen displays no signal message.
Cant seem to access anything. No response from trying to get into BIOS it doesn't seem to respond to keyboard inputs......

---

### Post by darkod on 2012-05-05
If you can't get into BIOS or you can't boot with a cd, it seems not related to ubuntu. It might be a hardware problem.

You should always be able to boot with a cd, even if the hdd is completely dead or missing.

---

### Post by Carl G on 2012-05-05
Hi. Never been a problem ,it's as though it's still 'asleep' and not responding to input.

---

### Post by Carl G on 2012-05-05
OK now pulled the power supply and it's booted up on xp and running a disk check....
So, maybe all's well that ends well. Now, should she try loading Ubuntu again.....:-)

---

### Post by dino99 on 2012-05-05
you might need to boot by adding an option, try first with noacpi or nomodeset

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

