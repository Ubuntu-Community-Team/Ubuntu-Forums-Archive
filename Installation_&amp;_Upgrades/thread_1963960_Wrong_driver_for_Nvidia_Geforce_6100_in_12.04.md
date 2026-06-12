---
title: "Wrong driver for Nvidia Geforce 6100 in 12.04"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by jarokopitar on 2012-04-23
Here goes:
I upgraded my Kubuntu 11.04 to 12.04. Most stuff works, but the graphics was really, really slow. A snail in molasses slow. Even though in 11.04 everything worked (TM).
So I went to desktop effects and turned off OpenGL. OK, graphics is now usable.
I checked which driver I have installed; sure enough, it is nvidia-current, supporting GeForce series 6 and newer. GeForce 6100 is series 4, according to lspci.
So I went to search for the driver that does support GeForce series 4. And lo and behold, I found it: nvidia-96 claims to support it. But alas! I cannot install it. Aptitude tells me the driver depends on xorg-video-abi-10 [UNAVAILABLE].

What do I do?

Also, when I upgraded, my webcam stopped functioning. However, since it may be related to the video driver, I'm holding off on that one until I have graphics in general working properly.

---

### Post by mastablasta on 2012-04-23
did you disable/remove the proprietary driver before upgrade?

---

### Post by jarokopitar on 2012-04-24
> **mastablasta said:**
> did you disable/remove the proprietary driver before upgrade?
No. But I did not exactly upgrade; my system had stopped booting, and the monitor doesn't receive any signal it can interpret until Xorg loads, so I installed the 12.04 pretty much from scratch.
Anyway, it's really a clean install.

---

### Post by VMC on 2012-04-25
Maybe its related to this bug [#982710]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982710").

The problem I have is r-clicking takes several seconds for focus.

---

### Post by jarokopitar on 2012-05-03
> **VMC said:**
> Maybe its related to this bug [#982710]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982710").

The problem I have is r-clicking takes several seconds for focus.
I don't think so.

My card isn't explicitly supported in the driver info, but the driver that does explicitly support it is unavailable.
And the extreme slowness means that I have to switch to a text console and back just to see the screen redraw if OpenGL is turned on. If it is off, it mostly works, but I no longer have access to text consoles, and the video is still sluggish.

So how can I install the proper driver?

---

### Post by mips on 2012-05-03
> **jarokopitar said:**
> 
I checked which driver I have installed; sure enough, it is nvidia-current, supporting GeForce series 6 and newer. GeForce 6100 is series 4, according to lspci.


6100 should be supported by nvidia-current, [http://www.nvidia.com/object/linux-display-amd64-295.40-driver.html](http://www.nvidia.com/object/linux-display-amd64-295.40-driver.html) as it's listed there as supported hardware.

Have you tried [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) ?

EDIT: Dould also be a nvidia bug, [http://ubuntuforums.org/showpost.php?p=11901260&postcount=6](http://ubuntuforums.org/showpost.php?p=11901260&postcount=6)

---

### Post by g9ahwkcm on 2012-06-06
Here's what worked for me on upgrade 11.10 -> 12.04 ubuntu, with nvidia geforce 6150 (this stinking card is an issue every stinking release)...

I tried every 32bit driver from nvidia from the latest to the 295.20 with no luck...

zivley 's post on 
[http://ubuntuforums.org/archive/index.php/t-1986601.html](http://ubuntuforums.org/archive/index.php/t-1986601.html)
got me most of the way there...

I also added acpi=off to my kernel line in /boot/grub/menu.1st as I think the nouveau frame buffer thing was hosing me up.

And I also installed lightdm, switched to the lightdm-gtk-greeter, as the unity-greeter wasn't allowing my userid to log in, all the other accounts would show up but mine.

Anyway good hunting...

---

### Post by bogan on 2012-06-06
Hi!, **jarokopitar,**

You Posted: > GeForce 6100 is series 4, according to lspci what does ```
lspci | grep -1A2 VGA
``` actually show?

According to the nvidia Driver site the GeForce 6100 is a GeForce 6 Series card, and is supported by the latest driver v 295.53
[http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html) 

That is for the 32bit version, make sure you get the right one.

Chao!,** bogan.**

---

