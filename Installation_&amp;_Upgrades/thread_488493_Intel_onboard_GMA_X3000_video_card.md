---
title: "Intel onboard GMA X3000 video card"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by skooter on 2007-06-30
Hi,

I'm not having succes installing my onboard GMA X3000 (motherboard: ASUS P5B-VM SE). I'm running Feisty. 

What i did:

```
sudo apt-get install xserver-xorg-video-intel
```

... and then...

```
sudo dpkg-reconfigure xserver-xorg
```

... i chose "intel" for the list instead of "vesa" and finished the rest of the config. Then reboot.

After reboot i get a picture but still get this:

```
glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

```
cat /etc/X11/xorg.conf|grep Driver
        Driver          "kbd"
        Driver          "mouse"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "intel"
```

The video card supports OpenGL 1.5 and Shader 3.0...

What am i doing wrong slash missing?

---

### Post by tpg on 2007-06-30
I don't think it will work with the version of the intel video driver included with feisty. It will work with v2.0, which is currently in gutsy (the development version). Maybe someone knows of a source for the latest intel driver for feisty?

---

### Post by skooter on 2007-06-30
Hmm... that was some pretty sad info.

---

### Post by skooter on 2007-07-05
I found this ...
[http://www.intellinuxgraphics.org/](http://www.intellinuxgraphics.org/)

And this ... 
[http://en.wikipedia.org/wiki/Intel_GMA](http://en.wikipedia.org/wiki/Intel_GMA)
[http://support.intel.com/support/graphics/sb/CS-010512.htm](http://support.intel.com/support/graphics/sb/CS-010512.htm)


But i'm pretty nerves starting to compile my own kernel.

---

### Post by skooter on 2007-07-07
Ay... thats odd. Last night i tired the "intel"-driver again. And now it works. Don't remember changing anything. And I dont have the chance to test it with a game but MythTV runs smoothly. Also i get this:
```
glxinfo
Error: unable to open display (null)
```
But then i... 
```
sudo bash
su mythtv
export DISPLAY=:0  <--- maybe only with ssh
glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 965G 4.1.3002 x86/MMX/SSE2
```
(Remember to exit again from root!)

... So no need to compile the linux kernel as i thought.

Would be really nice to know what made the change, but i have no idea.

Here are some important things i found at: intellinuxgraphics.org ...

"In general, Intel graphics driver is well integrated in Linux distributions so users won't worry about the driver setup." 

"Question: Does the i965 3D driver support vertex shaders and other advanced GL functionality?
Answer: Yes, the i965 hardware supports a fully programmable GL pipeline and the driver exposes it through the GL API."

Also read the "Configuration"-part at: [http://www.intellinuxgraphics.org/install.html](http://www.intellinuxgraphics.org/install.html)

I attached the xorg.conf that worked for me. I'm using danish PS/2 keyboard and USB mouse, just that you know.

---

### Post by houston.hemi on 2007-11-29
I'm using an ASUS P5K-V motherboard with the Integrated graphics "Intel Graphics Media Accelerator X3000".  

Will your configuration file work on this system??  If so, please send steps on how to do this, for I am brand new to the Linux world. I'm lovin' it so far, but it is not very forgiving...

Thanks,

Houston.Hemi

---

