---
title: "How to install drivers for nVidia and Intel HD GPUs on Ubuntu 13.04"
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by nshkurkin on 2013-05-22
**I want to install the drivers onto my Ubuntu 13.04 for my nVidia Geforce 650m and/or Intel HD 4000 GPUs.** I installed my Ubuntu 13.04 onto my MacBook Pro Retina following these [instructions]("http://randomtutor.blogspot.com/2013/02/installing-ubuntu-1304-on-retina.html?m=1"), which means my Ubuntu boots through EFI and not Grub (as per what the tutorial suggested and showed). This also means I cannot boot into recovery mode...
 
With a clean install, everything works pretty much perfectly (aside from Suspend bugs) but both my nVidia and Intel GPUs do not show up as hardware devices that need "proprietary software" (the Wifi device shows up but nothing else). 

I already tried installing [Intel HD drivers for linux]("https://01.org/linuxgraphics/downloads") and the whole "apt-get" for nvidia drivers. Sadly, when I reboot after installing Intel HD drivers I get terminal for login and not the usual GUI (I did error checking and the screen was unable to begin drawing). I installed the nvidia driver but this time I just got a black screen after boot and not even a terminal. In both cases I had to do a complete reinstall.

**Is there a way to properly install either of these drivers without breaking my Ubuntu? **

I can completely understand that the drivers aren't necessary to get, but these drivers would be my ticket to accessing my GPUs' full capability (i.e. access to openGL 4.x programming).

---

### Post by dino99 on 2013-05-22
All the packages/drivers you'll need are baked inside the ubuntu archives and/or ppa(s); so follow the ubuntu howto (which are trusted) and avoid the other sources.

you need these drivers installed:
- xserver-xorg-video-intel
- xserver-xorg-video-nouveau
- nvidia-3xx-updates
        and "bumblebee" to use intel/nvidia together : ```
sudo add-apt-repository ppa:bumblebee/stable
```  [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

to deal easily with the archives for installing/updating/purging/... install synaptic: ```
sudo apt-get install synaptic
```  ```
sudo synaptic
```

---

### Post by nshkurkin on 2013-05-23
Thank you very much for your speedy response! But I couldn't get it to work. Here's the process I followed:

**1.** Clean install of Ubuntu 13.04

**2**. Updates install from Software Center

**3**. I go to the terminal and perform the following:

Log in as root
```

sudo su

```

I ran the following, but both were already installed:
```
apt-get install xserver-xorg-video-intel
apt-get install xserver-xorg-video-nouveau
```

Installing the nVidia driver:
```
apt-get install mesa-utils
apt-get instal jockey-kde

add-apt-repository ppa:xorg-edgers/ppa
add-apt-repository ppa:ubuntu-x-swat/x-updates

apt-get nvidia-current-updates nvidia-settings
nvidia-xconfig
```

Then I added bumblebee:
```
add-apt-repository ppa:bumblebee/stable
apt-get install bumblebee virtualgl
```

And final synaptic:
```
apt-get install synaptic
synaptic
```

**4. **In synaptic I refresh all the packages and update all that are recommended.

**5. **I reboot.

At this point I am greeted by "You are running in a low-graphics state." I said "go back to old configuration" but that broke my system. At another attempt, I tried going to the desktop in low-graphics mode but the screen simply went black and I had to reboot. If I try to restart lightdm in the terminal, it just gives me a black screen as well. I looked in the xorg error log and it said that the nVidia module could not load because it was not found.

I checked in the terminal to see if Ubuntu recommended any drivers (hopefully nVidia)
```
ubuntu-drivers devices | grep recommended
```
And that came up with nothing at all.

I do another complete reinstall and do everything minus installing the nVidia driver and everything works perfectly fine. I run **nvidia-settings** and it says that I am currently not using the nVidia GPU and that none are recognized. 

As it stands, without the nvidia driver Ubuntu works fine but cannot run OpenGL 4.x applications. I am basically doing this because I want to write OpenGL 4.x applications. Are there any more resources you can point me to or any suggestions to give?
 
(Side note: **jockey-kde **shows that I can get nVidia-319-updates and **nvidia-current-updates** gives back **nVidia-304-updates**. Should I get 304 or 319?)

---

### Post by mikesmithv on 2013-05-23
My system also contains the nVidia Geforce 650m and Intel HD 4000 GPUs but it is a Dell 17R SE (not Mac) and I had similar problems.  I am not that motivated to find a solution because the standard driver that is selectable with Ubuntu Desktop seems to be pretty good (good acceleration when needed and adaptive power management for acceptable battery operation).  It would be interesting to see how much longer battery life would be using just the Intel HD 4000 but after numerous re-installs I have given up.  I'm not sure about exactly what is going on under the hood but it appears the Intel HD 4000 is only accessible via an nVidia driver, the Intel driver just cannot "see" the chip I think.

As far as your question about which nvidia driver to use the standard Ubuntu Desktop 13.04 CD installed the nvidia open source diver by default but in System Settings --> Software & Updates under "Additional Drivers" I selected the "recommended" proprietary nvidia-310 driver and it seems to work the best.  Of the choices you mentioned the nvidia-304 seemed buggier so I would be inclined to go for the nvidia-319.  Too bad that's not an option under "Additional Drivers" in my system or I would try it.  The 319 version has some significant improvements according to [this]("http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE") article.

---

