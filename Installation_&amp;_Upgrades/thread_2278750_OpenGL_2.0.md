---
title: "OpenGL 2.0"
date: 2015-05-18
forum: Installation &amp; Upgrades
---

### Post by cj-walfall on 2015-05-18
Could someone walk me through how to install OpenGl 2.0 on Ubuntu 14.04 LTS. I need it in order to play a game (starbound) that i downloaded from steam.

---

### Post by grahammechanical on 2015-05-18
Two things are relevant to this matter. The video adapter and the video driver. Both should meet the OpenGL 2.0 standard. Run this command

```
/usr/lib/nux/unity_support_test -p
```

It is a test to see if our video adapter is capable of running Unity 3D. It will give some relevant information. This is what I get
> graham@sdb1-Uplus1:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GT 220/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 304.125

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

It tells me that both the video adapter and the driver meet the OpenGL 3.3 standard. If I was using the open source video driver I would see this difference

> OpenGL vendor string: nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string: 3.3.0 Mesa 10.0

I am running 15.04 so I have newer Mesa packages than 14.04. Lets us first see if you need a driver capable of meeting the OpenGL 2.0 specification.

Regards.

---

### Post by cj-walfall on 2015-05-18
when i run this in the terminal glxinfo | grep version , i get this:

server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL version string: 1.4 Mesa 10.1.3

when i run a steam app, in the logs i get this error witch cause's the app to crash:
 
[22:35:18.665] Error: Failed to initialize graphics mode: (GraphicsException) OpenGL 2.0 not available!

does anyone know how to update openGL to 2.0 so that i don't get this error?

---

### Post by cj-walfall on 2015-05-18
when i run the code i get the same thing as you

---

### Post by cj-walfall on 2015-05-18
mabey this is irrelevent but i have been trying to fix this problem for a couple hours now and when i try to watch a youtube video, the video doesn't load and stay black.

---

### Post by cj-walfall on 2015-05-18
not to be rude or anything but what next?

---

### Post by deadflowr on 2015-05-18
> **cj-walfall said:**
> not to be rude or anything but what next?

Please post the out from the command from post #2, please.
Though it may show some information that may be the same. Not all the information will be the same.
Particularly the information about the graphics card in use.

```
lspci | grep VGA
```
can also give you the info on the card you have.

---

### Post by cj-walfall on 2015-05-18
this is what I got:

OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Q35 
OpenGL version string:  1.4 Mesa 10.1.3

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

---

### Post by cj-walfall on 2015-05-18
when I run lspci | grep VGA , i get this:

00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)

---

### Post by Vladlenin5000 on 2015-05-18
OpenGL and Youtube aren't related.
What do you mean by the same results? And which ones, by the way? He posted two...

[Starbound system requirements]("http://playstarbound.com/system-requirements/") regarding graphics is just ```
**Graphics:** 256 MB graphics memory and opengl 2.1 compatible gpu
```
This is the minimum. If you already have a version higher than 2.1 you don't need to install anything else. Assuming you are running any recent (supported) Ubuntu version or variant or ANY other modern Linux distro, have a fairly decent graphics card/chip with at least 256MB, with either open source or proprietary drivers correctly installed _you already have everything you need_. **UPDATE**: Apparently you don't, sorry... ```
OpenGL version string:  [COLOR=#ff0000]1.4[/COLOR] Mesa 10.1.3
```

So... Here's my suggestion:
(Removed, no solution)


YouTube requires either HTML5 (preferred) or Flash. Google Chrome already defaults to HTML5, Firefox as well if I'm not mistaken. Chrome also come with updated Flash so it works in all scenarios. You can also install Flash system-wide for Firefox and other apps but you NO longer need it for YouTube, it just works (always, provided the graphics drivers are working correctly). So... Besides OpenGL related stuff, what else have you messed with already?

---

### Post by cj-walfall on 2015-05-19
fisrt I have opengl 1.4 Mesa 10.1.3. i need to upgrade it to 2.0 in order to run starbound. for your second question iI don;t remember the site i was on because i visited so many trying to fix the proble. but i do remember installing some kind of graphic driver's or something a long those lines. after that i realized i didn't want what i installed so i used a code that was provided on the same page to undo what i did and something about using defult graphic drivers. 
SORRY i know its not much to go on but any help is welcome

---

### Post by Vladlenin5000 on 2015-05-19
It's an old Intel. Drivers for Intel graphics are open source and installed by default. It's unlikely you could have done something drastic and any recent version should work.
The problem is your integrated graphics doesn't support the openGL version required. It's hardware, not software.

---

### Post by QIII on 2015-05-19
@cj-walfall:

This thread is tagged as "Lubuntu" and some of the advice given will not work on Lubuntu -- you'll get an error.

Is this Lubuntu or Ubuntu?

---

### Post by mc4man on 2015-05-19
You need newer Hardware. If this is a laptop then get a better/newer one, if a desktop maybe you could find some video card for it but old & crappy will likely remain such.

---

### Post by QIII on 2015-05-19
Threads merged.  Please to not start multiple threads regarding the same issue.  It causes a dilution of the Forum's ability to help when people answer in more than one place, as happened here.  It can become confusing for you and for those who try to help.

---

