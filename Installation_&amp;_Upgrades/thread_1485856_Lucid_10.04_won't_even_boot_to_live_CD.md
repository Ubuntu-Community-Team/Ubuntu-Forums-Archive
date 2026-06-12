---
title: "Lucid 10.04 won't even boot to live CD"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by Silvertones on 2010-05-17
This is crazy. I have 2 laptops a Dell & a Toshiba. Both have NVidia GeForce FX Go 5200 cards. I first did an upgrade on the Dell and that ended in a BSOD. I used the Alt CD for that. I just received the Live CD in the mail. I put it in the Dell and ended with a BSOD. I figured as much. What got me is that I couldn't get 9.1 to boot after that. It kept trying and would shut done. After the 4th time it booted. I hope it continues.
I thought I'd try it in the Toshiba and it went fine LIVE. I can't install it on that machine as it's my recording only lappy.
10.04 is pretty but can't tell much else.

---

### Post by kansasnoob on 2010-05-17
> **Silvertones said:**
> This is crazy. I have 2 laptops a Dell & a Toshiba. Both have NVidia GeForce FX Go 5200 cards. I first did an upgrade on the Dell and that ended in a BSOD. I used the Alt CD for that. I just received the Live CD in the mail. I put it in the Dell and ended with a BSOD. I figured as much. What got me is that I couldn't get 9.1 to boot after that. It kept trying and would shut done. After the 4th time it booted. I hope it continues.
I thought I'd try it in the Toshiba and it went fine LIVE. I can't install it on that machine as it's my recording only lappy.
10.04 is pretty but can't tell much else.

Start here:

[http://www.ubuntu.com/getubuntu/releasenotes/1004#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs](http://www.ubuntu.com/getubuntu/releasenotes/1004#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs)

**Boot options hidden by default on Desktop and Netbook CDs**

> The Ubuntu 10.04 LTS Desktop and Netbook CDs feature a new boot interface that is noninteractive by default. To configure advanced boot options, press any key at the first boot screen.   

Then you need to know about boot parameters:

[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

I would try F6 > nomodeset.

This may (or may not) be helpful:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539878](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539878)

---

### Post by Silvertones on 2010-05-17
Let me say this more simply.
I insert the live CD. It spins and a purpilish screen comes up with some little graphics thing at the bottom.
Then the screen goes black/blank. The CD is still loading whatever it is it loads. I presume when it stops it's at the screen were you choose to install or try but I can't tell because the screen is BLACK.

---

### Post by kansasnoob on 2010-05-17
> **Silvertones said:**
> Let me say this more simply.
I insert the live CD. It spins and a purpilish screen comes up with some little graphics thing at the bottom.
Then the screen goes black/blank. The CD is still loading whatever it is it loads. I presume when it stops it's at the screen were you choose to install or try but I can't tell because the screen is BLACK.

Have you tried pressing any key as soon as that first purple screen appears?

---

### Post by Silvertones on 2010-05-17
No I haven't but there are so many reported issues that i won't even considere 10.04 at this point. 9.1 installs and just works. Why change.

---

### Post by jon62 on 2010-05-18
I have just had this and pressing any key worked for me!!:guitar:

---

### Post by Silvertones on 2010-05-20
Pressing the spacebar got me to the screen where I choose the install options. I chose the option to try Ubuntu. The cd drive and HD were cranking away loading it but the screen went black again. If I could at least get the live CD to work I may be a little more confident in trying to reinstall.
For me with only dialup a reinstall is really a PIA.

---

### Post by Silvertones on 2010-05-22
I've been able to get the live CD to boot using the "nomodeset option. The problem now is that I can't get anything higher then 1024 X 768 monitor resolution. With 9.1 it's 1400 X 1050 which is good. I even tried the 9.1 Live CD and it goes to 1400 X 1050.
I also have a Belkin G+Mimo PCMCIA card. Does anyone no how to check if this is going to work in Lucid?
Thanks

---

### Post by dino99 on 2010-05-22
dont be shy, ask google  :P

---

### Post by Silvertones on 2010-05-22
I have but there is so much to wade through and with dialup it gets sort of frustrating

---

### Post by Silvertones on 2010-05-23
The answer I come up with is there is no fix. At least right now. My Toshiba will load the live CD without any intervention but it is also at a much lower resolution.

---

### Post by Silvertones on 2010-05-23
I'm confident that if I used the Alt CD again and did an upgrade and added  the "i915.modeset=0" to the boot line after "quiet splash" Lucid would be visable BUT I'm concerned that the resolution will still be low. Does anyone have a comment on this?
Thanks

---

