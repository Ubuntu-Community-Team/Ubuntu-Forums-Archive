---
title: "No Desktop Effects after upgrade to Intrepid"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kayvee on 2008-10-25
Yesterday I upgraded my desktop computer from Hardy to Intrepid (Release Candidate). Everything went fine except for Desktop Effects. After upgrade + reboot, a dialog box popped up asking me if I am interested in using nVidia drivers for my graphics card. I picked the 'nVidia 96' driver and asked it to install and Activate it. It never did so. And now, when I go to Appearance > Visual Effects, it refuses to activate them. I go to Hardware Drivers and it says that no hardware on my computer needs restricted drivers. Visual Effects used to work fine in Hardy.

---

### Post by jespdj on 2008-10-25
The [release notes for 8.10](http://www.ubuntu.com/getubuntu/releasenotes/810) say the following:
> **nVidia "legacy" video support**

The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.

Users of other nVidia chipsets that are supported by the 173 or 177 driver series will be transitioned to the nvidia-glx-173 or nvidia-glx-177 package instead. However, unlike drivers 96 and 71, drivers 173 and 177 are only compatible with CPUs that support SSE (e.g. Intel Pentium III, AMD Athlon XP or higher). Systems with older CPUs will also be transitioned to the nv driver on upgrade.
So, if your nVidia video cards only works with the 96 driver, then it is too old for Ubuntu 8.10 to support 3D acceleration.

---

### Post by kayvee on 2008-10-25
Thats a bummer. So, there is no way I can ever get desktop effects on my computer unless I either downgrade to Hardy or upgrade my graphics card? Or is this something that would eventually be fixed?

I hope it will be fixed. I just realized that I cannot run a program called pymol which is very important for my work :-( In fact, I cannot even run glxgears. Is there something I am missing here?

---

### Post by simonjp on 2008-10-25
> **jespdj said:**
> The [release notes for 8.10](http://www.ubuntu.com/getubuntu/releasenotes/810) say the following:

So, if your nVidia video cards only works with the 96 driver, then it is too old for Ubuntu 8.10 to support 3D acceleration.

That's odd, because I seem to be experiencing the same problem as kayvee except I have a nvidia 6000 series on board card (6150) and an Athlon XP, so shouldn't be experiencing this problem.

See my post [here in this thread.]("http://ubuntuforums.org/showpost.php?p=6007472&postcount=11")  Would you have any ideas on this?

> **kayvee said:**
> Thats a bummer. So, there is no way I can ever get desktop effects on my computer unless I either downgrade to Hardy or upgrade my graphics card? Or is this something that would eventually be fixed?

I also hope it's fixed as well....

---

### Post by FuturePilot on 2008-10-25
It will be fixed at some point
[http://www.nvnews.net/vbulletin/showthread.php?t=116555]("http://www.nvnews.net/vbulletin/showthread.php?t=116555")

> While I can't promise that it'll be released before Ubuntu 8.10 comes out, we are working on it.

---

### Post by DJ_Peng on 2008-10-26
I ran into that as well (and I can't believe we reached RC status on Intrepid with that big honkin' bug still unsquashed) but I was able to get some compositing with xcompmgr. [This thread]("http://ubuntuforums.org/showthread.php?t=75527") will help you get it all set up.

---

### Post by kayvee on 2008-10-26
> **FuturePilot said:**
> It will be fixed at some point
[http://www.nvnews.net/vbulletin/showthread.php?t=116555]("http://www.nvnews.net/vbulletin/showthread.php?t=116555")

Reading the whole thread, that statement is the only hope there - rest of it casts an ominous shadow over the prospects of us ever getting legacy drivers...

Is there any other way to get 3D acceleration? I ask that because I use a particular program called pymol that stopped working now. It spits out this message when I start the program from command line. 
```
/var/lib/python-support/python2.5/pymol/api.py:374: Warning: 'as' will become a reserved keyword in Python 2.6
freeglut (pymol): failed to open display ''
 PyMOL: abrupt program termination.

```

Is this something related to nVidia drivers problem? Or can this be fixed without waiting for legacy drivers?

---

### Post by Daeluin on 2008-10-26
well I have a 6600gt and am not using legacy drivers, and have the same problem. or a very similar one. the driver appears to be activated, and lsmod | grep nv shows the nvidia module loaded. but glxinfo segfaults and xorg borks on any config except the new 7.4 generic autoconfig, which uses the nv module.

see here [http://ubuntuforums.org/showthread.php?t=877724](http://ubuntuforums.org/showthread.php?t=877724)

---

### Post by dark_phantom on 2008-10-26
> **jespdj said:**
> The [release notes for 8.10](http://www.ubuntu.com/getubuntu/releasenotes/810) say the following:

So, if your nVidia video cards only works with the 96 driver, then it is too old for Ubuntu 8.10 to support 3D acceleration.

I have this problem as well, but it broke more than just 3D acceleration.  I can't even get the remote desktop viewer to show up, keeps getting a libGL.so.1 error.

---

### Post by kayvee on 2008-10-27
Is there one single place (or a few) that I can keep checking on daily basis to see if there is a solution for this problem?

---

### Post by DJ_Peng on 2008-10-28
I suspect subscribing to a bug (both at Launchpad and possibly an upstream bug) could get you notified of action on it, but otherwise I've signed up for the intrepid-changes maillist. This way I'll get notified when new packages are accepted, although the traffic on it may be petering out with less than a handful of days to Intrepid's release. I also subscribed to the topic on the nvnews forum so when an update is posted I'll get it as well. If someone has a better way to keep track of it I'd love to know about it.

---

### Post by kayvee on 2008-10-30
Intrepid will be released today. Does anyone know if this issue with nVidia drivers is fixed in the final release?

---

### Post by Elfy on 2008-10-30
It's not an intrepid issue - it's the lack of driver from nvidia.

There has been a beta released for legacy cards
[http://ubuntuforums.org/showthread.php?t=963358](http://ubuntuforums.org/showthread.php?t=963358)

---

### Post by kayvee on 2008-10-30
Thanks for the link to that thread. Did that work for you? You sounded as if it did not work. 
I am not interested in desktop effects as much as I am in getting 3D acceleration. I use a program called pymol that seems to need 3D acceleration. After upgrade to Intrepid pymol does not start - it crashes with an error:
```
freeglut (pymol): OpenGL GLX extension not supported by display ':0.0'
```

---

