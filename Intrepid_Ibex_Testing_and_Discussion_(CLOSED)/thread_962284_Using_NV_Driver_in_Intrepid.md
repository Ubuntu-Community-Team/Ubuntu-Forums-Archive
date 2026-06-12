---
title: "Using NV Driver in Intrepid"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Jæd on 2008-10-29
Hi,

I have a machine which needs to use the legacy nvidia driver. I've read that Nivida hasn't released this yet (if it ever will...). What are the options I can use under Intrepid...? How/can I install the open-source nv driver. I can't find it in apt...

Thanks...!

J

---

### Post by reg-sux on 2008-10-29
I misunderstood your question.

---

### Post by reg-sux on 2008-10-29
What you are searching for is [nouveau]("http://nouveau.freedesktop.org/wiki/FrontPage") I believe.

You can search this forum for threads about it. I don't think there's a package for it.

---

### Post by Aearenda on 2008-10-29
The change to the nv driver will be automatic on upgrade - see the release notes at [http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

You can use the nouveau driver to improve the situation a bit if you need features nv doesn't provide: [http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages)

For me, nouveau isn't fast enough yet, and nv doesn't do external monitors, so I'm sticking with Hardy for the present :-(

---

### Post by Jæd on 2008-10-29
> **Aearenda said:**
> The change to the nv driver will be automatic on upgrade - see the release notes at [http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)


If I've already upgraded to Intrepid, how can I download this separately...?

> **Aearenda said:**
> You can use the nouveau driver to improve the situation a bit if you need features nv doesn't provide: [http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages)

For me, nouveau isn't fast enough yet, and nv doesn't do external monitors, so I'm sticking with Hardy for the present :-(

I will look into this...

Thanks for the reply, btw...! :D

---

### Post by Aearenda on 2008-10-29
The nv driver is a standard part of Ubuntu - you should never need to download it seperately unless something has gone very wrong. To check it is there, look for xserver-xorg-video-nv in Synaptic. It is what is used automatically if you don't have the proprietary nvidia driver installed, and you have nvidia hardware. If you are running Intrepid, and you can log in in the normal way, then that's what is being used unless you change it (actually this is true of all fresh installations of Ubuntu, no matter what version). 
If you can't login except to a terminal, or if you are repeatedly taken into a very low-resolution graphics mode, then tell us so and we can help fix it.

---

### Post by Jæd on 2008-10-30
> **Aearenda said:**
> The nv driver is a standard part of Ubuntu - you should never need to download it seperately unless something has gone very wrong. To check it is there, look for xserver-xorg-video-nv in Synaptic. It is what is used automatically if you don't have the proprietary nvidia driver installed, and you have nvidia hardware. If you are running Intrepid, and you can log in in the normal way, then that's what is being used unless you change it (actually this is true of all fresh installations of Ubuntu, no matter what version). 
If you can't login except to a terminal, or if you are repeatedly taken into a very low-resolution graphics mode, then tell us so and we can help fix it.

Ah, thanks for clearing this up. I downloaded and installed the Nouveau driver and this seems to work slightly better.

Thanks for the help...! :D

---

### Post by laxon on 2008-10-30
Anyone knows, if I can use two screens with the nv-driver? Under Hardy I managed to get a 19 inch and a 22 inch screen to work (desktop over to screens) with the original nvidia-driver.

Thanks for the answers!
Alex

---

### Post by Jæd on 2008-10-30
Just seen :

Beta **71.86.07** [http://www.nvnews.net/vbulletin/showthread.php?t=122140](http://www.nvnews.net/vbulletin/showthread.php?t=122140) 
Beta **96.43.09 ** driver  [http://www.nvnews.net/vbulletin/showthread.php?t=122139](http://www.nvnews.net/vbulletin/showthread.php?t=122139)

---

