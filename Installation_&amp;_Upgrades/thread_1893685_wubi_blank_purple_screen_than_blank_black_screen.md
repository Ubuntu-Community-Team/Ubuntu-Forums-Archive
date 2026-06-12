---
title: "wubi blank purple screen than blank black screen"
date: 2011-12-10
forum: Installation &amp; Upgrades
---

### Post by improvent363 on 2011-12-10
I installed wubi in win7 ultimate 64 but all I get is blank purple screen than a blank black screen and the blank screen just stucks their. That does not happen with win7 OS. 

I am trying wubi because I couldn't also install from CD [ver. 10.4] and usb 2.0 flash drive  [*using Universal USB Installer from pendriverlinux.com on a 4GB kingston ].*
Please tell me how to fix this. If you need more info please don't hesitate to let me know!

I attached my system information if anyone need it to fix the problem please.

---

### Post by bcbc on 2011-12-10
With nvidia cards you generally have to use the 'nomodeset' kernel boot option at startup. This thread explains how: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Post #1 discusses the live CD override and overrides on an installed system.

Post #8 discusses overrides on the first boot after installing with Wubi. (Note in some cases you will need to override again using the technique in post #1 as discussed in post #8).

After booting, go to software-drivers and install the nvidia drivers. Check out this thread first: [http://ubuntuforums.org/showthread.php?t=1814360](http://ubuntuforums.org/showthread.php?t=1814360) as I'm not sure whether the driver in the repos is appropriate or not. The threads quite old so maybe the repos is best (or someone who has some experience with this can chime in)

---

### Post by improvent363 on 2011-12-11
> **bcbc said:**
> With nvidia cards you generally have to use the 'nomodeset' kernel boot option at startup. This thread explains how: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Post #8 discusses overrides on the first boot after installing with Wubi. (Note in some cases you will need to override again using the technique in post #1 as discussed in post #8).


Okay. I did the method #2 on Post #8 and exactly copy the code below but I get the same scenerio:

> loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
search --set=diskroot -f -n /ubuntu/disks/root.disk
probe --set=diskuuid -u $diskroot
linux /vmlinuz root=UUID=$diskuuid loop=/ubuntu/disks/root.disk  preseed/file=/ubuntu/install/preseed.cfg wubi-diskimage ro quiet splash [COLOR=Red]nomodeset[/COLOR]
initrd /initrd.img
boot                      So, did I do it right?

---

### Post by bcbc on 2011-12-11
Yes that looks right. You could remove the 'quiet splash' and see if there is some better diagnostics displayed if and when it halts.

But, there's also a chance that the wubi first install has completed enough to generate the grub.cfg (and this means it won't care about the wubildr-disk.cfg file anymore.) 
So... after selecting Ubuntu, hold the SHIFT key and if a grub menu appears, then follow the instructions in post #1 to edit the first entry there instead.

(All this stuff wouldn't seem quite so bizarre if all graphics cards worked out of the box)

---

### Post by improvent363 on 2011-12-13
> **bcbc said:**
> Yes that looks right. You could remove the 'quiet splash' and see if there is some better diagnostics displayed if and when it halts.

But, there's also a chance that the wubi first install has completed enough to generate the grub.cfg (and this means it won't care about the wubildr-disk.cfg file anymore.) 
So... after selecting Ubuntu, hold the SHIFT key and if a grub menu appears, then follow the instructions in post #1 to edit the first entry there instead.

(All this stuff wouldn't seem quite so bizarre if all graphics cards worked out of the box)

1. I deleted quiet splash and all I get is purple screen. I went to grub menu and typed what was stated in post #1 and I just get the same blank screen results. 

2. So, I am thinking of installing an old verion of ubuntu via wubi or usb installation as all I needed to use ubuntu is go to some websites and surf for an hour. So, I don't care about any additional programs or good resolution. So, do you know which old version of ubuntu [or some other linux] that  does not do this:
> The newest kernels have moved the video mode setting into the kernel.   So all the programming of the hardware specific clock rates and  registers on the video card happen in the kernel rather than in the X  driver when the X server starts.. This makes it possible to have high  resolution nice looking splash (boot) screens and flicker free  transitions from boot splash to login screen. Unfortunately, on some  cards this doesnt work properly and you end up with a **black screen**. [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)


---

### Post by bcbc on 2011-12-14
I'm pretty sure that all current versions of Ubuntu have issues with nvidia out of the box. Usually it's as simple as supplying nomodeset to get started and then installing the drivers. I'm not sure why this isn't working for you, unless you're not editing the menu that's actually booting (although it sounds like you are) 

I don't think you'll have better luck on an older release of Ubuntu... I've heard that Mint is a little easier because it's basically Ubuntu with more non-free software by default (?) but have never used this myself.

---

### Post by improvent363 on 2011-12-21
> **bcbc said:**
> I'm pretty sure that all current versions of Ubuntu have issues with nvidia out of the box. Usually it's as simple as supplying nomodeset to get started and then installing the drivers. I'm not sure why this isn't working for you, unless you're not editing the menu that's actually booting (although it sounds like you are) 

I don't think you'll have better luck on an older release of Ubuntu... I've heard that Mint is a little easier because it's basically Ubuntu with more non-free software by default (?) but have never used this myself.

Never mind I got it to work. I was putting the nomodeset at the end of boot grub screeen and not after "splash".

---

