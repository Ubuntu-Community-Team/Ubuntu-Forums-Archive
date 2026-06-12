---
title: "[Solved] Default audio device - Ubuntu 19.10"
date: 2019-10-18
forum: Installation &amp; Upgrades
---

### Post by Silverfox_28 on 2019-10-18
I installed Ubuntu 19.10, but at the first boot I notice that there is no audio coming from the ALC1150 chip audio on my Gigabyte motherboard. I go to audio settings an I realize that the device set by default is that of the video card (HDMI/DisplayPort 5 - Ellesmere HDMI Audio), then change to "Line-Out - Internal Audio" and restart the PC. But on restart, bad surprise, there is still the same problem. How can I change the default audio device?

---

### Post by trmfach on 2019-10-19
Same problem here.
Fresh install of Ubuntu 19.10. Default output device after start was the output from my AMD Radeon RX 560 Series. I wasn't able to change it to the preferred analog Line-out output. After changing it in "Settings" it reversed after the next boot. 
Because of a unequal mouse movement (cursor moves sometimes suddenly slower and after that fast again) I decided to go back to 19.04.

---

### Post by bhupsi on 2019-10-20
Same problem.  On upgrade from 19.04 to 19.10 I have no sound out.  Shows audio out as HDMI/Displayport instead of Built-in audio.  I get audio back by going into settings, sound and changing to Built-in Audio.  Rebooting causes problem to re-appear.  I am on an Hp Pavilion laptop.  lspci shows:  Audio device: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Audio Controller

---

### Post by CatKiller on 2019-10-20
One of the pulseaudio utilities - I can't remember which one - lets you select the default audio device easily. That functionality is built into the normal KDE settings, which is why I can't remember what the extra utility is called that you need to install if you're using Gnome.

---

### Post by bhupsi on 2019-10-20
I found a bug report on this problem and a fix in the comments that worked for me:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1847570](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1847570)

The fix was :
Comment out from  /etc/pulse/default.pa

load-module module-switch-on-port-available
load-module module-switch-on-connect
 
reboot

---

### Post by ya-paulle on 2019-10-26
Same here.

---

