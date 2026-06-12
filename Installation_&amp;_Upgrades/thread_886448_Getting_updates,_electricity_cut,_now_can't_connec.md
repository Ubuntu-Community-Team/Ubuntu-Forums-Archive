---
title: "Getting updates, electricity cut, now can't connect to the net"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by rapattack1 on 2008-08-11
Hi I was on my notebook, with the latest Ubuntu that I installed a month ago, at a wifi hotspot and I accidentally pulled the cord out while getting updates. Actually it was installing them. Now I can't connect to the net at all. I use wlassistant and it says that there is no wireless(pcmcia) device or something like that. When I go into 'hardware testing' it lists the wifi device there. I came home and then tried used the eth0 device(pcmcia) but again I got the same problem. Is there something I can do about this offline?

---

### Post by Elfy on 2008-08-11
Have you let it finish installing the updates? Maybe 

```
sudo dpkg --configure -a
```

see if the problem is still apparent once the updates have been able to finish.

---

### Post by rapattack1 on 2008-08-11
Ahhhh yes I did that because I thought to myself ok I will go into synaptic and it told me to do that command. So the system finished installing whatever after i did it but now the network setting have gone stupid. There are two wired connections listed now. At first I went into the 'network' thing and I just click onto the one that was ticked and the numbers were wrong and I saved it but I dunno how it got so screwed up. One light is showing on the pcmcia dongle but it is a straight green light . The other light is not flickering like it should and in 'network' the icon shows that the cable is not inserted into the port. If you know what I mean. How do I reset this?

---

### Post by timcredible on 2008-08-11
i'd reinstall from scratch, if apt was actually installing updates and you turned off the pc, hard telling what files got messed up.

---

### Post by rapattack1 on 2008-08-11
Yes I was thinking that last night too. OK will do that. Thanks!!!

---

