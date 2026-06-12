---
title: "Karmic Koala Instalation Problem"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by SVAndrei on 2009-12-23
Hello everyone. I am an absolute noob, but i tried to install Ubuntu 9.10 on my PC.

I am running an Intel P4 at 3 ghz, 2 GB RAM, NVIDIA Geforce 7600 graph card.

What happens is that i try to install Ubuntu, and just when the install screen should appear, my monitor displays an "Out Of Range" Message. Same thing happens with the LiveCD. I have an LG L1753S Monitor. With the Live CD feature, Ubunto does boot up, as i can hear the chime when the OS loads. I just can't see anything.

Any hints on what can i do?

Thanks.

---

### Post by mikewhatever on 2009-12-24
Try hitting f4 at the live cd menu (the menu where you select what to do with Ubuntu), and select Safe Graphics mode.

---

### Post by SVAndrei on 2009-12-24
Ok, i tried hitting F4, and did select the safe graphics mode, but it's the same effect. Could it be strictly monitor related, or is my graphics card too old?

---

### Post by bcn17 on 2009-12-24
I wouldn't think your graphics card is too old. Generally, with ubuntu graphic card problems stem from the card being to new. 

It might be worth a shot to do an alternate cd install. However, you might still get the same problem. 

I am guessing 3 things. 

1.(Hopefully) Something is different with the live cd than a full install that is causing you a problem, so trying the alternate cd should be a good get around. 

2. You need the restrcited drivers for your card, however to install the restricted drivers you need a GUI. There should be a way to install them via CLI, but I'm not sure how. 

3. Or, some component of your computer, not necessarily video card, is incompatible with ubuntu in some way and your gonna have a hell of a time figuring it out... heh heh. :D

Keep us updated!

---

### Post by mikewhatever on 2009-12-24
I've been reading bug reports that say higher end nvidia cards aren't detected as such by xserver.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/320671](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/320671)
A workaround is suggested in post #8, hope it helps.

Edit: If you use the text installer, as suggested by bnc17, I suspect the problem will remain after the installation. However, you'll be able to install the proprietary driver with <sudo apt-get install nvidia-glx-185>.

---

### Post by bcn17 on 2009-12-26
> **mikewhatever said:**
>  However, you'll be able to install the proprietary driver with <sudo apt-get install nvidia-glx-185>.

I would definitely try using the alternate cd and then follow mikewhatever's advice.

---

