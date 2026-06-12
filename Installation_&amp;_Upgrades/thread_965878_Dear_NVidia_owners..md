---
title: "Dear NVidia owners."
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by 4leite on 2008-10-31
Hi,

I am fortunate to have a reasonable knowledge of Ubuntu/Gnu/Linux. So I thought I'd plunge ahead with this whole update business even though I have one of the 'problem' cards. First, thanks for all the useful posts and bug reports. Having installed the latest binary driver from NVidia's site I now have, for the first time in Ubuntu, dual monitor's with a virtual desktop large enough to fit my widescreen and laptop monitor, without having to hack X, xorg.conf, kernel, drivers, etc.

Thought I'd share a few things...
You have been warned - there are heaps of warnings all over the place that if you have an NVidia card, you might run into problems. If you own a laptop and you think you might be affected and or you don't know what sort of graphics card you have (There'll most likely be a wee NVidia sticker on your laptop) and you're not confident with the command line, install Hardy 8.04.1 and wait till this is sorted.

If you do the upgrade and you want help, being nice to people gets a better response and is more likely to solve your problem. If you want to let off some steam - get in touch with NVidia and rant at them.

I've seen a lots of posts from desktop owners saying just stick with the fallback 'nv' driver and go without 3d effects. Most of the time, those of us with laptops are much less interested in the magical 3d effects and much more interested in seeing anything at all on the screen / on our external monitor / both (at least this upgrade I got a 640x480 screen).

I have an NVidia Geforce go 7300 card on Ubuntu (Gnome) x86_64. Which is a legacy card according to some of the Nvidia site, a currently supported card according to other bits and doesn't exist at all according to the driver download page. Apparently the 177.80 driver supports (this is what I am running now).

If you know that you have a legacy driver, check here: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/+bug/251107](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/+bug/251107)

--> Don't think this is the recommended method, but it worked for me.

Otherwise, here's what I did:
Drop to prompt (ctr+alt+f1).
Install build-essential:
```
apt-get install build-essential
```
Download driver ([www.nividia.com](www.nividia.com))
```
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/177.80/NVIDIA-Linux-x86_64-177.80-pkg2.run
```
```
sh NVIDIA-Linux-x86_64-177.80-pkg2.run
```
Answer prompts.
Reboot.
(Open terminal)
Backup xorg.conf so NVidia-settings doesn't get confused:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Run NVidia-settings.
```
sudo nvidia-settings
```
....

Hope this helps someone out.

If you're into such things, it might be worth posting a link to relevant pages for each card, cause it took me ages to figure out which driver I should be using.

---

### Post by 4leite on 2008-11-01
update:

For some reason 'move window' was on and set to button1 by default. To use mouse I had to press a the fn key or my mouse just grabbed the window. Disabled and fixed now. Not sure if it was related or not...

---

### Post by spaceghoti on 2008-11-01
32-bit users will want to use ```
wget http://us.download.nvidia.com/XFree86/Linux-x86/177.80/NVIDIA-Linux-x86-177.80-pkg1.run
``` instead of the 64-bit version listed here.

---

