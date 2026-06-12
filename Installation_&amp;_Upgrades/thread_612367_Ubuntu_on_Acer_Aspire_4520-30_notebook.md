---
title: "Ubuntu on Acer Aspire 4520-30 notebook"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by Irihapeti on 2007-11-13
My son has one of these notebooks with Vista Home Premium on it. Vista is not working properly. So he is open to the idea of looking at Ubuntu and has a Feisty LiveCD that I gave him. Now that University has finished for the year, he might even find time to do something with it :)

I found this thread:
[http://ubuntuforums.org/showthread.php?t=606764&highlight=4520-30&](http://ubuntuforums.org/showthread.php?t=606764&highlight=4520-30&)

But it relates to a slightly different model with a different graphics card/mode. The -30 model has nVidia nForce 630M UMA, not GeForce 7000M.

SO... Has anyone got any experience with this graphics setup? What advice can you offer?

Thanks
Irihapeti

---

### Post by '888' on 2007-11-20
Just try to use Ubuntu 7.10 Gutsy Gibbon
I have my acer 4520 works all with this one
but for wireless, sound and graphic card 
you should download the driver
i have broadcom card for wireless so there no big deal about this one
if you have atheros you should download ndiswrapper 
to wrap your windows driver to be used at linux environment
for the sound card just download linux-backports-modules
and add this line
options snd-hda-intel model=acer
at /etc/modprobe.d/alsa-base file

---

### Post by Irihapeti on 2007-11-20
Thanks for your reply

Is your graphics card nForce or GeForce?

---

### Post by AJB2K3 on 2007-11-20
Most acers work with 7.10

---

### Post by '888' on 2007-12-02
nvidia geforce 7000M

---

### Post by Irihapeti on 2007-12-03
> **'888' said:**
> nvidia geforce 7000M

So has anyone got it working with nVidia **nForce** graphics?

Maybe we just try it and find out. :) Anyway, it looks promising.

---

### Post by grokwik on 2007-12-26
Maybe someone could help, I just bought a aspire 7220. On the specs (pdf downloaded on their website) they tell it has a geForce 7000M but they also tell the chipset is a nForce 630M...
Reading this post, it seems geForce 7000M and nForce 630M are two different models. :confused:

---

### Post by Irihapeti on 2007-12-26
Sorry I can't help you much. Yes, I think that GeForce and nForce are different graphics modes. But as the laptop in the original post belongs to my son, and he's in another town and he's not been in a hurry to try the liveCD, I can't yet tell you how the nForce graphics works.

Maybe I should email him and ask him to try it now because by doing so he'd be helping someone else. I think that might get his attention :)

---

### Post by grokwik on 2007-12-26
=D>Nice education... big up Mr :)

---

### Post by eabhi on 2007-12-28
Hey even I have Acer Aspire 4520 (GeForce 7000M and Atheros).

Here is what I have done

1. Got graphics card detection problem while trying to start Ubuntu 7.10 in Live CD. So started in "Safe Graphics mode" (runs in 800x600 resolution) and finished installing in the same mode.
2. Sound, WiFi and Display were not OK.
Installed Restricted Drivers for nVidia (nvidia-glx-new). You would need to enable all the four repositories in "Adminisration -> Software Sources". Then Manually search for the Acer monitor and set the resolution to 1280x800. Enable all the the 3D Effects
3. Follow the below mentioned post for getting sound enabled. Work absolutely fine.
4. Bluetooth Works Out of the Box
5. Need to try WiFi soon to get everything working. Will update here if I am able to do that uccessfully or will ask more doubts

I have following issues now

1. The Resolution keeps on getting resetted to 800x600 whenever I reboot the lappy and need to manually go and change it to 1280x800
2. The eth connection number keeps on incrementing like eth1, eth2, eth3,... everytime I reboot the lappy.

Second one is OK, but does anyone has a fix for the 1st problem.

Cheers
eabhi

---Edit: I have got the Solution for the Resolution problem... here it is

   1. Make sure the restricted driver is installed (in Synaptic search for nvidia-glx-new)
   2. Execute this command in a terminal:
      sudo dpkg-reconfigure -phigh xserver-xorg
   3. Open Restricted Drivers Manager and enable the nVidia driver.
   4. Reboot, and you should be good to go.

Hope this helps..


> **'888' said:**
> Just try to use Ubuntu 7.10 Gutsy Gibbon
I have my acer 4520 works all with this one
but for wireless, sound and graphic card 
you should download the driver
i have broadcom card for wireless so there no big deal about this one
if you have atheros you should download ndiswrapper 
to wrap your windows driver to be used at linux environment
for the sound card just download linux-backports-modules
and add this line
options snd-hda-intel model=acer
at /etc/modprobe.d/alsa-base file

---

### Post by grokwik on 2007-12-31
Thanks a lot. I have an acer aspire 7220 with the same hardware (geforce 7000M) and you technique works as a charm :)
At last I have my good ol' 1440*900 :D

---

### Post by soulmoksha on 2008-01-03
Hi 
I am very new to linux. I have bought a Acer aspire 4520 machine in which i have been trying to load both fedora and ubuntu. While fedora loads quite easily, once restarted it does not boot. ubuntu needs to be loaded in the safe graphics mode but once it is uploaded it does not boot once it restarts. Finally I loaded Kubuntu 7.04 which booted after restart. However, the graphics and the wifi was down. Then i switched it off as i had work on the internet (my office only works on wifi, used XP which is also loaded on my machine.) Again when tried to boot back with Kubuntu, it hung giving me an error message.

Busy box V.1.1.3 (Debian 1:1.1.3-3Ubuntu 3) built in shell (Ash)
Enter help for a list of built in commands.
/Bin/sh: cant access tty; job control turned off
(intirafms) 

This is the first tryst with linux and am quite confused how to deal with the situation. I desperately want to shift out of windows based OS but have been unsuccessful.

My laptop specs are: 
Acer Aspire 4520
AMD 64, 1.8 ghz
1.5 GB RAM
160 GB hard disk
NVIDIA GeForce 7000m

Thanks in advance

:(

---

### Post by grokwik on 2008-01-03
[bad placement of my original post]

---

### Post by grokwik on 2008-01-03
you can find how to make it work quite easyly over the forums, this post included.

For the video card :
> **eabhi said:**
> 
1. Make sure the restricted driver is installed (in Synaptic search for nvidia-glx-new)
   2. Execute this command in a terminal:
      sudo dpkg-reconfigure -phigh xserver-xorg
   3. Open Restricted Drivers Manager and enable the nVidia driver.
   4. Reboot, and you should be good to go.



For the wifi :```

mkdir /tmp/wifi
cd /tmp/wifi
wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz
tar -xvzf madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007
make
sudo make install

```For the soundcard :[LIST=1]
[*]Download/install "linux-backports-modules"
[*]Add this line to /etc/modprobe.d/alsa-base : ```
options snd-hda-intel model=acer
```[/LIST]I have a aspire 7220 and this technique worked well... Hope this'll work for you too.

---

