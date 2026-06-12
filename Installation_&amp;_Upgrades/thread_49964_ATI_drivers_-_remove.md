---
title: "ATI drivers - remove??"
date: 2005-07-18
forum: Installation &amp; Upgrades
---

### Post by immoral giant on 2005-07-18
Is it possible to remove the ATI drivers.

I'm having problems.  I installed the Mesa drivers initially.  Since then i followed [this](http://ubuntuforums.org/showthread.php?t=24557)  guide and got the ATI drivers.  With the ATI Drivers i got high fps in glxgears (cant remember what it was) but since then i followed this .[Here]("http://ubuntuforums.org/showthread.php?t=32495")

Now fglrxinfo gives:

```
root@ubuntu:/home/user # fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

``` 

Is there any way i can just uninstall the drivers and redo the guide?  I tried redoing it but it doesn't change.

---

### Post by mad_scientist03 on 2005-07-19
You could try removing the xorg-driver-fglrx package. You could also search around to find where the other video drivers have originated (in terms of which packages they belong to), and remove those. I would try a "sudo dpkg-reconfigure xserver-xorg" and see if you have any luck from there.

---

### Post by immoral giant on 2005-07-19
I did that reconfigured it, and i still get the same problem.

---

### Post by immoral giant on 2005-07-20
I uninstalled ubuntu and reinstalled it, and followed the guide and everything is working.

---

