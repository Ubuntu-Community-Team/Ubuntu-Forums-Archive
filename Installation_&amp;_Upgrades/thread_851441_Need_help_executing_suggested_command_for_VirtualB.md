---
title: "Need help executing suggested command for VirtualBox"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by HamaLee on 2008-07-06
I'm getting an error when I run my virtual machine (VirtualBox, just upgraded to Hardy).  I've searched around a bit and the suggestion the error gives me seems to solve the problem, however I--being fairly illiterate--don't know how to DO what the error box tells me.  

Here's the error message: 

> VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


Can anyone direct me to a walk-thru of how to "execute 'blahblahblah' as root"?

Much thanks in advance, from Linux-virgin non-programmer just-wants-my-dang-Sigmaplot-loaded user.  Been running Ubuntu since January, love it overall!

---

### Post by sdennie on 2008-07-06
Try running:

```

sudo /etc/init.d/vboxdrv setup

```

---

### Post by HamaLee on 2008-07-06
Ding ding ding!  Worked no problems, I should've Wiki'd "sudo" WEEKS ago!

Thanks a bunch.  Now I can do my work at home---wait! Crap. That was a bad idea. ;-)

---

### Post by sdennie on 2008-07-06
Actually, xkcd is a better reference for sudo than wikipedia: [http://xkcd.com/149/](http://xkcd.com/149/)

---

