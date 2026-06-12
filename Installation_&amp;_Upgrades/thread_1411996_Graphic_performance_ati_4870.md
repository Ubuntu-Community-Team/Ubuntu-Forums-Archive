---
title: "Graphic performance ati 4870"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by Perfex on 2010-02-20
Hello,

I just updated my graphics card to an ati 4870 2gb, and installed Karmic, everything went smooth with the install, though after installing the restricted drivers for my card, seems sluggish, aspecialy when I try to resize a window

Does anyone have any insight into this? or a driver set that works better

Current System:
abit at8-32
amd fx55
mushkin x 4 gig
sapphire toxic 4870 2gig

(visual affect set to normal)

---

### Post by Vakman on 2010-02-20
Hm, I had hoped someone else would reply, nobody did so I guess I will have to.
Where did you install the drivers from, like in what way? Just from the System > Administration > Hardware Drivers?
Please run ```
glxinfo | grep direct
``` thought I don't think that will matter because it will say "Yes: but do so anyhow.
Try turning the Visual Effects to "None" and see if that helps as well.

---

### Post by Perfex on 2010-02-20
:~$ glxinfo | grep direct
direct rendering: Yes

I have installed the restricted drivers - 3D-accelerated proprietary graphics driver for ATI cards.

its all working, though just sluggish, do the open drivers have better performance?

Performance is better with the affects off, though my hardware is sufficient enough for anything ubuntu can dish out

---

### Post by Vakman on 2010-02-20
Hm, I have not had much success installing from there.
Try to install the ones from the website - [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) and install it. The ones from that manager never seem to have success for me but I think they are the same ones but regardless install those.
Follow [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually)
The Jaunty guide works for Karmic so do not worry about that.

---

### Post by Perfex on 2010-02-20
Thanks for the advise, will see if that method helps, will work on that later this evening

---

### Post by Perfex on 2010-02-20
OK I used the method you suggested

~$ glxinfo | grep direct
direct rendering: Yes

~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series 
OpenGL version string: 3.2.9551 Compatibility Profile Context

I still notice delays in resizing windows, though maybe there is supposed to be a delay?

I'm puzzled

---

### Post by Perfex on 2010-02-20
Well I guess the delay is a bug, after combing google I found

[http://blog.jasondonenfeld.com/169](http://blog.jasondonenfeld.com/169)
[http://www.phoronix.com/forums/showthread.php?t=15163](http://www.phoronix.com/forums/showthread.php?t=15163)

apparently its an xorg bug, or not all depends on what you read, some say has to do with an intel fix, some say ati

---

### Post by Vakman on 2010-02-21
> **Perfex said:**
> Well I guess the delay is a bug, after combing google I found

[http://blog.jasondonenfeld.com/169](http://blog.jasondonenfeld.com/169)
[http://www.phoronix.com/forums/showthread.php?t=15163](http://www.phoronix.com/forums/showthread.php?t=15163)

apparently its an xorg bug, or not all depends on what you read, some say has to do with an intel fix, some say ati

Hm, odd. I knew about this bug but I did not notice it since installing updated drivers. Then again, I have a 4850.
Sorry that I couldn't be of more help.

---

### Post by Perfex on 2010-02-21
and you have compiz turned on?

---

### Post by Vakman on 2010-02-21
> **Perfex said:**
> and you have compiz turned on?

On or off. Makes no difference in reference to the sluggish-ness.
Usually I have them on.

---

