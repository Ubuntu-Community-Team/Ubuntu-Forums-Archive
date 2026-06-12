---
title: "Monitor resolution problem"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by ivanrkv on 2011-01-01
I have this great monitor, with weird hardware. The model is ViewSonic VX2835wm. It's 28" with 1920x1200 res and 60Hz refresh rate. It works fine in windows, but only after I install the drivers (comes in .inf file), otherwise proper resolution is not detected. In windows as high as it goes is 1600x1200. After I installed Ubuntu, I expected problems with hat too, and wasn't disappointed. I tried installing drivers, using Gnome and KDE, nothing worked. Then today I installed Kubuntu, just for the hell of it. then i stumbled on this [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)   and did the whole xrandr config. It worked. then i remembered i have not enabled nvidia drivers, and went and enabled them. i restart, and the monitor is back to the ugly 1024x768. I don't know what to do at this point. i tried editing xorg.conf but that resulted in x server breaking. Any advice?

---

### Post by chrism66 on 2011-01-02
Same problem here. Tried the xandr fix and will not work fro me.

---

### Post by dino99 on 2011-01-02
remove xorg.conf as actual kernel directly deal with X:

sudo rm /etc/X11/xorg.conf

then add this ppa to synaptic repo tab:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

then update, upgrade and reboot

then check driver activation

---

### Post by theasprint on 2011-01-02
Hi,

How about manually installing your nvidia driver?

I would suggest you manually install your nvidia driver obtained from the Nvidia website.

** This step only applies to NON-OPTIMUS Nvidia graphics cards. If you are using an Optimus driver I'll help you later.

1. Go and detect your graphics card. If you know your graphics card  model then you can skip this step. Or else, you can go terminal and enter
```
lspci | grep VGA
```

2. Then go Nvidia.com and download the driver for your graphics card model. Remember to download the Linux version.

3. The Nvidia driver requires gdm to be turned off. Therefore to turn it off, do this:
```
sudo service gdm stop
```

4. Then install your Nvidia driver by doing:
```
sudo bash <your Nvidia driver's directory>
```

5. Then turn on your gdm again:
```
sudo service gdm start
```

* Upon installing the Nvidia drivers, there will be an Nvidia X Server installed with it too. It is similar to the Nvidia Control Panel in Windows. Then you can adjust your resolution and the rest.

** If you still face problems, then go to the thread in my signature below and follow the instructions of TheRawGod. That thread tells you how to even turn off the Nouveau driver. (which is the replacement of the Nvidia drivers for Ubuntu)

Good Luck :D

---

### Post by ivanrkv on 2011-01-02
@theasprint, I don't think that graphics card is the problem, since it works perfectly fin on my LG 19" screen

@dino99 you method did not work

---

### Post by BicyclerBoy on 2011-01-02
What are the startup error messages in the x server xorg log files ?

Does this monitor not report its EDID correctly ?
Do you connect via HDMI or DVI VGA or component or ?

It is easy enough to set a video mode in xorg & disable EDID mode validation.

What is your graphics card ?

run glxgears

nvidia-settings is the equivalent to nv-control panel.
The glx driver is the nvidia X server.

---

