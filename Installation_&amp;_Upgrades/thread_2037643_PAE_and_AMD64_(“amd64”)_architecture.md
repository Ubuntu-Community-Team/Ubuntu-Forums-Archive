---
title: "PAE and AMD64 (“amd64”) architecture"
date: 2012-08-05
forum: Installation &amp; Upgrades
---

### Post by hank22077 on 2012-08-05
I've got an old computer with AMD 64. No problems with the previous 10.04 LTS; however, installing 12.04 LTS gives me a blank screen with 'Input Not Supported' displayed for about 15 to 20 seconds before the system loads. It seems to work fine; but what's up?
Anyone else with this problem? I've provided 2 links below concerning the AMD 64 and PAE details. can't seem to find out what it's all about; and, am still pretty much a newbie to Ubuntu. So...?

[https://help.ubuntu.com/12.04/installation-guide/amd64/index.html](https://help.ubuntu.com/12.04/installation-guide/amd64/index.html) ;
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS)

---

### Post by Cheesemill on 2012-08-05
PAE and the amd64 versions of Ubuntu are mutually exclusive.

PAE is only used with the 32-bit kernel.

---

### Post by hank22077 on 2012-08-05
OK, thanks.
Somehow, I had accidentally downloaded the 32bit, lol.

Guess I was in a hurry to try 12.04 n didn't pay enough attention.

But, like I said above: "12.04 LTS gives me a blank screen with 'Input Not Supported' displayed  for about 15 to 20 seconds before the system loads. It seems to work  fine; but what's up?" Any insight would be appreciated.

---

### Post by oldfred on 2012-08-05
It seems more like a video issue. Do system then boot ok?

When they first moved the video drivers to the kernal my system would start to boot and then turn monitor off. Only because I was installing from USB, I could see USB still flickering so it was still installing. Once I learned to use nomodeset then it has worked to install until I get the nVidia driver installed.

What video card/chip do you have?

---

### Post by hank22077 on 2012-08-05
Yeah, it installed fine (from cd) and boots fine.
No problems while using the system.
Just the  screen issue while starting up

---

### Post by mastablasta on 2012-08-06
it doesn't matter if you have 32 bit. 32 bit can run on 64 bit, 64bit can run on 64 bit. but 64 bit can't run on 32 bit CPU.
 
it's a video driver issue.

---

### Post by hank22077 on 2012-08-13
yEAH, IT SEEMS TO BE THE VIDEO OUTPUT OF MY MONITOR...oops! Sorry, had caps on.
Anyway, I moved 10.04 above 12.04; and, the loading of 12.04 when selected no longer gives me the screen issue.

Thanks guys!

---

