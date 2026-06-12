---
title: "Calling For Testers - Rotation with xrandr"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gali98 on 2009-10-04
Sorry guys. This is totally my fault for not remembering. nVidia cards need a special option in the xorg.conf
This is not a bug. If you are having trouble rotating, see this post:
[http://ubuntuforums.org/showpost.php?p=8064085&postcount=24](http://ubuntuforums.org/showpost.php?p=8064085&postcount=24)
Thanks Rhubarb for fixing my mistake!


**********************************

I am calling for anyone and everyone to do a quick test.
xrandr seems to have a problem rotating some displays in karmic (one's that worked before. I want to compile some data to help the devs.
Relevant bug report here:
[https://bugs.launchpad.net/ubuntu/+source/x11-xserver-utils/+bug/442722](https://bugs.launchpad.net/ubuntu/+source/x11-xserver-utils/+bug/442722)

It does not involve installing any extra software.
I just need you to run one command.

Open up the terminal (must be in an X session i.e. not on a TTY like Ctrl+Alt+F*)
and run the command 
```
xrandr -o right
```
Then post here with:

Whether or not the rotation worked. (If it did simply run xrandr -o normal to fix it)

You graphics card (run sudo lshw -c video to find out) and what driver you are using. (i.e. open source/proprietary and nVidia/ATI/Intel/etc...)

Any output you get from the command (if it works right, there shouldn't actually be any output.)

And any other information you think might be relevant.
Thanks so much!
Kory

Edit: Also, if you don't mind, put the same information if yours fails in a comment in the bug report (link above.)
It might have a better chance of getting fixed if more people report the problem. Thanks!

---

### Post by zoomy942 on 2009-10-05
worked great here

```
zimmerman@Karmic-Tablet:~$ xrandr -o right
zimmerman@Karmic-Tablet:~$ xrandr -o normal
zimmerman@Karmic-Tablet:~$ sudo lshw -c video
[sudo] password for zimmerman: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:27 memory:e0400000-e04fffff memory:d0000000-dfffffff(prefetchable) ioport:2000(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:e0500000-e05fffff
zimmerman@Karmic-Tablet:~$ 


```

---

### Post by forumache on 2009-10-05
here worked too, nVidia 6200 with nVidia's drivers in Karmic (185)

---

### Post by NCLI on 2009-10-05
It works perfectly, and I get no output from running the command:

  ```
  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GME Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:98280000-982fffff ioport:60c0(size=8) memory:80000000-8fffffff(prefetchable) memory:98300000-9833ffff

```

---

### Post by mkis62 on 2009-10-05
worked ... no problems

---

### Post by meborc on 2009-10-05
well, didn't work for me :) > X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14

i think it might be my laptop resolution (1680x1050)

>   *-display               
       description: VGA compatible controller
       product: G84 [GeForce 8600M GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:e0000000-efffffff(prefetchable) memory:fa000000-fbffffff ioport:ef00(size=128) memory:fea00000-fea1ffff(prefetchable)

---

### Post by ricsi-pontaz on 2009-10-05
Didn't work for me.

```

ricsipontaz@ricsipontaz-desktop:~$ xrandr -o right
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14
ricsipontaz@ricsipontaz-desktop:~$ sudo lshw -c video
[sudo] password for ricsipontaz: 
  *-display               
       description: VGA compatible controller
       product: G92 [GeForce GTS 250]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:18 memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:fa000000-fbffffff ioport:e800(size=128) memory:febe0000-febfffff(prefetchable)
ricsipontaz@ricsipontaz-desktop:~$ 


```

---

### Post by yanns on 2009-10-05
It has half-worked.

I have 2 monitors, and, after xrandr -o right, I lost one of them.
xrandr -o normal did not give me the monitor back (still deactivated)

```
$ xrandr -o right
$ xrandr -o normal
$ sudo lshw -c video
  *-display:0             
       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:feb00000-feb7ffff ioport:e898(size=8) memory:e0000000-efffffff(prefetchable) memory:feac0000-feafffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:feb80000-febfffff

```

Intel drivers from [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu)

---

### Post by MacUntu on 2009-10-05
Nope but I don't know if it a. worked before and b. should work because I'm using the vesa driver (resolution currently 1024x768****).

```
13:18:51 test@box:~$ xrandr -o right --verbose
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 271mm x 203mm )  *76  
 1    800 x 600    ( 271mm x 203mm )   73  
 2    640 x 480    ( 271mm x 203mm )   73  
 3    640 x 400    ( 271mm x 203mm )   0   
 4    320 x 400    ( 271mm x 203mm )   0   
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none
Setting size to 0, rotation to right
Setting reflection on neither axis
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14
```
```
13:20:02 test@box:~$ sudo lshw -c video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: G73 [GeForce Go 7600]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d1000000-d1ffffff memory:b0000000-bfffffff(prefetchable) memory:d0000000-d0ffffff ioport:2000(size=128)
```

---

### Post by jperez on 2009-10-05
Worked perfectly for me on an Intel GM956/GL960 IGC for my laptop (res. 1280x900) on Karmic; no output displayed while running.

Jesse~

---

### Post by ronacc on 2009-10-05
failed here , nvidia 7600gs and repo 185.18.36 driver 

```
ron@ron-desktopb:~$ xrandr -o right
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  154 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14
ron@ron-desktopb:~$ 

```

---

### Post by dino99 on 2009-10-05
oem@oem-desktop:~$ xrandr -o right
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14
oem@oem-desktop:~$  xrandr -o normal
oem@oem-desktop:~$ sudo lshw -c video
[sudo] password for oem: 
  *-display               
       description: VGA compatible controller
       product: G86 [GeForce 8500 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:fa000000-fbffffff ioport:cc00(size=128) memory:feae0000-feafffff(prefetchable)

---

### Post by Colonel Kilkenny on 2009-10-05
> **ronacc said:**
> failed here , nvidia 7600gs and repo 185.18.36 driver 

```
ron@ron-desktopb:~$ xrandr -o right
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  154 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14
ron@ron-desktopb:~$ 

```

Exactly same Nvidia card and result here.

---

### Post by philinux on 2009-10-05
Busted here.

xrandr -o right
```

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14

```

---

### Post by Basicalyptic on 2009-10-05
No worky for me:

> $ xrandr -o right
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14

$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: G86 [GeForce 8500 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:fa000000-fbffffff ioport:bc00(size=128) memory:fe9e0000-fe9fffff(prefetchable)


Proprietary nVidia drivers, version 185

---

### Post by MALEADt on 2009-10-05
Works in here, OSS ati driver (R700 card)
```
tim@firefly:~$ sudo lshw -c video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff(prefetchable) ioport:2000(size=256) memory:cfef0000-cfefffff memory:cfe00000-cfe1ffff(prefetchable)

```

---

### Post by tom56 on 2009-10-05
Failed here

```
tom@tom-desktop:~$ xrandr -o right
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14
tom@tom-desktop:~$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: ION VGA
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: b1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:22 memory:fb000000-fbffffff memory:e0000000-efffffff(prefetchable) memory:f8000000-f9ffffff(prefetchable) ioport:ec00(size=128) memory:fafe0000-faffffff(prefetchable)
tom@tom-desktop:~$
```

GeForce 9400M, 1680x1050 resolution, nvidia-glx-185 185.18.36-0ubuntu3

---

### Post by gali98 on 2009-10-05
Thanks everyone! I added your data to the bug report!
Also, if you don't mind, put the same information if yours fails in a comment in the bug report (link above.)
It might have a better chance of getting fixed if more people report the problem. Thanks!
Kory

---

### Post by Tich666 on 2009-10-05
worked fine for me, although it did disable the LVDS output and only rotated the DVI one.

```
$sudo lshw -c video
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:29 memory:f8000000-f83fffff memory:d0000000-dfffffff(prefe
```
```
$xrandr
Screen 0: minimum 320 x 200, current 2960 x 1050, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+1680+0 (normal left inverted right x axis y axis) 287mm
DVI1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm

```

---

### Post by gali98 on 2009-10-05
So far the pattern I have seen is that the only one's failing are nVidia. (Though if it never worked before, It obviously wouldn't work now.)
Kory

---

### Post by gali98 on 2009-10-06
*Bump*

Anyone else want to give me your report? The more reports the better.
Kory

---

### Post by Lazy123 on 2009-10-06
```

~$ xrandr -o right
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14

```
```

~$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: G92 [GeForce 8800 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:e2000000-e2ffffff memory:d0000000-dfffffff(prefetchable) memory:e0000000-e1ffffff ioport:3000(size=128)

```

The driver is nvidia-glx-185 (185.18.36-0ubuntu3) and the rotation obviously failed.

---

### Post by cantab on 2009-10-06
**I have no idea if it ever worked on a previous ubuntu distribution**
The monitor is connected to the nvidia card.

tw296@bevelle:~$ xrandr -o right
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  154 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14 
tw296@bevelle:~$ sudo lshw -c video
[sudo] password for tw296: 
  *-display               
       description: VGA compatible controller
       product: NV44A [GeForce 6200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list rom
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
       resources: irq:16 memory:fc000000-fcffffff memory:e0000000-efffffff(prefetchable) memory:fb000000-fbffffff memory:fd000000-fd01ffff(prefetchable)
  *-display UNCLAIMED
       description: VGA compatible controller
       product: MGA 1064SG [Mystique]
       vendor: Matrox Graphics, Inc.
       physical id: b
       bus info: pci@0000:02:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=64
       resources: memory:f7ff8000-f7ffbfff memory:f4000000-f47fffff(prefetchable) memory:f7000000-f77fffff memory:f4820000-f482ffff(prefetchable)
tw296@bevelle:~$

---

### Post by Rhubarb on 2009-10-06
Good news nvidia users!

While **xrandr -o right** didn't work initially for my nvidia 7950 graphics card (running nvidia version 173.14.20), I did remember a way to get it playing nicely with xrandr that I'd experimented with a few years back.

This solution will work in Karmic (x64 Karmic beta which is what I'm using currently) and for that manner many previous versions of Ubuntu and many versions of the nvidia proprietary driver as well:-

First edit your xorg.conf and add in an extra line:
```
gksu gedit /etc/X11/xorg.conf
```

So it should look something like this:
```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"true"
	Option	"RandRRotation"	"true"
EndSection
```

Notice the **Option	"RandRRotation"	"true"** line.
Now simply log off, then log back in again, and when you run
**xrandr -o right** everything will work nicely as it should :)

-----

Now for my results:
Obviously it didn't work initially until I had modified my xorg.conf file.
And now it works very nicely with the proprietary nvidia driver enabled! :D

```
$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: G71 [GeForce 7950 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fa000000-faffffff memory:d0000000-dfffffff(prefetchable) memory:fb000000-fbffffff ioport:df00(size=128) memory:fc000000-fc01ffff(prefetchable)
```

---

### Post by schmolch on 2009-10-06
Works fine on 2 Tablet-PCs with Intel-GMA-950.
Does not work on NVIDIA-Desktop (didn't expect it to)

---

### Post by FormerSlacker on 2009-10-06
Works fine over here with the proprietary ATI drivers in Karmic. (**fglrx 8.66.10**)

Ati HD3650

```
       description: VGA compatible controller
       product: Mobility Radeon HD 3600 Series
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:29 memory:d0000000-dfffffff(prefetchable) memory:efde0000-efdeffff ioport:ef00(size=256) memory:efd00000-efd1ffff(prefetchable)

```

---

### Post by gali98 on 2009-10-07
Oh goodness.... I am dumb.... I forgot about the line you had to add to the xorg.conf...

Thanks Rhubarb!
I will make sure and test it tonight before I clear the bug just to make sure, but I am sure that's what it is. I totally forgot about it.
sigh... Thanks guys
Kory

---

### Post by dino99 on 2009-10-07
work fine with:

oem@Mubuntu:~$ sudo lshw -c video
[sudo] password for oem: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon RV250 [Mobility FireGL 9000]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
       configuration: latency=66 mingnt=8

---

### Post by gali98 on 2009-10-07
No need for anyone else to post. Rhubarb found my problem.
Read the first post again.
Kory

---

### Post by executorvs on 2009-10-08
works from disc on friend's hp tx2500us. however, when she rotates the screen on her tablet under karmic her stylus calibration seems to be inverted and no longer usable. any ideas on what's going on here or how to fix it? my google fu seems weak today as I couldn't find any bug reports clearly stating this issue.

---

### Post by Favux on 2009-10-08
Hi executorvs,

Sounds like, if she's using a rotation script, the xsetwacom commands aren't working.  Or you're using the xrandr command or something similar without xsetwacom commands.  So stylus etc. isn't rotating with the screen.  The xsetwacom problem is described in Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?p=6546012#post6546012](http://ubuntuforums.org/showthread.php?p=6546012#post6546012)  For her TX2500 in Karmic she probably needs the modified wacom.fdi in gali98's HOW TO in post #104  here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)

Then for rotation methods see the Rotation HOW TO:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)

---

### Post by executorvs on 2009-10-08
she says her rotate button didn't work so she used the display console under preferences to rotate right.

---

### Post by gali98 on 2009-10-08
You beat me to it Favux! :)
The rotate button doesn't work under ubuntu. But definately check out that rotation howto favux posted. It's really great!
Kory

---

