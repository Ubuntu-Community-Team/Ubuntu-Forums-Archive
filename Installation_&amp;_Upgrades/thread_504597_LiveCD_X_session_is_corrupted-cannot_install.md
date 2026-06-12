---
title: "LiveCD X session is corrupted-cannot install"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by porksmash on 2007-07-19
Hi guys and gals,

I've been trying to install Ubuntu on a new PC here, but whenever I get to the point where X starts, the graphics are all corrupted, almost like I am using a resolution that is unsupported by the monitor. Except in this case it is, because I select 640x480 in the VGA options when the liveCD boots (F4 I believe). I am using a NVidia 7300GS video card. It is fairly new, I am guessing, since it has an HDMI output, so is it possible that it is not being correctly detected or something?

When I ctrl+alt+f5 or something to switch to another terminal, all the text shows up correctly, so I really think it is just an X problem that is hopefully easy to fix. Any ideas?

---

### Post by taurus on 2007-07-19
Once option is the reconfigure X again.  While you are logged in from a console, run

```
sudo dpkg-reconfigure -xserver-xorg
```
Use the default values for all questions and pick vesa as a driver for your graphic card for now.  When done, get back to GUI and restart X again with <Alt>F7 and <Ctrl><Alt>Backspace.

Otherwise, use the alternate CD to install it since it uses text base installer.

---

### Post by porksmash on 2007-07-19
Thanks taurus.

In case anyone else has this problem, here is what I did.

So when the livecd reached the point where I should be seeing the gnome desktop, but got a garbled mess, I switched to another terminal (<ctrl>+<alt>+F3 or most any other F key besides F7). Then I ran the command ```
sudo nano /etc/X11/xorg.conf
```
Searched for the line that let me change the driver from "nv" to "vesa" and then deleted all resolution options except "1024x768" for the video modes below that. For some reason the vesa driver craps out also at a higher resolution with this card. Well anyway, this got me a clear video display so I could install ubuntu to the hard drive. 

After the install, I installed the binary nVidia drivers as per [this guide.]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29") Once the real drivers were installed, I restarted X and ran ```
sudo dpkg-reconfigure xserver-xorg
``` to reset all my resolutions to fit my monitor. 

This was not for 7.04, this was 6.10, by the way.

---

