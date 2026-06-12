---
title: "Live CD Install - Freezes During Install"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by GoLoGo on 2006-08-03
Hello,

I have read many posts, different suggestions still no luck. What happens is an issue with my Nvidia 7800 GT pci express video card. When I start off the Live CD Desktop it has little distorted patches all around the screen, everytime I try and run the Installation, it freezes. I want to try and fix this problem, because a few months ago, when I installed the system through textmode it had the same problem. I installed the latest drivers, downloaded kernel sources- build-essentials ect... tried to configure my xorg.conf file but It would not boot, so I want to try and fix the problem. Thank you.

---

### Post by aysiu on 2006-08-04
Distorted patches sounds like a video problem, **but** freezing is not a video problem. It's very likely your disk was corrupted--either during the ISO download or during the burn process.

Have you done a checksum? Did you burn at a low speed?

[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html) gives you details on both of those.

---

### Post by tseliot on 2006-08-04
Please follow these instructions:

1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

---

### Post by GoLoGo on 2006-08-04
I am a proud owner of a fully working Ubuntu system. Thanks tseliot.

Second Question - Now that I have a fully working system, thats stable to work with - do I go on now in following a Nvidia driver installation HOWTO guide? or Do I have to do something special? to get OpenGL and all that fancy stuff with my card to work... Thank you, im so happy :D

---

