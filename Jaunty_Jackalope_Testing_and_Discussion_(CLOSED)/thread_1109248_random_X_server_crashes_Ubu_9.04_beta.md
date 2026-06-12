---
title: "random X server crashes Ubu 9.04 beta"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Predrag on 2009-03-28
Hi I have problem with Ubuntu 9.04 beta. Sometimes when I open some program or im surfing on internet my ubuntu randomly crash.Crash = my X server restart to Log screen.This restarting of X server i have noted in Ubuntu 9.04 alpha 6.I can send you some log but i dont know which one.I have fujitsu siemens amilo 1510,Ati x 1100; 1,5Gb Ram;

---

### Post by Nibblyn on 2009-03-28
Similar issue here. I belive it is because of the ati card. Try forcing AGP mode "1". 

...in xorg.conf:

Section "Device"
    ...
    Option "AGPMode" "1"
EndSection


Please report back if you solve it. Thanks.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

[https://answers.launchpad.net/ubuntu/+question/63408](https://answers.launchpad.net/ubuntu/+question/63408)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/139210](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/139210)

---

### Post by binbash on 2009-03-28
wrong forum.This should go to Jaunty Development forum

---

### Post by Predrag on 2009-03-29
I didnt solve this problem but I have a Xorg.0.Log in attachment.Maybe this problem is beacuse amd/ati didnt realease officialy driver for 9.04.

---

