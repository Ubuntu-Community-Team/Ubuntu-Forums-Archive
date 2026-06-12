---
title: "Problem installin Graphics Driver"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by VanDerGraff on 2011-03-30
I just put ubuntu 10.04 on my dell dimension 2400 and it has been very laggy since. I think it has somthing to do with the graphics driver not being installed properly. I had upgraded the gpu awhile ago to a radeon 2200 pro and i think when i installed ubunut either the driver didnt install or it is the wrong one. Can anyone help?

thank you

---

### Post by jcolyn on 2011-03-30
Your system ram may not be enough ..

---

### Post by tommcd on 2011-03-31
> **VanDerGraff said:**
> I had upgraded the gpu awhile ago to a radeon 2200 pro and i think when i installed ubunut either the driver didnt install or it is the wrong one.
If you go to: system > administration > additional drivers, it should offer to install the proprietary ati driver. Then reboot the computer.

And welcome to the Ubuntu forums!

---

### Post by VanDerGraff on 2011-03-31
> **jcolyn said:**
> Your system ram may not be enough ..

I have the maximum amount of ram my motherboard can hold.. Which happens to be a whopping 1g which i would think should be enough.

---

### Post by VanDerGraff on 2011-03-31
> **tommcd said:**
> If you go to: system > administration > additional drivers, it should offer to install the proprietary ati driver. Then reboot the computer.

And welcome to the Ubuntu forums!

Thanks okay when i go to administration there is no tab for additional drivers. Do you mean go to hardware drivers? Because when i do that it just tells me that no propritary drivers are in use on the system.

---

### Post by tommcd on 2011-03-31
> **VanDerGraff said:**
> Thanks okay when i go to administration there is no tab for additional drivers. Do you mean go to hardware drivers? Because when i do that it just tells me that no propritary drivers are in use on the system.
Yes, hardware drivers is correct. I thing with Ubuntu 10.10 they changed it to "additional drivers".
Are there any hardware drivers listed there for you to install? If, not then there may not be any driver available for your card. ATI dropped linux support for a lot of older ati cards.
I have no experience with ati unfortunately. I always use nvidia, since there is still much better linux support for nvidia cards.
See this tutorial for more info on ati cards: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Is your user name "VanDerGraff" a reference to the progressive rock group VanDerGraff Generator by any chance??

---

### Post by VanDerGraff on 2011-03-31
> **tommcd said:**
> Is your user name "VanDerGraff" a reference to the progressive rock group VanDerGraff Generator by any chance??

actually yeah. Good catch. they are one of my favorite bands of all time.

---

### Post by jcolyn on 2011-03-31
Check out this review of your model.. [http://www.pcworld.com/article/115403/dell_dimension_2400.html](http://www.pcworld.com/article/115403/dell_dimension_2400.html)

"It was no surprise that this Dimension did not pass muster in our  high-end graphics tests. It's wishful thinking to expect a powerful  graphics card in a $700 PC, and the integrated Intel Extreme (845GV)  chip set borrows from the system's main memory, inhibiting graphics  performance. In our 3D gaming tests, frame rates reached around 30  frames per second only at the lowest tested resolution of 1024 by 768  pixels and 16-bit color, and dipped to less than 5 fps at a resolution  of 1600 by 1200 and 32-bit color. The result was bland-looking colors  and jerky action during game play. And without an AGP slot, there's no  practical graphics upgrade."

This is what I would suggest. Upgrade your Intel video driver by opening a terminal and entering ```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```Next

```
sudo apt-get update
```Then

Open update manager and install the updates. Next open synaptic and enter intel then look for xserver-xorg-video-intel and check it for upgrade then apply..

If you also want to upgrade the kernel then instead of the synaptic method after ```
sudo apt-get update
```as above enter in the terminal ```
sudo apt-get dist-upgrade
```

---

### Post by tommcd on 2011-03-31
VanDerGraff said his video card was radeon 2200.

VanDerGraff,
In order to find out exactly what graphics card you have, open a terminal and post the output of: ```
lspci | grep -i vga
```
This will show us exactly what graphics card you have.
Also post the output of:
```
glxinfo | grep -i render
```
The glxinfo will tell us if direct rendering is enabled for your video card.

BTW, I am a huge VanDerGraff Generator fan also!!:)

---

### Post by VanDerGraff on 2011-04-02
> **tommcd said:**
> VanDerGraff said his video card was radeon 2200.

VanDerGraff,
In order to find out exactly what graphics card you have, open a terminal and post the output of: ```
lspci | grep -i vga
```This will show us exactly what graphics card you have.
Also post the output of:
```
glxinfo | grep -i render
```The glxinfo will tell us if direct rendering is enabled for your video card.

BTW, I am a huge VanDerGraff Generator fan also!!:)

I do have a radeon 2200 pro and when i typed in the glxinfo into the terminal it said:

direct rendering: Yes
OpenGL renderer string: Mesa DRI (RV280 5960) 20090101 x86/MMX/SSE2 TCL DRI 2


what do i do from here? and im glad to hear your a fan of them i feel like hardly anybody knows of them.:guitar:

---

