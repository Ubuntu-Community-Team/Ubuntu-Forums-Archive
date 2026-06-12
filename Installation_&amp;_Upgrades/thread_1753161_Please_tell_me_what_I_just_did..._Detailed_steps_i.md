---
title: "Please tell me what I just did... Detailed steps included"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by 3602 on 2011-05-08
In an attempt to correctly play Half-Life 2 in Wine, I installed the AMD driver downloaded from their site.
```
sudo sh ati-driver-installer-11-4-x86.x86_64.run
```
Reboot. Now, with both FireGL and this running a conflict is created. Naturally the system boots into command prompt. So:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
and reboot. Got a graphical user interface. There was no OpenGL as the GLX-Dock has a large black bar behind it.
Went into Synaptic and completely removed:
```
fglrx
fglrx-amdcccle
fglrx-modaliases
xserver-xorg-video-radeon
xserver-xorg-video-all
xserver-xorg-video-ati
```
Reboot. Got OpenGL, but performance is choppy. Glxgears is very choppy.
So how to revert to the old fglrx? There is an uninstall script at /usr/share/ati. Shall I run that or shall I reinstall all of the above removed packages beforehand?
Thank you very much.

---

### Post by 3602 on 2011-05-08
So I ran the uninstall script and re-installed all those removed packages. Now I don't even have OpenGL (no GLX-Dock, no Compiz). Trying to run glxgears gives me:
```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

---

### Post by alphacrucis2 on 2011-05-08
Don't install the amd/ati driver that way. Use the buildpkg method as explained in the binary driver HOWTO. That way, the package management system knows that you have installed fglrx and also which version you have installed. You are asking for trouble installing stuff outside of the package management system.

[URL="https://help.ubuntu.com/community/BinaryDriverHowto/ATI"]https://help.ubuntu.com/community/BinaryDriverHowto/ATI
[/URL]

BTW probably what you forgot to do was initialise the ati config. Always do this after installing fglrx and before rebooting:

```
sudo aticonfig --initial -f
```

The -f may not be required but better to be safe than sorry.

---

### Post by 3602 on 2011-05-08
Thank you! Now I got my GLX-Dock back and 2794 FPS in glxgears!
But: One question. In Jockey, the FireGL driver is deactivated and it says "a different version of this driver is in use". What is this different version:
Here's my fglrxinfo output if it can help:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200 Series
OpenGL version string: 3.3.10362 Compatibility Profile Context

```

---

### Post by alphacrucis2 on 2011-05-08
> **3602 said:**
> Thank you! Now I got my GLX-Dock back and 2794 FPS in glxgears!
But: One question. In Jockey, the FireGL driver is deactivated and it says "a different version of this driver is in use". What is this different version:
Here's my fglrxinfo output if it can help:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200 Series
OpenGL version string: 3.3.10362 Compatibility Profile Context

```

I'm guessing the different version being the one downloaded from AMD?

---

### Post by 3602 on 2011-05-09
It shouldn't be, I ran the *fglrx-uninstall.sh* found in */usr/share/ati *sincebefore the second post
 
EDIT: Purged all fglrx again and installed the run script according to the BinaryDriverHowTo page. All is well.

---

