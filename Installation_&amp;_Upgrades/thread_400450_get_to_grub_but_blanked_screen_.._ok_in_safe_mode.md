---
title: "get to grub but blanked screen .. ok in safe mode"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by pixelpainter on 2007-04-03
Hi, I'm an Ubuntu newbie, and I have had some success with Fedora in the past. I just built a new system based on nvidia 680i chipset with an evga 8800 video card.

Ubuntu installed fine, grub loads fine, dual boot windows xp and Vista loads ok...  but when I select kernel to boot I get a blank screen after "Grub 1.5" , it looks like there is some hdd activity for a sec, then nothing. No Ubuntu logo no text (even if I boot without quiet mode on) 

I am able to boot into safe mode, and using "startx" I am able to get into  GUI, I have fully updated everything... but still no luck.

I am assuming this is a hardware/driver issue... but I can't figure out what it is.. and I am sorry to say it is driving me nuts.

I have looked here on the forums.. and although I have seen similar issues... it does not seem that any of them allow to boot into safe mode and start up x.... so it seems this situation is a little different.

Is there a way to check for errors... i am afraid I do not know how to do this... any suggestions or help would be much appreciated as booting in safe mode is not a permanent solution :(

Thanks in advance 
Daniel

---

### Post by garlik42 on 2007-04-03
I had a similar problem with the 64 bit feisty-0331 dvd on boot, the log file for X11 is in /var/log/Xorg*log

What I found, was the Nvidia driver that was on the disk couldn't handle my card. So I installed in safe mode, and then switched the video driver from nvidia to "vesafb"  (/etc/X11/xorg.conf) or it might have been "vesa". Once I made the change to vesa, the system booted fine but in a low resolution, I did an upgrade with apt-get, got the latest and greatest, then switched back to the nvidia driver and all is well.

I know this is not the exact same problem but maybe it will give you some ideas.

---

### Post by pixelpainter on 2007-04-03
Thank you so much, and yes a big help :)
Also managed to find out there are issues w/the 8800 card, and it seems one must get the newest nvidia driver (and I think they also have newer glx driver) from nvidia site.

I have added some quotes from info on other posts :) hope this of use to others :)


> 
Currently the driver that comes with Feisty is 9631, and nvidia only added support for the Geforce 8 series in the 9746 and greater driver. It's been officially out for months now. Plus it seems there is also a new 9755 driver out (that the Envy script already supports) that adds the following;

* Added support for Quadro FX 4600 and Quadro FX 5600
* Added initial support for NVIDIA SLI with GeForce 8800, Quadro FX 4600, and Quadro FX 5600


> 
8800 GTX is only working with the drivers from nvidia.
for x86 you can find here : [http://us.download.nvidia.com/XFree8...-9755-pkg1.run](http://us.download.nvidia.com/XFree8...-9755-pkg1.run)
for x64 hre : [http://us.download.nvidia.com/XFree8...-9755-pkg2.run](http://us.download.nvidia.com/XFree8...-9755-pkg2.run)


> 
The nvidia-glx package drivers won't work with the 8x series cards. Get the latest ones off Nvidias website (NVIDIA-Linux-x86-1.0-9755-pkg1.run) and just 'sudo sh' it outside of xserver (or whatever you guys call it, the GUI).


> 
Running beryl with no problems on an 8800 GTS. Simply added the fiesty beryl repos and installed beryl.


---

