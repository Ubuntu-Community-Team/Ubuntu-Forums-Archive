---
title: "NVidia 177.80 final has been released"
date: 2008-10-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xebian on 2008-10-07
NV 177.80 has been released and it's working fine for me with kernel 27-6 64-bit.:guitar:

---

### Post by fjf on 2008-10-07
Is there a link and a howto somewhere?

---

### Post by plun on 2008-10-07
I strongly advice all users to wait for a Ubuntu release

Exception is also partly approved

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/275098](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/275098)

It causes just a mess with a manual installed driver,  we must also find
remaining bugs with driver management !

---

### Post by xebian on 2008-10-07
Here is the link

[http://www.nvidia.com/object/linux_display_ia32_177.80.html](http://www.nvidia.com/object/linux_display_ia32_177.80.html)

This is very helpful for us KDE4 users.

---

### Post by blakamin on 2008-10-07
> **xebian said:**
> Here is the link

[http://www.nvidia.com/object/linux_display_ia32_177.80.html](http://www.nvidia.com/object/linux_display_ia32_177.80.html)



Link now 404:confused:

---

### Post by jfernyhough on 2008-10-07
Just wait - it's being packaged as we speak.

Plus the link does work.

---

### Post by dalonso on 2008-10-07
Anybody with nvidia HDMI output can confirm if it shows now in alsa -L or should we still wait to kernel 2.6.28?

---

### Post by blakamin on 2008-10-07
> **jfernyhough said:**
> Just wait - it's being packaged as we speak.

Plus the link does work.
I'm still getting a 404 on 5 separate computers using 2 different ISP's

:confused:

---

### Post by Asraniel on 2008-10-07
works for me

---

### Post by forumache on 2008-10-07
Patience is a virtue!

Go to sleep. Wake up tomorrow, check daily updates, it might be there.

Have a safe dream ;)

---

### Post by Half-Left on 2008-10-07
Pretty sure you dont need all of them lines in your xorg.conf now because without them it dont make a speed difference, just running nvidia-settings -a InitialPixmapPlacement=2 does.

So you can take all that junk out your xorg.conf and try it, either that or they have enabled them by default.

---

### Post by dagrump on 2008-10-07
Does the line that claims-fixed problem (nasty bug) IRQs being disabled on some multi GPU SMP configurations. Does this mean my sli nvidia cards might work? I see where they are recognized early in the xorg log but it errors out at the end w/ no device found. 
I've tried every angle I could think of, installed 8.04.1 they worked fine. Reinstalled 8.10 w/o nvidia drivers works, well at least there is a gui. I would like get them working, at least not have to remove one of them.

---

### Post by norwoods on 2008-10-07
will a backport to hardy heron lts be available soon?

---

### Post by xebian on 2008-10-08
> **norwoods said:**
> will a backport to hardy heron lts be available soon?

The pkg direct from NVidia is working very nicely for hardy.  No frills plain vanilla built in card GEforce 6150.

---

### Post by dlm4849 on 2008-10-08
A somewhat related question - will EnvyNG recognize that a new driver has been released and update, or will we (hardy users) have to install a different way?

Thanks

---

### Post by gtdaqua on 2008-10-08
Download the package and do a chmod +x. Get the linux-headers-`uname -r` and build-essential packages. Run the downloaded package. As simple as that for a built-in 6150 LE. Is it complicated for others?

However, 2.6.27-5 and -6 doesnt load on my PC. .27-4 and .27-3 works.

---

### Post by norwoods on 2008-10-09
> **gtdaqua said:**
> Download the package and do a chmod +x. Get the linux-headers-`uname -r` and build-essential packages. Run the downloaded package. As simple as that for a built-in 6150 LE. Is it complicated for others?

However, 2.6.27-5 and -6 doesnt load on my PC. .27-4 and .27-3 works.

the problem is when the kernel is updated.  if the nvidia driver is packaged, updates will update the kernel and the driver to match.  if the nvidia driver is not packaged, an update to the kernel leaves a stale nvidia driver.

---

### Post by rarendes on 2008-10-10
> **norwoods said:**
> the problem is when the kernel is updated.  if the nvidia driver is packaged, updates will update the kernel and the driver to match.  if the nvidia driver is not packaged, an update to the kernel leaves a stale nvidia driver.

Exactly. So, is there a way to upgrade with the blessing of Ubuntus Repository?

I'm using Hardy x64, and checked hardy-proposed and hardy-backports, but the current driver delivered through these channels is still 

```
roland@pdbxe100:~$ dpkg -l | grep nvidia
ii  nvidia-glx-new                             169.12+2.6.24.14-21.50                   NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common                       20051028+1ubuntu8                        NVIDIA binary kernel module common files
ii  nvidia-settings                            1.0+20080304-0ubuntu1.1                  Tool of configuring the NVIDIA graphics driv
```

---

### Post by ajackson on 2008-10-10
> **rarendes said:**
> Exactly. So, is there a way to upgrade with the blessing of Ubuntus Repository?

I'm using Hardy x64, and checked hardy-proposed and hardy-backports, but the current driver delivered through these channels is still 

Use EnvyNG, I think it's in the main repository. The guy who codes that does update the driver on a regular basis and as his website says what happens with Envy indirectly helps jockey as well.

---

### Post by drs305 on 2008-10-10
Posted to the wrong thread, but I guess while I'm here, EnvyNG is in the universe repo.

---

### Post by fluffman86 on 2008-10-10
This new driver almost totally breaks X for me.  It's actually WORSE than using VESA.

I did a fresh install of Intrepid alpha 6 and got my nvidia-settings back the way I like them: a 1280x1024 monitor on the left and a 2000x1500 (roughly) CRT on the right using TwinView to expand my monitor.  Turns out it's running 177.7x nvidia with kernel 2.6.27-3.  

The minute I upgrade to the beta, I get the latest 2.6.27-5 or -6 kernel, with 177.8 nvidia driver and I'm stuck with mirroring screens at 800x600 or less.  After a lot of piddling with nvidia-settings (and with xorg.conf not accepting my old working xorg.conf file from hardy...GRR!!!), I can finally get my CRT working almost right, but my LCD will not upgrade.  Whatever happened to displayconfig-gtk (?)...that tool was awesome.  

Anyone know why nvidia-settings will not properly detect my monitor?  It actually lists some weird 1300xsomething widescreen (?) resolution, but not a standard 1280x1024.  I'd really like to upgrade to Intrepid but this is a total deal breaker right now.

Also, while I'm at it...here's a screenshot of my desktop:
[http://www.weekendmeltdown.com/fluffman/halp.png](http://www.weekendmeltdown.com/fluffman/halp.png)

Notice that my screen is actually a meta-mode that is as tall as my large CRT.  The problem is that my mouse will go off the top of my left screen, as evidenced by the update manager...but I can't see anything directly over the menu bar.  I'm learning to live with it, but it can be annoying.  Is there a way to extend my screen and still trap my mouse within the actual viewable area?  

Thanks.

---

### Post by alej on 2008-10-11
> **dalonso said:**
> Anybody with nvidia HDMI output can confirm if it shows now in alsa -L or should we still wait to kernel 2.6.28?

I've been waiting exactly for that for a while now.... 

It seems it should,.... althought I haven't yet properly tried it..... 

To make things clear for everybody. HDMI Video output has been working for a while with NVIDIA.. yet the problem was that there was no audio .... it does seem it will now....

```

alejandro@alekubuntu:~$ aplay -L
front:CARD=NVidia,DEV=0
    HDA NVidia, CONEXANT Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, CONEXANT Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, CONEXANT Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, CONEXANT Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, CONEXANT Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, CONEXANT Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=NVidia,DEV=0
    HDA NVidia
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

I'll let you know how it goes for me...

hp dv9343eu laptop... NVIDIA GeForce Go 7600

---

### Post by 73ckn797 on 2008-10-11
> **xebian said:**
> NV 177.80 has been released and it's working fine for me with kernel 27-6 64-bit.:guitar:

Intrepid installed and Nvidia drivers working out of the box on GeForce 7900GS video card.

Operating System: Linux-x86
NVIDIA Driver Version: 169.12

---

