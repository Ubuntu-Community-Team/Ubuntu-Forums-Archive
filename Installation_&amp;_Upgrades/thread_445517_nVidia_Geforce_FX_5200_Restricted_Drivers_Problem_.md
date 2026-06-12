---
title: "nVidia Geforce FX 5200 Restricted Drivers Problem solved!"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by ZeroVerteX on 2007-05-16
I was originally unable to get the restricted drivers to work out-of-the-box with Feisty. After alot of digging I found Envy ([http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")), a very nice utility to assist in the installation of the nVidia and ATI restricted drivers. I did have to reload my installation to finally get it working right but here are the steps.

Install Ubuntu Feisty Fawn 7.04 from desktop install CD with nVidia Geforce FX 5200 installed
Ran updates
installed ssh (just in case i couldn't locally get back to a terminal)
installed Envy 0.9.3
installed nVidia driver 1.0.9755 via Envy
rebooted to a black screen with no X and no terminal
SSH'd in from my laptop and edited /etc/X11/xorg.conf to read

```
Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
    BusID "PCI:1:0:0"
    Option "AddARGBGLXVisuals" "True"
    Option "NvAGP" "1"
EndSection

```

Rebooted to a glorious GDM login using restricted nVidia drivers.

I suppose one could edit the xorg.conf before restarting to save from having to SSH from another machine or fight with Xwindows to get a virtual terminal going.

I'm going to try to submit this to launchpad so maybe a patch can be issued. I'm not a programmer so I won't be making any patch. Please excuse any typos or misspellings as it is very late. Cheers and good luck!

[http://www.zerovertex.com](http://www.zerovertex.com)

---

### Post by joe.turion64x2 on 2007-05-16
> **ZeroVerteX said:**
> I was originally unable to get the restricted drivers to work out-of-the-box with Feisty. After alot of digging I found Envy ([http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")), a very nice utility to assist in the installation of the nVidia and ATI restricted drivers. I did have to reload my installation to finally get it working right but here are the steps.

Install Ubuntu Feisty Fawn 7.04 from desktop install CD with nVidia Geforce FX 5200 installed
Ran updates
installed ssh (just in case i couldn't locally get back to a terminal)
installed Envy 0.9.3
installed nVidia driver 1.0.9755 via Envy
rebooted to a black screen with no X and no terminal
SSH'd in from my laptop and edited /etc/X11/xorg.conf to read

```
Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
    BusID "PCI:1:0:0"
    Option "AddARGBGLXVisuals" "True"
    Option "NvAGP" "1"
EndSection

```

Rebooted to a glorious GDM login using restricted nVidia drivers.

I suppose one could edit the xorg.conf before restarting to save from having to SSH from another machine or fight with Xwindows to get a virtual terminal going.

I'm going to try to submit this to launchpad so maybe a patch can be issued. I'm not a programmer so I won't be making any patch. Please excuse any typos or misspellings as it is very late. Cheers and good luck!

[http://www.zerovertex.com](http://www.zerovertex.com)
That is strange, I have that same graphics card and it always fine with any Linux I have tried. Even the LiveCDs with Beryl load it by default.

It's good to know the problem is solved.

Joe.

---

### Post by ZeroVerteX on 2007-05-21
And honestly, I don't know if just adding the lines to the xorg.conf might have fixed the problem without using Envy. Might try on the next reload if there is one.

Also, just a side note, I've got an old Gateway machine with a 950Mhz PIII and 320MB RAM. I've added the MSI GeForce MX 5200 AGP card and it runs better than anything I've seen running VIsta. :p

---

