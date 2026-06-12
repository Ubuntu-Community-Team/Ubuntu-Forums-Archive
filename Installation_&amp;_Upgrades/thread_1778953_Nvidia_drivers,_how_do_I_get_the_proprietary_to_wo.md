---
title: "Nvidia drivers, how do I get the proprietary to work?"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by LoloftheRings on 2011-06-09
Hello,

After using Arch Linux for a while, I tried Ubuntu 11.04 again. Most of  it was a pleasant surprise, except for the nvidia drivers. I currently have the nouveau drivers, but when I activate the nvidia drivers and reboot, it's installed but not in use. I figured I should run nvidia-xconfig (as suggested by nvidia-settings) but that makes my computer boot into a tty. Removing the /etc/X11/xorg.conf file makes it boot in nouveau again.

How do I install the Nvidia drivers? Ive tried the drivers from nvidia.com too, with the same results. I really want to be able to play my games, and nouveau just isnt going to cut it.

Thanks in advance.

---

### Post by Quackers on 2011-06-09
Are drivers found if you run Additional Drivers? Can you activate the (recommended) one from there?

---

### Post by nerdy_kid on 2011-06-09
dont use the drivers from nvidia.com, use the ones in the repos instead -- they are customized.  Ensure that nvidia-current is installed and run
```

sudo nvidia-xconfig

```
and reboot

---

### Post by LoloftheRings on 2011-06-10
Okay.. I installed it from the Additional Drivers dialog again, ran the sudo nvidia-xconfig, but I get the same results. Executing startx from tty1 gave me the following error:

(EE) No devices detected.

Fatal server error:
No screens detected

The Additional drivers dialog gives this state of the driver:
The driver is activated but currently not in use.

$ lsmod |grep nvidia
nvidia               9766978  0 

I'm a bit confused, am I currently using the Nvidia driver or nouveau? I don't seem to the the right framerate in my games, so I guess I'm still at nouveau, but I do have 3d.. I'm clueless :(

edit: My games do not run, I don't know how I managed to get them running past though.

edit2: Oh I'm using an ASUS K73SV-TY081V laptop, maybe it's a sandy bridge problem or something? I have no idea how this should work..

---

### Post by LoloftheRings on 2011-06-11
bump

I'm now considering going arch linux on this laptop too if nobody knows how to fix it :(

---

### Post by foresthill on 2011-06-11
Which Nvidia card / chip are you using? There are two different Nvidia drivers (one for the newer chips and a "legacy" driver) and sometimes it can be tricky figuring out which one you need.

---

### Post by LoloftheRings on 2011-06-11
I have a 540m.

---

### Post by foresthill on 2011-06-11
> **LoloftheRings said:**
> I have a 540m.


A quick Google search indicates that there is a problem with the current 11.04 kernel and your model of Nvidia chip. There is a newer kernel, however I doubt there is a compatible driver for it out yet. I Someone correct me if I'm wrong on this.

I would suggest either installing 10.10 or going with another distro for now.

---

### Post by LoloftheRings on 2011-06-11
Okay, thanks your time everyone.

---

### Post by Quackers on 2011-06-11
Ah, I see. I couldn't understand what was wrong.
It seems you have been unlucky with that particular graphics chip. Keep checking for updates. Nvidia seem to be very good for updating drivers, on the whole :-)

---

### Post by LoloftheRings on 2011-06-12
AHAAAAAAA (sorry, im quite happy)

[http://linux-hybrid-graphics.blogspot.com/2011/05/testers-needed-intelnvidia-bumblebee.html](http://linux-hybrid-graphics.blogspot.com/2011/05/testers-needed-intelnvidia-bumblebee.html)

For all those with sandy-bridge + nvidia card, go do that. It finally works, I have my nvidia card running as it should, at full speed! :D

Props to the devs out there <3

---

