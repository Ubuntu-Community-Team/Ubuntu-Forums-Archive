---
title: "Only able to login with Ubuntu 2D"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by PZJM on 2011-11-20
Hey folks, I have upgraded my laptop from 10.10 to Ubuntu 11.10 64 bit. However, when I login using the regular Ubuntu option I have no options except a couple of menu options at the top. I then tried using the Ubuntu 2D option and everything showed up. I'm not sure why this is happening. I'm hoping someone may be able to shine some light on this subject. Here is some of my laptop specs:

Toshiba Satellite A305-S6916
Intel Dual Core Processor
512 Dedicated ATI graphics card Radeon 3600

---

### Post by fantab on 2011-11-20
> **PZJM said:**
> Hey folks, I have upgraded my laptop from 10.10 to Ubuntu 11.10 64 bit. However, when I login using the regular Ubuntu option I have no options except a couple of menu options at the top. I then tried using the Ubuntu 2D option and everything showed up. I'm not sure why this is happening. I'm hoping someone may be able to shine some light on this subject. Here is some of my laptop specs:

Toshiba Satellite A305-S6916
Intel Dual Core Processor
512 Dedicated ATI graphics card Radeon 3600

Run the following in Terminal to see if your Satellite can run UNITY:

```
/usr/lib/nux/unity_support_test -p
```

If you don't understand the results, then post the output here.

---

### Post by PZJM on 2011-11-20
Here is the output:


laptop:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 3650
OpenGL version string:  3.3.11005 Compatibility Profile Context

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

From the output it looks like it should be supported. Does this sound correct?

---

### Post by fantab on 2011-11-20
Yes, it is supported and it should work.

Have you updated your new installation?
 If not do it. I remember I too had such a problem when I first installed 11.10_64bit but since updates it works beautifully.

If updates don't solve your problem then, maybe you'll have to check your graphics driver. I am not sure. First try Updating your system.

---

### Post by PZJM on 2011-11-20
Thanks. I'll give it a try tomorrow.

---

### Post by PZJM on 2011-11-21
Well, I ran an updated and then logged back in using "Ubuntu" instead of "Ubuntu 2D".  It did not work:(. The only thing on my desktop is a menu bar at the top of the screen. I'm not sure what is going on but it's annoying. Are there any other troubleshooting techniques I need to look into.

Thanks...

---

### Post by trundlenut on 2011-11-21
I came across this thread and I am suffering for this problem too.  I have done a fresh install on an HP Laptop with ATI X 1250 chip.

When I try to login to Unity I just get the default background, no menus nothing.  If I change to a terminal when I change back I just get the mouse on top of the terminal output!

I ran the command as suggested by Fantab and got the same output as PZJM.

The first thing I tried was updating everything, but it didn't help.  Unity 2D works fine though.

---

### Post by PZJM on 2011-11-21
Hey trundlenut, I found this link that stepped my through how to reset some of the default settings. Here is the link

[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

I only used these three commands

unity --reset-icons
unity --reset
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset

Afterwards, I was able to utilize "Ubuntu" instead of "Ubuntu 2D". I hope this helps.

---

### Post by trundlenut on 2011-11-22
> **PZJM said:**
> Hey trundlenut, I found this link that stepped my through how to reset some of the default settings. Here is the link

[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

I only used these three commands

unity --reset-icons
unity --reset
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset

Afterwards, I was able to utilize "Ubuntu" instead of "Ubuntu 2D". I hope this helps.


I came across something similar and now it is all working.

---

