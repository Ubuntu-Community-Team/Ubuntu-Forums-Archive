---
title: "Instalation issues"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by bloodhound on 2011-03-07
Hi i have some problems after a clean install of obuntu 10.10 livecd

I am mostly a mandriva user, but wanted to try ubuntu since everyone is talking about it, so i did.

The default install went ok, and the system looked nice, but ... when i have activated the nvidia "recommended" drivers all went to hell. 

Now when i boot i see an ugly "Linux" boot menu, when i shutdown instead of the nice Ubuntu shutdown logo , the text overwrites it, etc. 

Also the entire system feels slow: when opening a firefox browser, or when i am opening nautilus, etc


Am i doing something wrong? Do i have to do xxx aditional settings to get it to work ok?

My hardware: Phenone 1090T 6 cores
Vga: nvidia 9800GT
Ram: 8GB DDR3 Double Channel Corsair

With my hardware, ubuntu with gnome should fly, not work like my system was a pentium 3.

I used Ubuntu 64 bit version BTW.

---

### Post by Sean Moran on 2011-03-07
There are some major problems with Ubuntu and nVidia.  Sometimes, even if you repeat the same thing a second time, you get a different result.  That's major.

Rules I've learned with this GeForce8200M GPU are to:
1. NEVER try to install restricted drivers (eg. nvidia185) until after the installation is done.
2. Trust in Karmic Koala 9.10, and adhere to Rule #1.

3. To make sure you're on the right track, open a terminal and enter:
```

sudo dpkg -i dkms*
sudo dpkg -i patch*
sudo dpkg -i nvidia-185-kernel-source*
sudo dpkg -i nvidia-185-libvdpau*
sudo dpkg -i nvidia-glx-185*
sudo dpkg -i nvidia-settings*
sudo nvidia-xconfig

```I have those files already downloaded and ready to go which is why I can use the * at the end of each line if I am offline and want to expand my nVidia horizons.


PS: Yours might be different to mine, likely more advanced than I have.  For me, it is the 185 drivers that work.  Yours might be different packages.
If all else fails, revert to rules #1 and #2.

---

### Post by bloodhound on 2011-03-09
Thanks for the reply, i will give it a try and let you know.

---

