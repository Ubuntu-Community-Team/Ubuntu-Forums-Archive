---
title: "Gutsy + Nvidia = Not possible?"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by misja on 2007-10-12
I was using Feisty without many problems, but because I needed a newer version of some packages I decided to upgrade to Gutsy today.
After installation and reboot, X did not start anymore. So I ended up on the command line.

The reason that X did not start, was that the NVidia driver that was specified in xorg.conf was not found.
I was using the Nvidia driver (installed it with Envy) because I am using a dual monitor setup that I could not configure properly otherwise in Feisty.

First I tried to replace 'nvidia' by 'nv' in xorg.conf as suggested in some posts. But although that made x start again, I ended up with both my screens showing garbage. Actually I get the same result when I start Gutsy from a live cd.
When I replaced nv by vesa I at least got a user interface again. But I wanted to have my dual monitor setup working again of course.

Unfortunately the Envy installer doesn't work yet under Gutsy so I downloaded and installed the newest NVidia driver for my video card (Geforce 7300) by myself.
But, after installation and reboot, x still does not start.

Does this mean that there is no way to use NVidia's own drivers for Gutsy? Btw I am using the 64bit version of Gutsy, don't know if that matters. And yes i downloaded the 64bit version of the NVidia drivers of course :)

---

### Post by Woody1987 on 2007-10-12
According to the envy website you need to uninstall the driver before you upgrade to any newer version. Have you tried 

```
dpkg-reconfigure xserver-xorg
```

---

### Post by bigken on 2007-10-12
personally I would run sudo dpkg-reconfigure xserver-xorg and select vesa 
for my driver the use restricted drivers manager in system/administration to install the nvidia drivers

---

### Post by dabl on 2007-10-12
> **bigken said:**
> personally I would run sudo dpkg-reconfigure xserver-xorg and select vesa 

I agree with that -- choose "NO" to autodetect on the first screen, and choose "VESA" in the second screen, and finish the script and restart X and you'll have a VESA GUI.

> 
 use restricted drivers manager in system/administration to install the nvidia drivers

Hmmmmmm ... the Gutsy Restricted Driver Manager was seriously buggy the last time I tried it.  I use the Envy script installer -- it "just works", although there is a minor tweak required to use it for Gutsy. Here's guidance:

[http://kubuntuforums.net/forums/index.php?topic=3086232.0](http://kubuntuforums.net/forums/index.php?topic=3086232.0)

Note that last sentence for the Gutsy tweak.  :)

---

### Post by misja on 2007-10-12
>  personally I would run sudo dpkg-reconfigure xserver-xorg and select vesa

Yes I tried dpkg-reconfigure. I have tried selecting both nvidia and nv as drivers but they both left me with either a crashing or a non-functional xserver. Vesa however gives me a proper gui. But with both monitors showing the same desktop.
I think my dual-monitor setup requires that I use the nvidia driver, so that I can set twinview settings in xorg.conf.

> use restricted drivers manager in system/administration to install the nvidia drivers

The restricted drivers manager does not start anymore after I upgraded to gutsy. It says it needs linux-restricted-module-2.6.22.14-generic. But when I try to apt-get install that module I get the message that this module is not found :(

---

### Post by misja on 2007-10-12
> I use the Envy script installer -- it "just works", although there is a minor tweak required to use it for 

I don't know why it works for you, but when I run the Envy installer it eventually quits because it says it does not recognize my 'operative system' :)

---

### Post by nowhere@cox.net on 2007-10-12
I had exactly the same problem only I had it with Feisty. Did exactly what was stated above.  On install, do not auto detect. Select the VESA driver. Then (I think from what you wrote you haven't gotten this far) Use the restricted package manager to install the restricted nvidia drivers. I believe you will need them to use the dual monitor features. 

For me x would crash using the nv drivers. I HAD to start with VESA and let the restricted package manager install the nvidia drivers. 

Hope this helps,
Eric

---

### Post by misja on 2007-10-12
I had everything working in Feisty. The restricted driver manager was working then as well, but I used envy to install the nvidia drivers.

As I said the restricted driver manager has stopped working after I upgraded to Gutsy. Envy doesn't work anymore either. I guess I just have to stick with Vesa and a single monitor until somebody decides to fix these problems..

---

### Post by puleen on 2007-10-19
I got Gutsy configured now with my nVidia card (it does it out of the box) but still no/poor support for dual monitor. I have an analog LCD connected to the same card (in addition to a digital LCD), yet it does not get detected nor can I add it in the "Screen and Graphics Preferences"

Anyone else able to set dual monitor up ?

---

### Post by sudoreboot on 2007-10-23
While trying to set up my nv or nvidia after my xorg got corrupted by gutsy upgrade I've encountered this thread as well as some related bug report. Removing all restricted/nvidia/glx packages and reinstalling nvidia-glx-new + restricted module with same number has kernel, finally allowed me to open X again with nvidia driver. nvidia-settings allowed me to use twinview for the first time. I quite like it - one screen functions as desktop and the other as TV. I wish that keyboard will only affect the part of the screen that is focused by mouse.

---

