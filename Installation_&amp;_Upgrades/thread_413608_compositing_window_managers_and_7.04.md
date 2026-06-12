---
title: "compositing window managers and 7.04"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by cjae on 2007-04-19
Hi,

I have quite a few questions, and since they will not be answered in other forums I will ask them here.

Sorry: I guess I should have said xubuntu.
1. I want to get  a fresh install ofxubuntu and cannot find the iso link (xfce) 

2. I would like to get some sort of compositing window manager whether it is beryl or compiz I do not know. I have read all the articles in wikipedia involving aiglx, beryl, compiz and xgl. I know that aiglx mix into or layer on xorg and that aiglx is incorporated into as of 7.x of xorg. And I understand that all of these groups may be collaberating in the near future. 

What I would like to know is that if I have a nvidia fx 5500 that has an old 15" crt and I use svideo out for a tv which I used for surfing and watching media. What combination would be the best for me. I have a intel 865 p4 mobo as well. I have read something about the new nvidia drivers not needing certain things as of the 9xxx series. Ok I would probably use a newer one, but I understood that in dapper and edgy the main nvidia driver was 8178 or something like 8xxx series is likely to be the same in 7.04? 

3. Would I be able to use beryl or whatever on both the monitor and the tv? And what is it that I must use twinview right?

4. Plus do I not benifit from a custom kernel and is the whole generic thing going to be carried on in 7.04? Cause I have a hyper-threading cpu that I believe does not get used when the kernel is of the generic type right? Even if I issue apt-get linux-686-smp it only downloads a small bit and makes the system monitor look like two cores? I know that hyper threading was not the greatest achivement but I just want to know if this is the case.

Thanks cjae

---

### Post by smartboyathome on 2007-04-19
ISO:
[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)

---

### Post by aeon on 2007-04-19
If I remember correctly the different kernel builds (smp, EMT64, x86_64 et.al) where dropped in the newer releases because the tweaks made to these kernels didn't matter all that much.. I'm running a pure 64 bit install and the generic kernel right now and I have yet to see a significant loss in performance or otherwise, but ofcourse YMMV.. Not quite shure how the vanilla kernel handles the hyperthreading though..

as for the feisty release of xubuntu you can find it here: [http://cdimage.ubuntu.com/xubuntu/releases/feisty/release/]("http://cdimage.ubuntu.com/xubuntu/releases/feisty/release/")

assuming you do a clean install the only thing you need to do is use the restricted modules plugin that comes with feisty to install the nvidia drivers and then open up a terminal and:
```
sudo apt-get install beryl beryl-manager emerald emerald-themes
```

and restart the xserver. You should now be able to start beryl and have the nvidia driver properly configured..

Hopefully this helps!

:wink:

---

### Post by cjae on 2007-04-20
Will it work on my TV as well?

---

### Post by jfinkels on 2007-04-20
> **cjae said:**
> Will it work on my TV as well?

The video monitor you use should have no effect on how your system or programs run, whether it be a CRT monitor, an LCD monitor, or a "TV" monitor. It should display your video output just fine if it displays your desktop at all.

---

