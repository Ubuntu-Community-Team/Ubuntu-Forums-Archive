---
title: "Two monitors on two graphic cards"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by harberst on 2011-06-10
I've been searching for two days and haven't found an answer yet, but maybe I missed something.  If there is already an answer please share it, if this isn't the right place for this question please let me know where I should ask.

Okay so to start with I'm using Ubuntu 11.04. I should have two graphic cards, and they are both detected in the terminal. 
 
```
 lspci | grep VGA
02:00.0 VGA compatible controller [0300]: nVidia Corporation C77 [GeForce 8200] [10de:084b] (rev a2)
03:00.0 VGA compatible controller [0300]: nVidia Corporation G98 [GeForce 8400GS] [10de:10c3] (rev a2)

```Both cards have monitors plugged into their VGA ports, but only one of the monitors shows a display.  The other monitor goes into power saver mode right after start up. Nvidia X Server settings only shows a single graphics card (the 8200) and a single monitor (detect monitor finds nothing). Going through Prefences: Monitors also only shows a single monitor and doesn't detect a thing when detect monitors is clicked. 

Monitor one has 1440 x 900 resolution and I'm not sure what the resolution of Monitor two is supposed to be, but it displays rather nicely at being set to 1440 x 900.

Both graphics cards are detected and usable in Vista, but a quick switch of the plugs shows that only the 8200 is registering in Ubuntu.  

Ideally I want to have a dual monitor set up, with one screen showing documents or pictures with the other using Gimp or Blender.  Any help in setting this up would be greatly appreciated.

---

### Post by harberst on 2011-06-12
Bump for help please?

I think the main problem is that even though the terminal detects the 2nd card when ordered, it's not in use. How would one go about, well, activating it?

---

### Post by harberst on 2011-06-15
Are ya'll seriously telling (silently) that no one can help with this?

---

### Post by bcschmerker on 2011-06-16
This issue of dual GPU's appears similar to [a situation for which I am fielding recommendations](http://ubuntuforums.org/showthread.php?t=1776921) (none received as of 15 June 2011), as I have an [eMachines®/Acer® EL1210-09](http://www.emachines.com/) (Advance Micro Devices® Athlon 64® LE-1620, [nVIDIA® MCP78S chipset/GeForce® 8200 IGP](http://www.nvidia.com/)) recently rebuilt as a 64-bit Lucid box and now in testing.  nVIDIA® supports several generations of GeForce® GPU with a proprietary driver and settings-application package in the Restricted repository.  The GeForce® 8200, according to nVIDIA® documentation on Hybrid SLI (Hybrid SLI being supported only in Microsoft® Windows® 6-up), should be able to see the video memory of a PCI-Express x16 add-on card.

Can't comment on seeing dual GPU's in **xserver-xorg-nv**, as the dual-GPU situation is quite new to me.

---

### Post by harberst on 2011-06-17
bcsmerker: Thanks for the reply. I've been noticing a lot of issues relating to dual gpus/monitors floating around here.

And all that digging around has led me to a desire to change my question. How can I get the 8400 to register as the main card? I'm seeing a lot of stuff about editing the xconf, but I don't really see any clear and concise (to me anyway) explanations of why/what is going on (I'm very much not a programmer, just an overly curious wannabe writer/artist type). Do I need to muck about with the xconf? If so what (and simple why's) do I need to do? Thank you to anyone who can help.

---

### Post by lrbh on 2011-12-01
Any advance on this?  (He asked, hopefully.)

---

