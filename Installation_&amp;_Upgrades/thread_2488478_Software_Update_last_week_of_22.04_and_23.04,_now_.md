---
title: "Software Update last week of 22.04 and 23.04, now can't detect external monitors"
date: 2023-07-05
forum: Installation &amp; Upgrades
---

### Post by Uone on 2023-07-05
I have two laptops:

[LIST]
[*]**pyxis** runs **22.04LTS** on a** Lenovo X1E with a Nvidia GTX 1050 Ti** and one external monitor connected via HDMI
[*]**crux** runs **23.04** on a **Lenovo Legion Pro 7 with a NVidia RTX 4080** with two external monitors: a 4K BenQ monitor via USB-C to DisplayPort, and a Dell HD monitor connected via HDMI
[/LIST]
I've been running both of these machines for months, just updating (i.e., not upgrading) the software weekly. All external displays worked fine.

I run Software Updater on Fridays. After last week's update (6/30), the external monitors **_disappeared_** - they're not detected at all :-(

I'll focus on the Legion Pro machine, **crux**, because that's my main machine.

I know that the hardware is connected properly since I can run Windows 11 and can use all three screens (the laptop and two external monitors).

I have these drivers installed:

$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd000027E0sv000017AAsd00003B64bc03sc00i00
vendor   : NVIDIA Corporation
model    : GN21-X9
driver   : nvidia-driver-535 - distro non-free recommended
driver   : nvidia-driver-525-open - distro non-free
driver   : nvidia-driver-525 - distro non-free        <- using this one
driver   : nvidia-driver-535-open - distro non-free
driver   : nvidia-driver-525-server - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

**Control Center/Displays** shows only the laptop screen. No external displays are shown. Why are they not detected?

**Software & Updates** aka **software-properties-gtk** says that I'm using **NVIDIA driver metapackage from nvidia-driver-525 (proprietary)**.

Questions:


[LIST=1]
[*]What happened? Shouldn't an software update improve rather than disable capabilities?
[*]The package xserver-xorg-video-nvidia-525-server is installed, but nvidia-settings no longer shows the X Server Display Configuration - why not?
[*]How does the system detect external monitors? Is there some configuration file that I need to reset?
[*]If I have to, I'm willing to re-install Ubuntu. But that's a major operation and I can't help thinking that there's gotta be a simpler fix ...
[/LIST]

Any suggestions? Thanks!

---

### Post by MAFoElffen on 2023-07-05
Did you try to remove / purge then reinstall your nVidia drivers? 

After 17 years of using nVidia on Unix and Linux systems, if something happens to my graphics, that is the first thing I do.

So much so, that I came up with this script that does it for me:
```

#!/bin/bash

## MAFoElffen, <mafoelffen@ubuntu.com, 2010.06.22
#      updated 2014.04.20
#  Name: reinstall-nvidia.sh
# 

DRIVER=$(apt list nvidia-driver* --installed 2> /dev/null | awk -F "/" ' ! /Listing/ {print $1}')

sudo apt remove --purge -y $DRIVER
sudo apt install -y $DRIVER


```

---

### Post by Uone on 2023-07-06
Thanks much for your help and your script. Through trolling through past posts, I found the purge/install suggestion and I tried it manually (not as easy as your clever script.

Unfortunately, it didn't help.

But I did finally get it to work after close reading of Xorg.0.log and detective work. It's a long story so I'll cut to the chase.

The software update that I installed on Friday updated the kernel to use the NVidia lowlatency drivers - that's why both my 22.04 and my 23.04 machines were affected. Unfortunately, that update requires lowlatency NVidia modules. But they require the proper Linux headers, in particular the ones in linux-headers-6.2.0-1007-lowlatency package.

But for some inexplicable reason, apt and Synaptic cannot find this package. And that means that the Nvidia modules cannot be loaded; so it falls back on the generic and minimal nouveau driver. Because the Nvidia modules did not load, the Xorg server is crippled. Since it's the X server that seeks external monitors, it never did so.

So I fell back to the 6.2.0-24-generic drivers, and now all is well.

As usual, bugs like this are simple ... once you find them. But finding it took a lot of time.

And I only encountered this problem because my upgrade could not find the linux-headers-6.2.0-1007-lowlatency package. I suppose that other people found it since I haven't heard of any other reports.

---

### Post by MAFoElffen on 2023-07-07
Thank you for telling me... Now I can look out for those on my two machines with nVidia. Dang. LOL.

Please use the Thread Tools and mark this thread as "Solved" so that others can find your your solution. As I'm sure that others are also affected by that update.

---

### Post by rossminet on 2023-07-16
I also found the solution after three weeks of searching for a solution. I learned a lot.

The 6.2.0 kernel update crashed. I had the oracle-kernel as the main kernel. I switched to low-latency but could not install any nvidia proprietary. Only X wirh Nouveau would work.

I finally discovered that the nvidia kernel module could not load because the low-latency headers were missing.
Once installed, I had to "enroll the mok" (due to secure boot), a process new to me. I can't disable secure boot since I also use Win 11.

When you enroll the mok, you have to be very careful with picking the password. There's a qwerty azerty problem. I simply type 8 adjacent characters; it will work on qwerty and azerty.

---

### Post by jsheedy on 2023-07-18
Would you be able to provide more information as to all steps you have taken?    I have been unable to resolve this. 
for me nvidia 535 drivers have been installed under Ubuntu 23.04
Wayland is disabled
mokutil has been run.
lowlatency headers have been installed. 

Xorg log
[   662.301] (II) UnloadModule: "libinput"
[   662.335] (II) NVIDIA(GPU-0): Deleting GPU-0
[   662.369] (II) Server terminated successfully (0). Closing log file.

NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.

[daemon]
# Uncomment the line below to force the login screen to use Xorg
WaylandEnable=false

---

### Post by jsheedy on 2023-07-19
Well, I ran through the entire process again, uninstalled all manually 535, installed 525, and now it does seem to work.  Any time a new version comes out(nvidia), or a new kernel is released,  I get a bit anxious that I will be killing X.  All is good for now

---

