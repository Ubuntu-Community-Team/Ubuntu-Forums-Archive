---
title: "Losing support for GeForce GTX 275"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by fletschge on 2010-08-10
Hi guys,

I'm experiencing problems with Ubuntu Lucid Lynx x64 Desktop Edition and my nVidia GT200b [GeForce GTX 275].
First of all, when Lucid Lync came out, everything worked perfectly out of the box. I even had all the shiny desktop effects with Compiz. Then, let's say around mid-june, after installing the latest updates Compiz didn't work anymore. So I had to use no visual effects anymore. OK not the end of the world I assumed. But since Kernel 2.6.32-24 came with the updates, I couldn't even get X running again. Everytime my machine boots up, I get a X error message that no matching screen could be found. I checked the xorg.conf, even ran 'nvidia-xconfig', removed xorg.conf and tried it again, etc. etc. I can't get it to run with the latest updates. So I chose to stick with 2.6.32-22, where I at least have a running X server.

Oh btw., yes I am using the recommended hardware acceleration driver from System->Administration->Hardware drivers (which is btw. the only selectable one, there is no other one). It says "version current".

Why is support for the GeForce GTX 275 dropping? Or what am I doing wrong?

My enabled updates: lucid-security, lucid-updates, lucid-proposed. I do not have backports enabled.

Thank you for any help.

- fletschge

---

### Post by dabl on 2010-08-10
Here's your guidance: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by fletschge on 2010-08-10
Hi dabl,

Thank you for the quick answer. After running
```

sudo apt-get --purge remove xserver-xorg-video-nouveau
sudo apt-get install nvidia-current
sudo update-alternatives --config gl_conf
sudo ldconfig
sudo nvidia-xconfig
```

nothing seemed to work, even not with 2.6.32-22. So I went back into low-graphics mode and installed the hardware driver under System->Administration->Hardware drivers.
Funny how, after rebooting, it worked perfectly even under 2.6.32-24 with compiz and all the effects. Don't know what it did, but it solved the problem :D

Thank you again.

- fletschge

---

