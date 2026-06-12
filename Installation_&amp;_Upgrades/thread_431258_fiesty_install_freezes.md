---
title: "fiesty install freezes"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by divine007 on 2007-05-02
Hey all,

I am very new to the linux OS, finally decided to give it a try this week.  I downloaded the 7.04 CD, verified it and checked it for errors - all ok.  My system boots to the install options menu, i choose Install, it goes all the way through to the Ubuntu light brown screen and freezes - the graphics seemed a little distorted.  

I figured it was something with the graphics card (Nvidia 7800gt) so I booted it in "video safe mode."  Everything worked flawlessly, but there isn't an option to install using the same safe mode.

My question, is this a known problem?  IF so, how can I fix this video problem so I can install it?

System Specs:
Opteron 165
DFI lanparty ut nf4 ultra-d
Nvidia 7800 GT
2gigs Ram

---

### Post by zvacet on 2007-05-03
Boot in recovery mode and type

```
dpkg-reconfigure xserver-xorg
```

select **nv** instead of** nvidia**

---

### Post by divine007 on 2007-05-04
**UPdate:**
I got it installed using the ALT CD.  Had some minor problems, all of which were my fault.  Note to anyone new to this, make sure the Ubuntu drive is PRIMARY. lol.  Once I did that everything fell into place.
[B]
Problem:[/B]
I get past the GRUB menu into Ubuntu, it asks for my name then password.  After I press enter at the password screen the graphics get pixelated.  Just like when I was trying to install from teh GUI/ regular CD.

**What I tried so far:**
Restarting and loading the Restore COnsole, then typing "dpkg-reconfigure xserver_xorg".  I get an error message, "Package "xserver_xorg" is not installed and no information is available".

What am I doing wrong?  I know it's a graphics issue because if I boot the Live CD and have it load in safe graphics mode everything works.

Please help, i'm soooo close.  Been at this for three days straight.

---

### Post by divine007 on 2007-05-04
wow, that was a mission... but i'm all set now.

Here's how I fixed it:

Loaded Restore Mode

type:  sudo apt-get update  
that should download any updates you need

type:  sudo apt-get dist-upgrade
that should get other updated

typed "uname -r"

sudo apt-get install linux-generic (replace generic with whatever version uname tells you)

once that's done, type:  sudo apt-get install nvidia-glx-new    (the new is for teh 7800-8800gt cards)

then, enable the driver, type:  sudo nvidia-xconfig --no-composite

then restart.  That's all, worked for me.

---

