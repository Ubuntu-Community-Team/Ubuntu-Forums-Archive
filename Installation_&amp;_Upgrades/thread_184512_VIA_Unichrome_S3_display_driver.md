---
title: "VIA Unichrome S3 display driver"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by astriskmanish on 2006-05-30
Hi, there just want to know that in the next relese of UBUNTU which is Ubuntu 6.06 Dapper Drake the display driver of  "VIA Unichrome S3 display driver" is suppoted or not b'coz its not there in the previous release which is Ubuntu 5.10 ("Breezy Badger") due to that the video clearity n also video motion is not upto the mark..:(

---

### Post by dyehue on 2006-05-30
[QUOTE=astriskmanish]Hi, there just want to know that in the next relese of UBUNTU which is Ubuntu 6.06 Dapper Drake the display driver of  "VIA Unichrome S3 display driver" is suppoted or not b'coz its not there in the previous release which is Ubuntu 5.10 ("Breezy Badger") due to that the video clearity n also video motion is not upto the mark..:([/QUOTE]

Works like a charm here (Via Unichrome KM400, Biostar m7viz mainboard).

---

### Post by AlexMR on 2006-05-30
Hello astriskmanish,

unfortunately, there are still some chipsets that aren´t supported yet. No love for my VIA VN800 Unichrome Pro IGP, for example.

But lots of other Unichrome stuff seems to work now with Dapper.

Greetings,
Alex.

---

### Post by Beej on 2006-05-30
Unichrome CLE266 chipset on my Mini ITX mobo Dri and XvMC are enabled out of the box. 


It is worth remembering that if you want hardware accelerated video on these chipsets, you will need to either run Xine with the xxmc driver (works great for me) or patch the cvs version of mplayer with the patch on the openchrome website and compile with the --enable-xvmc --with-xvmclib=viaXvMC flags (which I have been completely unable to get working)

---

### Post by pirast on 2006-05-30
Hi,
I created a precompiled Ubuntu Dapper package of Openchrome, which supports 

CLE266, KN400, KM400, K8M800, PM800, CN400, VN800

It can be found on [http://gamesplace.info/opensource/openchrome/dapper-binaries/](http://gamesplace.info/opensource/openchrome/dapper-binaries/)

Regarding VN800, there are still some bugs, but that should be fixed soon.

Martin

---

### Post by AlexMR on 2006-05-30
Hello pirast,

thank you very much for your package, it´s the first time I managed to use the via-module instead of vesa on my FSC Amilo Pro V2030 laptop. Although my fps in glxgears dropped from ~250 to ~140 compared to vesa...:???: 

Do you have a clue if it´s possible to activate direct rendering with it? The dri-module got loaded as well during bootup, but glxinfo shows no direct rendering.

Any help would be really appreciated.

Best regards and thanks again for my first via-experience :D 
Alex.

---

### Post by pirast on 2006-05-30
Hi,
I have exactly the same notebook and I hate it..

Here is the answer to your question:
You have to patch the dri cvs and compile the drm kernel module yourself:

cvs -z3 -d:pserver:anonymous@dri.freedesktop.org:/cvs/dri login
(password for anonymous is empty, just hit enter)
cvs -z3 -d:pserver:anonymous@dri.freedesktop.org:/cvs/dri co drm

#Install libdrm
cd drm/
./autogen.sh
make
sudo make install
#patch
wget http://washington.kelkoo.net/epia/patches/drm_via_p4vm800pro_pciids.patch
patch -p0 <drm_via_p4vm800pro_pciids.patch

#install kernel headers
sudo apt-get install linux-headers-arch
#(arch can be 386, 686, k7, mostly it is 386)

#Install kernel module
cd linux-core
make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via
sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/
sudo depmod -ae

From [http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code)

I get around 600-900 FPS. Please note that your system may be unstable when you do it because VN800 is not official supported by dri. This should change when the vn800 code is imported in the official via xorg branch. Maybe I will created some kernel module debs, it depends on demand.

Except Xv to be working soon, too - I am currently investigating in the problem with the openchrome developer.

---

### Post by AlexMR on 2006-05-30
Hi pirast,

yeah, it´s a lovely piece of hardware...:rolleyes: 

Anyway, thanks for the HOW-TO, I´ll give it a try. Worst case would be a fallback to vesa - so what ?

Greetings,
Alex.

---

### Post by pirast on 2006-05-30
I forgot to say one thing:
the cvs server seems to be offline, youll have to wait till it is online again

working fan controlling for amilo pro v2030 is coming, too :)

---

### Post by ahaslam on 2006-05-30
[QUOTE=pirast]Hi,
I created a precompiled Ubuntu Dapper package of Openchrome, which supports 

CLE266, KN400, KM400, K8M800, PM800, CN400, VN800

It can be found on [http://gamesplace.info/opensource/openchrome/dapper-binaries/](http://gamesplace.info/opensource/openchrome/dapper-binaries/)

Regarding VN800, there are still some bugs, but that should be fixed soon.

Martin[/QUOTE]

Hi, I have a K8M800 Unichrome Pro. I'd tried EVERYTHING to get it to work in breezy with no success. I'm now testing Dapper and all I did to make it work was edit xorg.conf as follows:

Section "Device"
Identifier "VIA Unichrome Pro"
Driver "via"
BusID "PCI:1:0:0"
Option "EnableAGPDMA"
Option "DisableIRQ"
EndSection

Glxinfo reports that DRI is on. 
With a resoloution of 1024x768 and 24 bit colour, I consistantly get 410 FPS with glxgears.

My question to you is, would the 'openchrome' drivers improve performance, compatibility or stability?

For your info I have a laptop with an AMD 1.6GHz Sempron & 512 MB RAM.

Cheers,
Tony.

---

### Post by AirRaven on 2006-05-30
I've got my Unichrome IGP to work earlier- it's such a nice change from the vesa drivers.

Only problem is that the screen flickers white a lot whenever I try and play a video in Totem or any other movie player in fullscreen. It's quite annoying, but other than that, it works fantastically well.

---

### Post by pirast on 2006-05-30
Tony, I do not know if it improves the performances. But openChrome adds some new features to the via driver.

If you are happy, stay with the via Xorg driver. The reason why I use the openChrome one is that the via Xorg driver does not support my chipset.

---

### Post by deadlydeathcone on 2006-05-30
Thanks for the binaries! I've been wanting to try openchrome for a while but never took the time to jump through the hoops required to get it compiled.

From what I can remember at the moment the openchrome driver are pretty much the xorg drivers with a few experimental additions. There's rudimentary compositing support, the rendering quality should be improved, and it's supposedly about 10% slower because of it (my score in glxgears actually improved, however).

---

### Post by astriskmanish on 2006-05-30
[QUOTE=pirast]Hi,
I have exactly the same notebook and I hate it..

Here is the answer to your question:
You have to patch the dri cvs and compile the drm kernel module yourself:

cvs -z3 -d:pserver:anonymous@dri.freedesktop.org:/cvs/dri login
(password for anonymous is empty, just hit enter)
cvs -z3 -d:pserver:anonymous@dri.freedesktop.org:/cvs/dri co drm

#Install libdrm
cd drm/
cd libdrm
./autogen.sh
make
make install
#patch
cd ../
wget [http://washington.kelkoo.net/epia/patches/drm_via_p4vm800pro_pciids.patch](http://washington.kelkoo.net/epia/patches/drm_via_p4vm800pro_pciids.patch)
patch -p0 <drm_via_p4vm800pro_pciids.patch

#Install kernel module
cd linux-core
make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via
cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/
depmod -ae

From [http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code)

I get around 600-900 FPS. Please note that your system may be unstable when you do it because VN800 is not official supported by dri. This should change when the vn800 code is imported in the official via xorg branch. Maybe I will created some kernel module debs, it depends on demand.

Except Xv to be working soon, too - I am currently investigating in the problem with the openchrome developer.[/QUOTE]


hello SIR, 
i was using the solution u gave did exactly as u had guided me but after 
cd libdrm
when i issued the comand 
./autogen.sh
then i got the reply as
bash: ./autogen.sh: No such file or directory:confused: 
So can u help me what to do next??
plz...

---

### Post by pirast on 2006-05-31
i now fixed the instructions

---

### Post by AlexMR on 2006-05-31
Hello pirast,

after installing some more packages (autoconf, automake1.8/9, libguile-dev with a bunch of dependencies and libtool), everything seemed to have compiled and installed fine - no errors while doing your HOW-TO.

But still, glxinfo shows me that there´s no direct rendering and glxgears sticks to about 140 fps. Did I miss something ?

I´ve also entered the lines Anthony Haslam mentioned into xorg.conf - same result...

By the way, fan controlling would be great as well :-D . But 3D-acceleration would make my day even more.

Greetings,
Alex.

---

### Post by pirast on 2006-05-31
Alex, try to restart your system :) 

And if this does not help, please attach Xorg.0.log and the output of dmesg. I'll attach my xorg.conf.

Thanks

---

### Post by AlexMR on 2006-05-31
Hi Martin,

rebooting didn´t bring up other results. Hopefully the last lines of $dmesg and the attached files help.

[4294720.617000] [drm] Initialized drm 1.0.1 20051102
[4294720.624000] PCI: Unable to reserve mem region #1:4000000@f0000000 for device 0000:01:00.0
[4294720.624000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 225
[4294720.625000] PCI: Via IRQ fixup for 0000:01:00.0, from 10 to 1
[4294720.626000] [drm] Initialized via 2.9.1 20060111 on minor 0:
[4294720.626000] [drm] Used old pci detect: framebuffer loaded
[4294720.682000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[4294720.682000] agpgart: Device is in legacy mode, falling back to 2.x
[4294720.682000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294720.682000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode

Thank you for your support!

Alex.

---

### Post by pirast on 2006-05-31
Alex, could you please try to use my xorg.conf?

---

### Post by AlexMR on 2006-05-31
Martin, I used your xorg.conf, still no direct rendering...

Are you using the i386 or i686-kernel ? So far I´ve been using the i686, might that make a difference ?

---

### Post by pirast on 2006-05-31
It should not make a difference since you compiled the kernel yourself.

Could you give me the output of uname -r?

I will then compile a kernel module for you with the hope that it works then ;)

Can I  also have the log when using my xorg.conf so that I can diff the logs?

---

### Post by AlexMR on 2006-05-31
Of course, here we go :-D :

~$ uname -r
2.6.15-23-686

I guess what´s missing is that -39 thingy, so actually it´s 2.6.15-23.39-686 (most recent ubuntu-kernel).

And the Xorg.0.log using your xorg.conf has been attached.

---

### Post by pirast on 2006-05-31
Alex, please try to increase the frame buffer memory area in BIOS :)

Then please give me the output of glxinfo | grep rendering

---

### Post by AlexMR on 2006-05-31
I already tried that one out - increased it to the max. 64 MB - no difference.:-|

---

### Post by pirast on 2006-05-31
Mhm my xorg log is nearly exactly the same and I have direct rendering.

How do you try if direct rendering works?

What does glxinfo | grep rendering output?

---

### Post by AlexMR on 2006-05-31
~$ glxinfo | grep rendering
direct rendering: No

Did you also upgrade your laptop´s BIOS to the newer version of April 2006 ? Perhaps I should try to downgrade again if you didn´t (god, FSC sucks!)

---

### Post by msofer on 2006-05-31
AlexMR: the line
[INDENT][4294720.624000] PCI: Unable to reserve mem region #1:4000000@f0000000 for device 0000:01:00.0[/INDENT]
in your dmesg suggests a buggy bios (as I have in my averatec laptop). Try adding 
[INDENT]reserve=0xf0000000,0x4000000[/INDENT]
to your boot options, so that the kernel does not use that memory for something else.

I am not 100% sure that those are the correct values for those params: they suggest you have 4093640704 bytes of RAM, and that you are reserving the last 64MB for video. If that doesn't work, you may want to adapt and follow the instructions at [this thread]("http://averatecforums.com/showpost.php?p=14323&postcount=14").

ISTR that I saw more detailed instructions somewhere else - involving reserving any memory "holes" in the "BIOS provided physical RAM map", and not assuming that the video mem is at the end of the physical memory. But can't find it now. Please let me know if you need me to look better.

HTH

---

### Post by pirast on 2006-05-31
AlexMR: No, I did not.

---

### Post by pirast on 2006-05-31
Alex, the issue is not caused by the bios, for me it works fine after an update.

---

### Post by saepia on 2006-05-31
Howto works well, without any problems od Dapper (testing). My GNOME is faster but I see problems in Blender (it uses OpenGL to create interface).

---

### Post by AlexMR on 2006-05-31
Martin, after I downgraded to the previous BIOS-version I had to experience the same issue - so you´re right, it´s not BIOS-relevant :) 

Did you have to reserve some RAM as mentioned by msofer (thanks by the way!)? 

I´m kind of clueless, perhaps I messed up some files before I found your HOW-TO, as I wildly tried to install different drivers from different places, compiling stuff from viaarena etc. Try and error - and reinstall :-D 

That´s what I will do now. Thank you guys for your great help so far, I´ll be back 8) 

Alex

---

### Post by pirast on 2006-05-31
Hi Alex,
no, I didn't have to use msofer's workaround. My suggestion would be a reinstall, too.

Martin

---

### Post by AlexMR on 2006-06-01
Hello,

a reinstallation did the trick, glxinfo shows me direct rendering=yes and I get about 750 fps with glxgears. Which should be really great...

Lamentabley, the possibilty of a system freeze due to the new driver showed up quite badly. 3D-effects with digikam´s diashow were as slow as without dri, and starting my Arindal-Win-Client with WINE ended up with a total freeze (no console reachable, ctrl+alt+del with no effect).

So I´ll wait for some improvements for this driver...

Anyway, very special thanks to Martin (pirast) for this great HOW-TO and his patience and support, hopefully things will turn out better within the next few months...So far I´ll stick to vesa.

Best regards,
Alex.

---

### Post by BarFly on 2006-06-02
Hi!  Is there any word on an Unichrome S3 driver for K8T800/K8T900?  I am using a low-end machine but with plenty of RAM.  VESA just does not cut it.  Of course, I could buy a cheap graphics card, but I would prefer not to as I have perfectlly good (for my purposes) on-board graphics.

Yeah, I could do it myself if I had a clue how to.  Alas, all I want to do is watch video without Ubuntu freaking out whenever I try to fast forward, rewind, etc.  That and watching video without random crashes (that's actually much better since I switched to Dapper).

---

### Post by pirast on 2006-06-11
Precompiled kernel modules for 2.6.15-23-686 can be found at [http://gamesplace.info/opensource/openchrome/dapper-binaries/](http://gamesplace.info/opensource/openchrome/dapper-binaries/) (drm.ko, via.ko)

They have to be placed in /lib/modules/2.6.15-23-686/kernel/drivers/char/drm

After running sudo depmod -ae and a restart, 3d acceleration should work. Make sure that you changed the driver in your xorg.conf to via.

---

### Post by MihaiM on 2006-06-13
I have a Benq JoyBook R23E with VIA Unichrome Pro and the VIA module is buggy. I get artifacts, blank screen, etc. I am forced to use VESA.

I wanted 3D for Google Earth, because in software it's very slow.

---

### Post by UNHOLYwoo on 2006-06-24
Hey everyone,

I ran through the HOW TO, which was very helpful (thanks btw) and I still can't seem to get Direct Rendering to work. I am running an Averatec 3715-EH1 with 0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01) (according to lspci).

Heres my glxinfo:
> root@fragile:~# glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
root@fragile:~#

my Xorg.0.log (or at least what I thought was relevant):

> drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "via"
(II) VIA(0): [drm] drmOpen failed
(EE) VIA(0): [dri] DRIScreenInit failed.  Disabling DRI.

and my xorg.conf as far as the video goes:
> Section "Device"
        Identifier      "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Driver          "via"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
EndSection

I've been trying out a slew of other drivers and am fairly new to linux, and this is the one thing that has been hindering me since I started using ubuntu (a few months ago).

Any help at all would be ***greatly*** appreciated (vesa drivers are so aggravating). Thanks in advance.

---

### Post by msofer on 2006-06-24
Looks like your 'via' kernel module is not loading, for some reason. Without it, no accel video.
Please try from a command line
   sudo modprobe via
If that works, launching Xorg with the via driverright after that should work fine too. If it does, just insure that the via module is loaded at startup. 

If the via module does not load, maybe you should try a different one from the [unichrome project]("http://unichrome.sourceforge.net/").

---

### Post by UNHOLYwoo on 2006-06-25
You know, thinking about it now, I've tried a bunch of other stuff, Unichrome included, and im sure something along those lines got really messed up. I think I'm going to do a fresh install of dapper and then redo this HOWTO... stand by, I may need help.

---

### Post by acojlo on 2006-07-01
Hello, I see the binaries are for 686, but my kernel is 386 (I think this is standard for Dapper Drake). Can I use *.ko for my vn800? I beleive I may not because it have not worked.

---

### Post by acojlo on 2006-07-02
In my question was the answer :) I upgraded my kernel to 686. Here is link for how to on upgrade the kernel: [http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

---

### Post by crispy_420 on 2006-07-02
I'm getting about 430-490 fps in glxgears. Before editing my xorg I was getting about 150 fps.

This is on an Averatec 5400 series. 

Is this any good?

I already changed my Xorg to via as below:

> Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Driver		"via"
	BusID		"PCI:1:0:0"
	Option		"EnableAGPDMA"
	Option		"DisableIRQ"
EndSection

Anyway to get anymore out of this or am I at the end of the line?

---

### Post by crispy_420 on 2006-07-07
Nobody knows?

---

### Post by yigal.weinstein on 2006-07-12
you may want to check out this site: [www.averatecforums.com/](www.averatecforums.com/)
It helped me get a specific dsdt for my Averatec so that fan and temp. can be displayed and the fan modified.

---

### Post by pirast on 2006-07-14
> **acojlo said:**
> Hello, I see the binaries are for 686, but my kernel is 386 (I think this is standard for Dapper Drake). Can I use *.ko for my vn800? I beleive I may not because it have not worked.

No. But I just updated everything including updating the kernel modules for 2.6.15-26-386

Have a look at [http://gamesplace.info/opensource/openchrome/dapper-binaries/](http://gamesplace.info/opensource/openchrome/dapper-binaries/)

The README is updated, too.

---

### Post by AlexMR on 2006-07-16
Hello,

just to give some feedback - on my FSC Amilo Pro v2030 with that nasty VN800 chipset, direct rendering (although glxinfo says something different) is still not working with the actually provided via-package and the kernel modules for 2.6.15-26-386.

Supertux shows a totally disturbed picture, digikam´s 3D-effects are as slow as without direct rendering, and some WINE applications cause a total freeze of the system. I don´t know if you experience the same issues (especially with Supertux - someone tested it as well?), but the openchrome driver is still very buggy for this chipset - so try it with prudence !

Anyways I would like to say thanks again to pirast for the efforts he made on  trying to make 3D-acceleration work by providing those actual packages, but lamentably I can not recommend their usage at their current state of development.

Greetings,
Alex.

---

### Post by mindtrick on 2006-08-27
Hi, I have S3 Unichrome Pro K8. 

Is xgl impossible for me? 

I read about xgl and there were how to's only about ati and nvidia.

---

### Post by JKoder on 2006-08-28
Hi.
I have a Via video card chipset PM800 or PN800 dont kow for sure
My question is: can i activate S-VIDEO on it with this driver ?

Thanks for response 
Sebastian

---

### Post by kev000 on 2006-10-15
Any work being done to make binaries for ubuntu edgy?

---

### Post by CosminGC on 2006-10-31
I would be interesting too

---

### Post by davescafe on 2006-11-01
> **CosminGC said:**
> I would be interesting too

I, too, would be interested in an Edgy (6.10) compile. I am willing to help, but I don't know if I have the expertise. I will subscribe to this thread and follow it for any new developments.

Dave

---

### Post by pirast on 2006-12-16
I created a howto, located at [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome), which describes how to compile OpenChrome yourself.

---

### Post by CosminGC on 2006-12-16
> **pirast said:**
> I created a howto, located at [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome), which describes how to compile OpenChrome yourself.

does it work on edgy?

---

### Post by DaneDog on 2007-01-09
I'm running Ubuntu Edgy 6.10 and that walkthrough went fine for me but it doesn't seem to work *WELL* with opengl well i have a PM400 though.... so it's worth a shot...

---

### Post by jonobo on 2007-02-01
Hi - thanks for all the ideas and information, especially 2 pirast :D 

Unfortunately i'm still stuck on my display problems - here comes the data:

Machine: Fujitsu Siemens Amilo Pro V 2035, Intel Celeron M 370 1.5GHz, 768MB RAM, Graphic Via VN 800 Mobile, Ubuntu 6.10 Edgy Eft.

```
jobo@zbox:~$ uname -r
2.6.17-10-generic
```

On the first day i had a quite clean and fresh Ubuntu Edgy Eft 6.10 install.

On the second day i tried to get better graphic-performance because for example my firefox was scrolling slow as ... slow. I followed this Howto: 
[http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/]("http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/")
That worked out quite well, i compiled the official cx700 Linux XOrg Display driver kernel Source and modified my xorg.conf and the xserver was running fast - on a 640x480 or 800x600 resolution. I played around with Mode-Lines a bit, but it didn't help.

On the third day i decided it might be better to follow the ways of the ubuntu-open-chrome-howto on:
[https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")
I did everything line by line, everything is running fine, on a 800x600 resolution - but i need 1280x800 ;)

On the fourth day i am really confused :confused: 
1. Which driver is installed now ? Official-VIA or Openchrome ? How do i find out ?
2. Why does my "glxinfo" output like this:
```
jobo@zbox:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  128 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  18
  Current serial number in output stream:  19
jobo@zbox:~$ 
```
2.1 *update* "glxinfo | grep render" now looks fine:
```
jobo@zbox:~$ glxinfo | grep render
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```


3. Why does my "glxgears" not stop, nor show any numbers, statistics, fps ?
3.1. Okay, found out how to get glxgears giving me output - now it is starting, 3 wheels are rotating normally, after a short time they stop continuous motion and only move from time to time - output like this:
```
jobo@zbox:~$ glxgears -printfps
1026 frames in 5.6 seconds = 184.060 FPS
1026 frames in 5.1 seconds = 201.348 FPS
1140 frames in 5.6 seconds = 204.729 FPS
1140 frames in 5.6 seconds = 205.171 FPS
1140 frames in 5.6 seconds = 205.174 FPS
1026 frames in 5.2 seconds = 197.531 FPS
1026 frames in 5.1 seconds = 201.152 FPS
```
4. Why is my Firefox, Video and all running well, but only on 800x600 ?

Whoo-hoooo -_- before i'm writing a book i stop at this point and give you all the data i got on my problem:

My xorg.conf:

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load  	"glx"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load  	"synaptics" 
EndSection


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option 		"TouchpadOff" "1" 	# touchpad ganz ausschalten, siehe man synaptics
EndSection


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "Device"
	Identifier		"Generic Video Card"
	Driver 		"via"
	VendorName  "VIA Tech"
	BoardName   "via"	
	BusID		"PCI:1:0:0"
	Option 		"EnableAGPDMA"
	Option 		"DisableIRQ"
EndSection


Section "Monitor"
	Identifier		"Generic Monitor"
	Option		"DPMS"
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24

	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Section "DRI"
	Mode 0666
EndSection
```

my xorg.0.log 
```
is attached, as it was way too long
```


and here some bonus-info:
```
jobo@zbox:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0c.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)
```

and some extra-info:
```
jobo@zbox:~$ lsmod
Module                  Size  Used by
via                    48224  0 
drm                    74644  1 via
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
ppp_generic            30612  0 
slhc                    8448  1 ppp_generic
nls_iso8859_1           5248  1 
nls_cp437               6912  1 
vfat                   14720  1 
fat                    56348  1 vfat
ipv6                  272288  15 
af_packet              24584  2 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
joydev                 11200  0 
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tsdev                   9152  0 
sg                     37404  0 
usbhid                 45152  0 
snd_via82xx            30360  2 
via_rhine              26116  0 
mii                     6912  1 via_rhine
pcmcia                 40380  0 
evdev                  11392  2 
bcm43xx               127252  0 
gameport               17160  1 snd_via82xx
psmouse                41352  0 
serio_raw               8452  0 
pcspkr                  4352  0 
snd_via82xx_modem      16648  1 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  3 snd_pcm_oss
snd_ac97_codec         97696  2 snd_via82xx,snd_via82xx_modem
snd_ac97_bus            3456  1 snd_ac97_codec
i2c_viapro              9876  0 
snd_mpu401_uart        10240  1 snd_via82xx
ieee80211softmac       33792  1 bcm43xx
snd_pcm                84612  4 snd_via82xx,snd_via82xx_modem,snd_pcm_oss,snd_ac97_codec
snd_timer              25348  2 snd_seq,snd_pcm
snd_rawmidi            27264  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
i2c_core               23424  2 i2c_ec,i2c_viapro
ieee80211              35272  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7552  1 ieee80211
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    58372  14 snd_seq_oss,snd_seq,snd_via82xx,snd_via82xx_modem,snd_pcm_oss,snd_mixer_oss,snd_ac97_codec,snd_mpu401_uart,snd_pcm,snd_timer,snd_rawmidi,snd_seq_device
soundcore              11232  3 snd
snd_page_alloc         11400  3 snd_via82xx,snd_via82xx_modem,snd_pcm
via_agp                11264  1 
agpgart                34888  2 drm,via_agp
ext3                  142728  2 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  4 usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
via82cxxx              10500  0 [permanent]
sd_mod                 22656  5 
generic                 6276  0 
sata_via               10500  4 
libata                 74892  1 sata_via
scsi_mod              144648  3 sg,sd_mod,libata
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability
```

okay - that should be enough for now - if anybody could give me a hint what i did wrong, or what is missing to get my 1280x800 running on whatever VN800-driver that would really make my day (or maybe the night - actually i decided to not-sleep until this screen is running well)

uh - my text was too long - i have to shorten it - so i'll put my xorg.0.log as an attachment, guess that's the right way anyway...

---

### Post by MihaiM on 2007-02-02
Beryl doesn't work with the VIA driver. Can anyone help?

---

### Post by jonobo on 2007-02-03
Okay - i solved my problem - partially - let's call it a work-around.

I installed the New official VIA Driver (not openchrome), i now have my 1280x800 running and firefox is scrolling smoothly - still i'm not satisfied - not enough fps in glxgears, impossible to play "tuxkart".

The way to my solution can be found on this website:
[http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/]("http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/")

All ideas and reports from other people with a VN800-chipset (or knowledge about it) are welcome ;)

---

### Post by xpan on 2007-02-10
I was trying to install a via card driver at my brother's machine using [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) and everything went fine (no errors, whatsoever).

But, when I change "vesa" driver to "via" driver in xorg.conf I cannot start x anymore and get a meesage "No Device detected"

I attach the xorg.0.log file

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux SteliosDesktop 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
       Before reporting problems, check http://wiki.x.org
       to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
       (++) from command line, (!!) notice, (II) informational,
       (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb  9 23:43:17 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "VA712"
(**) |   |-->Device "VIA Technologies"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
       Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
       Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
       Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
       Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
       Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
       Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
       Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
       Entry deleted from font path.
       (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
       /usr/share/fonts/X11/misc,
       /usr/share/fonts/X11/misc/,
       /usr/share/fonts/X11/TTF/,
       /usr/share/fonts/X11/OTF,
       /usr/share/fonts/X11/Type1/,
       /usr/share/fonts/X11/CID/,
       /usr/share/fonts/X11/100dpi/,
       /usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
       X.Org ANSI C Emulation: 0.3
       X.Org Video Driver: 1.0
       X.Org XInput driver : 0.6
       X.Org Server Extension : 0.3
       X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
       compiled for 7.1.1, module version = 1.0.0
       Module class: X.Org Font Renderer
       ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
       compiled for 7.1.1, module version = 1.0.0
       ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0327 card 1043,81ce rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1327 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2327 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3327 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4327 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:5: chip 1106,5327 card 0000,0000 rev 00 class 08,00,20 hdr 80
(II) PCI: 00:00:6: chip 1106,6327 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:7: chip 1106,7327 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 1106,c327 card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 00:0f:0: chip 1106,0591 card 1043,81cf rev 80 class 01,01,8f hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1043,81cf rev 07 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1106,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1106,3104 rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3337 card 1043,81cf rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:7: chip 1106,287e card 1106,337e rev 00 class 06,00,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1043,086c rev 7c class 02,00,00 hdr 00
(II) PCI: 00:13:0: chip 1106,337b card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 01:00:0: chip 1106,3343 card 1043,81ce rev 01 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 197b,2363 card 197b,2363 rev 02 class 01,06,01 hdr 80
(II) PCI: 03:00:1: chip 197b,2363 card 197b,2363 rev 02 class 01,01,85 hdr 00
(II) PCI: 04:01:0: chip 1106,3288 card 1043,81b3 rev 10 class 04,03,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
       [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
       [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
       [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
       [0] -1  0       0xdd000000 - 0xdeffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
       [0] -1  0       0xa0000000 - 0xbfffffff (0x20000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:3:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
       [0] -1  0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
       [1] -1  0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
       [2] -1  0       0x0000b800 - 0x0000b8ff (0x100) IX[B]
       [3] -1  0       0x0000bc00 - 0x0000bcff (0x100) IX[B]
       [4] -1  0       0x0000c000 - 0x0000c0ff (0x100) IX[B]
       [5] -1  0       0x0000c400 - 0x0000c4ff (0x100) IX[B]
       [6] -1  0       0x0000c800 - 0x0000c8ff (0x100) IX[B]
       [7] -1  0       0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
       [0] -1  0       0xdfe00000 - 0xdfefffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:19:0), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
       [0] -1  0       0xdfd00000 - 0xdfdfffff (0x100000) MX[B]
(--) PCI:*(1:0:0) unknown vendor (0x1106) unknown chipset (0x3343) rev 1, Mem @ 0xa0000000/29, 0xdd000000/24
(II) Addressable bus resource ranges are
       [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
       [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
       [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
       [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
       [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
       [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
       [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
       [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) Active PCI resource ranges:
       [0] -1  0       0xdfdfc000 - 0xdfdfffff (0x4000) MX[B]
       [1] -1  0       0xdfefe000 - 0xdfefffff (0x2000) MX[B]
       [2] -1  0       0xdfffe000 - 0xdfffe0ff (0x100) MX[B]
       [3] -1  0       0xdffff000 - 0xdffff0ff (0x100) MX[B]
       [4] -1  0       0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
       [5] -1  0       0xa0000000 - 0xbfffffff (0x20000000) MX[B](B)
       [6] -1  0       0x0000bc00 - 0x0000bc0f (0x10) IX[B]
       [7] -1  0       0x0000c000 - 0x0000c003 (0x4) IX[B]
       [8] -1  0       0x0000c400 - 0x0000c407 (0x8) IX[B]
       [9] -1  0       0x0000c800 - 0x0000c803 (0x4) IX[B]
       [10] -1 0       0x0000cc00 - 0x0000cc07 (0x8) IX[B]
       [11] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
       [12] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
       [13] -1 0       0x0000d800 - 0x0000d81f (0x20) IX[B]
       [14] -1 0       0x0000dc00 - 0x0000dc1f (0x20) IX[B]
       [15] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
       [16] -1 0       0x0000e400 - 0x0000e40f (0x10) IX[B]
       [17] -1 0       0x0000e800 - 0x0000e8ff (0x100) IX[B]
       [18] -1 0       0x0000ec00 - 0x0000ec0f (0x10) IX[B]
       [19] -1 0       0x0000f000 - 0x0000f003 (0x4) IX[B]
       [20] -1 0       0x0000f400 - 0x0000f407 (0x8) IX[B]
       [21] -1 0       0x0000f800 - 0x0000f803 (0x4) IX[B]
       [22] -1 0       0x0000fc00 - 0x0000fc07 (0x8) IX[B]
(II) Inactive PCI resource ranges:
       [0] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
(II) Active PCI resource ranges after removing overlaps:
       [0] -1  0       0xdfdfc000 - 0xdfdfffff (0x4000) MX[B]
       [1] -1  0       0xdfefe000 - 0xdfefffff (0x2000) MX[B]
       [2] -1  0       0xdfffe000 - 0xdfffe0ff (0x100) MX[B]
       [3] -1  0       0xdffff000 - 0xdffff0ff (0x100) MX[B]
       [4] -1  0       0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
       [5] -1  0       0xa0000000 - 0xbfffffff (0x20000000) MX[B](B)
       [6] -1  0       0x0000bc00 - 0x0000bc0f (0x10) IX[B]
       [7] -1  0       0x0000c000 - 0x0000c003 (0x4) IX[B]
       [8] -1  0       0x0000c400 - 0x0000c407 (0x8) IX[B]
       [9] -1  0       0x0000c800 - 0x0000c803 (0x4) IX[B]
       [10] -1 0       0x0000cc00 - 0x0000cc07 (0x8) IX[B]
       [11] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
       [12] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
       [13] -1 0       0x0000d800 - 0x0000d81f (0x20) IX[B]
       [14] -1 0       0x0000dc00 - 0x0000dc1f (0x20) IX[B]
       [15] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
       [16] -1 0       0x0000e400 - 0x0000e40f (0x10) IX[B]
       [17] -1 0       0x0000e800 - 0x0000e8ff (0x100) IX[B]
       [18] -1 0       0x0000ec00 - 0x0000ec0f (0x10) IX[B]
       [19] -1 0       0x0000f000 - 0x0000f003 (0x4) IX[B]
       [20] -1 0       0x0000f400 - 0x0000f407 (0x8) IX[B]
       [21] -1 0       0x0000f800 - 0x0000f803 (0x4) IX[B]
       [22] -1 0       0x0000fc00 - 0x0000fc07 (0x8) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
       [0] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
(II) OS-reported resource ranges after removing overlaps with PCI:
       [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
       [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
       [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
       [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
       [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
       [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
       [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
       [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
       [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
       [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
       [4] -1  0       0xdfdfc000 - 0xdfdfffff (0x4000) MX[B]
       [5] -1  0       0xdfefe000 - 0xdfefffff (0x2000) MX[B]
       [6] -1  0       0xdfffe000 - 0xdfffe0ff (0x100) MX[B]
       [7] -1  0       0xdffff000 - 0xdffff0ff (0x100) MX[B]
       [8] -1  0       0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
       [9] -1  0       0xa0000000 - 0xbfffffff (0x20000000) MX[B](B)
       [10] -1 0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
       [11] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
       [12] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
       [13] -1 0       0x0000bc00 - 0x0000bc0f (0x10) IX[B]
       [14] -1 0       0x0000c000 - 0x0000c003 (0x4) IX[B]
       [15] -1 0       0x0000c400 - 0x0000c407 (0x8) IX[B]
       [16] -1 0       0x0000c800 - 0x0000c803 (0x4) IX[B]
       [17] -1 0       0x0000cc00 - 0x0000cc07 (0x8) IX[B]
       [18] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
       [19] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
       [20] -1 0       0x0000d800 - 0x0000d81f (0x20) IX[B]
       [21] -1 0       0x0000dc00 - 0x0000dc1f (0x20) IX[B]
       [22] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
       [23] -1 0       0x0000e400 - 0x0000e40f (0x10) IX[B]
       [24] -1 0       0x0000e800 - 0x0000e8ff (0x100) IX[B]
       [25] -1 0       0x0000ec00 - 0x0000ec0f (0x10) IX[B]
       [26] -1 0       0x0000f000 - 0x0000f003 (0x4) IX[B]
       [27] -1 0       0x0000f400 - 0x0000f407 (0x8) IX[B]
       [28] -1 0       0x0000f800 - 0x0000f803 (0x4) IX[B]
       [29] -1 0       0x0000fc00 - 0x0000fc07 (0x8) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
       compiled for 7.1.1, module version = 1.2.0
       ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
       compiled for 7.1.1, module version = 1.0.0
       ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
       compiled for 7.1.1, module version = 1.0.0
       ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
       compiled for 7.1.1, module version = 1.0.0
       ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
       compiled for 7.1.1, module version = 1.0.0
       Module class: X.Org Server Extension
       ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
       compiled for 7.1.1, module version = 2.1.0
       Module class: X.Org Font Renderer
       ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
       compiled for 7.1.1, module version = 1.0.0
       ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
       compiled for 7.1.1, module version = 1.0.0
       ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
       compiled for 7.1.1, module version = 1.0.2
       Module class: X.Org Font Renderer
       ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
       compiled for 7.1.1, module version = 1.1.0
       ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "via"
(II) Loading /usr/lib/xorg/modules/drivers/via_drv.so
(II) Module via: vendor="X.Org Foundation"
       compiled for 7.1.1, module version = 0.2.1
       Module class: X.Org Video Driver
       ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
       compiled for 7.1.1, module version = 1.1.0
       Module class: X.Org XInput Driver
       ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
       compiled for 7.1.1, module version = 1.1.1
       Module class: X.Org XInput Driver
       ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
       compiled for 4.3.99.902, module version = 1.0.0
       Module class: X.Org XInput Driver
       ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) VIA: driver for VIA chipsets: CLE266, KM400/KN400, K8M800,
       PM800/PM880/CN400, VM800, K8M890
(II) Primary Device is: PCI 01:00:0
(EE) No devices detected.

Fatal server error:
no screens found

```

please help! :)


My brother uses the "asus p5vd2-mx" motherboard with the following details:

chipset: s3g unichrome pro p4m890
north bridge part number p4m890
graphics device id 3343

---

### Post by jonobo on 2007-02-10
Hi, which Howto did you use ?

This one ?

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Please give us the output of:

```
$ lspci
```

---

### Post by xpan on 2007-02-10
yes. I used that howto.

this is the output of the lspci:

```

00:00.0 Host bridge: VIA Technologies, Inc. Unknown device 0327
00:00.1 Host bridge: VIA Technologies, Inc. Unknown device 1327
00:00.2 Host bridge: VIA Technologies, Inc. Unknown device 2327
00:00.3 Host bridge: VIA Technologies, Inc. Unknown device 3327
00:00.4 Host bridge: VIA Technologies, Inc. Unknown device 4327
00:00.5 PIC: VIA Technologies, Inc. Unknown device 5327
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6327
00:00.7 Host bridge: VIA Technologies, Inc. Unknown device 7327
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:03.0 PCI bridge: VIA Technologies, Inc. Unknown device c327
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCIE Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3343 (rev 01)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

```

---

### Post by jonobo on 2007-02-10
Okay - got it ;)

Follow this link:
[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats)

Scroll down the page to the table, scan for your P4M890 and drop dead :(
Unfortunately openchrome-driver does not support your device by now, hopefully that will change in the future.

Supposed alternative, try the official VIA-Linux-Driver-Release (no 3D-Acceleration) - use the newest driver from here:
[http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=163](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=163)
direct downloadlink: 
[http://www.viaarena.com/Driver/cle266cn400cn-cx700cn800xorg40072-kernel-src_20061226.tgz](http://www.viaarena.com/Driver/cle266cn400cn-cx700cn800xorg40072-kernel-src_20061226.tgz)
then use this howto (replace 71 with 72, the newer driver):
[http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/](http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/)

or simply stick to the vesa-driver ;)

---

### Post by Taeke on 2007-02-19
I just received my VIA EX motherboard and try to enable the MPEG2/4 decoding by using VIA's driver and the tutorial on [http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/](http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/) . However after running ```
sudo ./makedriver drm
``` it complained about not finding 3D/DRI-Xorg_bin/via_dri.so which could be solved by linking to 3D/DRI-Xorg_bin/Ubuntu/6.10/via_dri.so. 

Then after running makedriver again it complained about not finding directory /usr/src/xc/programs/Xserver/hw/xfree86/drivers/via. Although I followed the tutorial above, including the apt-get stuff, I don't have these sources. I don't even have /usr/src/xc.

Any help would be appreciated.

---

### Post by jonobo on 2007-02-19
Which Chipset does your "VIA Ex" (more details about the motherboard ?) use ?

Please post the exact name of your graphic-chipset here :popcorn:

And there might be just a small typo or click on the wrong driver-download in your installation-trials, i don't have the directory /usr/src/xc/programs/Xserver/hw/xfree86/drivers/via neither, but have never been asked for it to compile the driver. I'm not a pro, so i would advise to simply double-check if you downloaded the right driver and then follow the instructions on [http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/](http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/) again, step by step. If you have more questions, maybe just post on that site, the guy who wrote the howto normally answers after one day.

Check the VIA-Driver-Download-Site carefully, you need the newest driver SOURCES for your chipset for the howto to work (That was my error, when i first tried to install, i simply downloaded the wrong sources): [http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=163](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=163)

For me it was this one: Version - XORG40072-kernel-src_20061226a from 14 February 2007 - (the second entry from top).

But depends on your graphic-chipset.

---

### Post by Taeke on 2007-02-19
The VIA EX uses the CX700M2 chipset which provides an MPEG2 and MPEG4/HDTV decoder. I used the cle266cn400cn-cx700cn800xorg40072-kernel-src_20061226a(20070212111755) sources (from 14 February 2007).

I'm planning to use this board as an HTPC using mythtv (using a Hauppauge PVR 500 MCE).

---

### Post by jonobo on 2007-02-19
Hi, i just tried to compile the driver again and got the same Error-Message now, got no time right now - will be back on the problem later. This is my Error-Message:

```
root@zbox:~/install-via-3-testarea/CLE266CN400CN-CX700CN800XORG40072-kernel-src_20061226/src# ./makedriver
Which version driver you want to release ? 
72
mkdir: kann Verzeichnis „/CLE266CN400CN-CX700CN800XORG40072/“ nicht anlegen: File exists
mkdir: kann Verzeichnis „/CLE266CN400CN-CX700CN800XORG40072//“ nicht anlegen: File exists
Which CPU do you use ? 
1. VIA C3-2(C5N/C5P), C7, Intel Pentium 2/3/4
2. VIA C3
3. AMD K7
4. AMD K8 with 32 bits OS(x86)
5. AMD K8 with 64 bits OS(x86_64)
1
cp: angegebenes Ziel „/usr/src/xc/programs/Xserver/hw/xfree86/drivers/“ ist kein Verzeichnis: No such file or directory
./makedriver: line 378: cd: /usr/src/xc/programs/Xserver/hw/xfree86/drivers/via: No such file or directory
make: *** Keine Regel, um »Makefile« zu erstellen.  Schluss.
chmod: Zugriff auf „mpatch“ nicht möglich: No such file or directory
./makedriver: line 410: ./mpatch: No such file or directory
make: *** Keine Regel, um »clean« zu erstellen.  Schluss.
cp: Aufruf von stat für „via_drv.o“ nicht möglich: No such file or directory
 -------- Complete to make & copy driver --------
```

I guess there will be a simple solution...

---

### Post by Taeke on 2007-02-19
This is exactly (well, except for the language) the same message as I get. Haven't found a solution yet, but I'm desperately trying to solve this issue (reading the source  :)).

---

### Post by Taeke on 2007-02-20
The makedriver script checks your current kernel (for Ubuntu that is 2.6.17-10-generic). Meanwhile the Ubuntu kernel has been updated to 2.6.17-11. Changing this in the makedriver script (depending on your version 1 (version 72) or 2 (version 71) times) fixed the problem. Also change the kernel version in the vinstall(-2d) script.
 
Thanks to emachine ([http://www.ubuntuforums.org/showthread.php?t=351324](http://www.ubuntuforums.org/showthread.php?t=351324)) for pointing this out.

---

### Post by varkatope on 2007-02-23
Hello,

I followed this HOWTO [http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/]("http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/") and got pretty far as the driver is already running.

But there is no 3D-acceleration as DRI is disabled so far.

After a clean install of Ubuntu Edgy Eft 6.10 i changed kernel from 2.6.7-10-386 to 2.6.7-10-generic     . No internet-updates were made.

followed the HOWTO precisely with one addition as i installed the kernel-source and made a symbolic link to /usr/src/linux.

I downloaded the most recent driver version 72 with 3D-acceleration here [http://www.viaarena.com/Driver/cle266cn400cn-cx700cn800xorg40072-kernel-src_20061226a(20070212111755).zip]("http://www.viaarena.com/Driver/cle266cn400cn-cx700cn800xorg40072-kernel-src_20061226a(20070212111755).zip").

The driver-compilation went without errors as fast as i could read the messages.
Then the driver-installation-script "vinstall" gave me the following errors:

```
/CLE266CN400CN-CX700CN800XORG40072$ sudo ./vinstall 
 -------- install start --------
Install Ubuntu 6.10 VIA/S3G UniChrome family graphic driver!
Which CPU do you use ? 
1. VIA C3-2(C5N/C5P), C7/C7M, Intel Pentium 2/3/4
2. VIA C3
3. AMD K7
4. AMD K8 with 32 bits OS(x86)
5. AMD K8 with 64 bits OS(x86_64)
6. Intel Pentium 4 with 64 bits OS(x86_64)
1
Please wait...
Do you want VMI-ONLY(1) path or V4L(2) path?(1/2)
2
cp: Aufruf von stat für &#8222;XServer/via-agp.ko&#8220; nicht möglich: No such file or directory
cp: Aufruf von stat für &#8222;XServer/via.ko&#8220; nicht möglich: No such file or directory
sed: kann /etc/modprobe.conf nicht lesen: No such file or directory

Now start to install VIA/S3G display utility...
Put the main program(s3utility) into the bin directory: /usr/local/bin
Utility installation is finished!
Now start to modify X config...
Found file '/etc/X11/xorg.conf'.
Found file './viax.conf', importing...
Original X config file was saved as /etc/X11/xorg.conf.viaold
X config is modified!
 -------- vinstall end --------
You can run vunistall to Rollback.
/CLE266CN400CN-CX700CN800XORG40072
```

After a reboot the driver was working, even the s3utility and xvidtune but the 3D-acceleration is absent as proven by the Xorg.0.log:

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux mume 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 23 14:07:58 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Standardgrafikkarte"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
<................>
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7
<........>
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "via"
(II) Loading /usr/lib/xorg/modules/drivers/via_drv.so
(II) Module via: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 4.1.72
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) via: driver for VIA chipsets: CLE266, KM400/KN400, K8M800/K8N800,
	PM800/PM880/CN400, P4M800PRO, CX700, K8M890, P4M890, CN750, P4M900
(II) Primary Device is: PCI 01:00:0
(--) Chipset CX700 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfcfe000 - 0xdfcfe7ff (0x800) MX[B]
	[5] -1	0	0xdfcff000 - 0xdfcff0ff (0x100) MX[B]
	[6] -1	0	0xdfefc000 - 0xdfefffff (0x4000) MX[B]
	[7] -1	0	0xdffff000 - 0xdffff0ff (0x100) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[10] -1	0	0xa0000000 - 0xbfffffff (0x20000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000c800 - 0x0000c87f (0x80) IX[B]
	[14] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[15] -1	0	0x0000f000 - 0x0000f01f (0x20) IX[B]
	[16] -1	0	0x0000f400 - 0x0000f41f (0x20) IX[B]
	[17] -1	0	0x0000f800 - 0x0000f81f (0x20) IX[B]
	[18] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfcfe000 - 0xdfcfe7ff (0x800) MX[B]
	[5] -1	0	0xdfcff000 - 0xdfcff0ff (0x100) MX[B]
	[6] -1	0	0xdfefc000 - 0xdfefffff (0x4000) MX[B]
	[7] -1	0	0xdffff000 - 0xdffff0ff (0x100) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[10] -1	0	0xa0000000 - 0xbfffffff (0x20000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c87f (0x80) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f01f (0x20) IX[B]
	[19] -1	0	0x0000f400 - 0x0000f41f (0x20) IX[B]
	[20] -1	0	0x0000f800 - 0x0000f81f (0x20) IX[B]
	[21] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(**) VIA(0): Depth 24, (--) framebuffer bpp 32
(==) VIA(0): RGB weight 888
(==) VIA(0): Default visual is TrueColor
(II) VIA(0): MergedFB mode forced off.
(==) VIA(0): Not using video BIOS to set modes
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VIA(0): Primary V_BIOS segment is: 0xc000
(II) VIA(0): MapBase = b7afc000, MmioBase=dd000000
(II) VIA(0): RegCR08 = 0, RegCR09=4f
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) VIA(0): VESA BIOS detected
(II) VIA(0): VESA VBE Version 3.0
(II) VIA(0): VESA VBE Total Mem: 131072 kB
(II) VIA(0): VESA VBE OEM: VIA CX700
(II) VIA(0): VESA VBE OEM Software Rev: 1.0
(II) VIA(0): VESA VBE OEM Vendor: 
(II) VIA(0): VESA VBE OEM Product: 
(II) VIA(0): VESA VBE OEM Product Rev: 
(--) VIA(0): Chipset: "CX700"
(--) VIA(0): Chipset Rev.: 0
(--) VIA(0): mapping MMIO @ 0xdd000000 with size 0x9000
(--) VIA(0): mapping BitBlt MMIO @ 0xdd200000 with size 0x200000
(--) VIA(0): mapping Integrated TV MMIO @ 0xdd00c000 with size 0x100
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) VIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) VIA(0): videoram =  131072k
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules/libi2c.so
(II) VIA(0): I2C bus "I2C bus 1" initialized.
(II) VIA(0): I2C bus "I2C bus 2" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) VIA(0): VESA VBE DDC supported
(II) VIA(0): VESA VBE DDC Level 2
(II) VIA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VIA(0): VESA VBE DDC read failed
(II) VIA(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
(II) VIA(0): I2C device "I2C bus 1:ddc2" removed.
(--) VIA(0): No DDC signal
(II) VIA(0): Generic Monitor: Using hsync range of 30.00-113.00 kHz
(II) VIA(0): Generic Monitor: Using vrefresh range of 43.00-60.00 Hz
(II) VIA(0): Clock range:  20.00 to 270.00 MHz
<...............>
(--) VIA(0): Virtual size is 1024x768 (pitch 1024)
(**) VIA(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) VIA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) VIA(0):  Mode "1024x512": 41.3 MHz, 31.9 kHz, 60.0 Hz
(II) VIA(0): Modeline "1024x512"   41.30  1024 1056 1160 1296  512 513 516 531
(**) VIA(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) VIA(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) VIA(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) VIA(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) VIA(0):  Mode "720x576": 32.7 MHz, 35.9 kHz, 60.1 Hz
(II) VIA(0): Modeline "720x576"   32.70  720 744 816 912  576 577 580 597
(**) VIA(0):  Mode "856x480": 31.7 MHz, 29.8 kHz, 59.9 Hz
(II) VIA(0): Modeline "856x480"   31.70  856 872 960 1064  480 481 484 497
(**) VIA(0):  Mode "848x480": 31.5 MHz, 29.8 kHz, 60.0 Hz
(II) VIA(0): Modeline "848x480"   31.50  848 864 952 1056  480 481 484 497
(**) VIA(0):  Mode "800x480": 29.6 MHz, 29.8 kHz, 60.0 Hz
(II) VIA(0): Modeline "800x480"   29.58  800 816 896 992  480 481 484 497
(**) VIA(0):  Mode "720x480": 26.7 MHz, 29.8 kHz, 60.0 Hz
(II) VIA(0): Modeline "720x480"   26.70  720 736 808 896  480 481 484 497
(**) VIA(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) VIA(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(==) VIA(0): DPI set to (75, 75)
Unknown Panel Size!!
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(**) VIA(0): Option: Cap0 auto detect= 0
(**) VIA(0): Option: Cap1 auto detect= 0
(**) VIA(0): Option: Cap0_FieldSwap Disabled
(**) VIA(0): Option: Cap0_HFilter Enabled
(**) VIA(0): Option: Cap1_HFilter Enabled
(**) VIA(0): Option: Capture Over Scan ON
(**) VIA(0): Option: HQV Filter Manual Select Disabled
(**) VIA(0): Option: Set MPEG decode frame buffer number Disable
(**) VIA(0): Option: Capture 1 use H/W auto flip
(**) VIA(0): Option: Capture 0 use V1 engine : Default path
(**) VIA(0): Option: HQV Manual Switch Disabled
(**) VIA(0): Option: No mpeg add one line on bottom = 0
(**) VIA(0): Option: DeBlocking Disable!!
(**) VIA(0): DeBlocking Minimum Width Default : 320
(**) VIA(0): DeBlocking Minimum Height Default: 240
(**) VIA(0): Option: Use 2D BitBlt method to write event-tag into VQ and make sure MPEG decode END Disable
(II) VIALoadVideoOption
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdd000000 - 0xddffffff (0x1000000) MS[B]
	[1] 0	0	0xa0000000 - 0xbfffffff (0x20000000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdfcfe000 - 0xdfcfe7ff (0x800) MX[B]
	[7] -1	0	0xdfcff000 - 0xdfcff0ff (0x100) MX[B]
	[8] -1	0	0xdfefc000 - 0xdfefffff (0x4000) MX[B]
	[9] -1	0	0xdffff000 - 0xdffff0ff (0x100) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[12] -1	0	0xa0000000 - 0xbfffffff (0x20000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c87f (0x80) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f01f (0x20) IX[B]
	[21] -1	0	0x0000f400 - 0x0000f41f (0x20) IX[B]
	[22] -1	0	0x0000f800 - 0x0000f81f (0x20) IX[B]
	[23] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[24] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[25] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(--) VIA(0): mapping framebuffer @ 0xa0000000 with size 0x8000000
(==) VIA(0): Write-combining range (0xa0000000,0x8000000)
(--) VIA(0): Frame buffer start: 0xaf85c000, free start: 0x300000 end: 0x8000000
(--) VIA(0): mapping MMIO @ 0xdd000000 with size 0x9000
(--) VIA(0): mapping BitBlt MMIO @ 0xdd200000 with size 0x200000
(--) VIA(0): mapping Integrated TV MMIO @ 0xdd00c000 with size 0x100
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) VIA(0): VIAScreenInit : V4L Enabled : fd2 = 9 
(II) VIA(0): I2C device "I2C bus 2:TV" registered at address 0x40.
(II) VIA(0): I2C device "I2C bus 2:TV" removed.
(II) VIA(0): I2C device "I2C bus 2:TV" registered at address 0x40.
(II) VIA(0): I2C device "I2C bus 2:TV" removed.
(II) VIA(0): I2C device "I2C bus 2:TV" registered at address 0x40.
(II) VIA(0): I2C device "I2C bus 2:TV" removed.
(II) VIA(0): 3D Engine has been initilized.
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
(II) VIA(0): [drm] drmOpen failed
(EE) VIA(0): [dri] DRIScreenInit failed.  Disabling DRI.
(II) VIA(0): VIAInternalScreenInit
(II) VIA(0): Frame Buffer From (0,0) To (1024,1280)
(II) VIA(0): Using 1280 lines for offscreen memory.
(II) VIA(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	8x8 color pattern filled rectangles
	CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		15 128x128 slots
		4 256x256 slots
		32 8x8 color pattern slots
(==) VIA(0): Backing store disabled
(==) VIA(0): Silken mouse enabled
(WW) No Gamma setting file exist, Create new ones
(**) Option "dpms"
(**) VIA(0): DPMS enabled
(II) VIA(0): direct rendering disabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "de"
(**) Generic Keyboard: XkbLayout: "de"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwertz)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+de+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
find_mesa_visual returned NULL for visualID = 0x0025

```

and glxinfo:

```
~$ glxinfo
name of display: :0.0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  18
  Current serial number in output stream:  19
~$ 

```

I wasn't able to test the hardware-video-acceleration yet but as far as DRI doesn't work i'm in need of help anyway.

---

### Post by sohaibma on 2007-03-03
I am trying to install the drivers in edgy from
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

when i reach the drm kernel modules section and try to execute the following command:
make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via

the following error shows up:
```
make -C /lib/modules/2.6.17-11-386/build SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules 
make[1]: Entering directory `/lib/modules/2.6.17-11-386/build' 
make[1]: *** No rule to make target `modules'. Stop. 
make[1]: Leaving directory `/lib/modules/2.6.17-11-386/build' make: *** 
[modules] Error 2

```



note: i have build-essential installed. The /build directory was not already there, i had to create it.

what is this error and how do i fix it.

---

### Post by link141 on 2007-03-29
Hi,
I also also have a Via/S3G Unichrome that requires the use of the openchrome driver, and I got it compiled and working on Kubuntu Edgy.  Yesterday, however, I decided edgy wasn't edgy enough, and decided to install the beta of Feisty.  Even though my integrated graphics set isn't detected out-of-the box, it is detected as "openchrome" when I go into system settings-> moniter and display-> hardware-> graphics card, and has a button below that offers me the option of selecting the openchrome driver (see screenshot), but as soon as I select it, apply the changes, and restart the xserver, the @##$ thing changes back to vesa!!  I assume that the this means the driver is already pre-compiled and installed in Feisty (which would be nice), but I can't understand why it won't let me use the driver.  Is there anyway to specify a driver under the "manufacturers" list in a terminal, instead of doing it graphically in the system settings frontend?  Or am I just going to have to re-compile the driver for Feisty?  Any help greatly appreciated.
Thanks

---

### Post by ivanopulo on 2007-04-01
[http://www.viaarena.com/Driver/linux-fbdev-kernel-bin_2.6.00.03.tgz](http://www.viaarena.com/Driver/linux-fbdev-kernel-bin_2.6.00.03.tgz) 

PN800

---

### Post by link141 on 2007-04-01
Hey, Thanks :D!!
This looks like an updated version of the Linux drivers I got on my motherboard cd, except **with** Ubuntu drivers (which I've been looking for for a year and a half ](*,)).  I have a couple of questions though:
[list=1]
[*]I am currently running feisty, will these drivers work on this Ubuntu version? (perhaps my posts should be moved to the feisty development area)
[*]As stated in my previous post, it appears that the appropriate driver (Openchrome) for my chipset is already in feisty, but it won't let me enable it (darn!).  If it is in there, will it be worth it to try to get it to work?
[*]I've got a couple of options, to use this driver, or the openchrome version.  Several have claimed that the openchrome driver is the most efficient way to use the chipset on linux - although, they may have only been talking about it being the most efficient **open-source** driver - and I want to know: which of the two drivers will work better?
[/list]

My chipset is either a K8M890 or a P4M800CE, but the driver you gave should work for both of these.  If anyone could answer any of these questions, that would be great!   
Thanks

---

### Post by deepclutch on 2007-04-05
why they are not including open chrome in repository or some generous helping mind(s) should have made a .deb file and kept.

---

### Post by PendragonUK on 2007-04-08
Has anyone had any luck with the newer Chrome hardware?

My laptop is running 9 series chip-set.

Windows identifies this as "VIA Chrome9 HC IGP" The handbook has the following info...

VIA VN896 Integrated Video System
(Internal On Chip)
Chrome 9HC
Integrated 128bit 2D/3D Graphic Engine and Clock up to 250MHz
Supports CRT Resolutions up to 2048 * 1536 at 75Hz

The screen is 15.4" WXGA (1280 * 800) TFT LCD

I'm currently using the Vesta driver, this isn't the end of the world but it would be nice to have the 2D driver at least. There is no intention of running games on this machine. (full on gaming rig looks after that side of things ;) but that's another storey)

It would be nice to run Beryl if possible but not essential.

---

### Post by link141 on 2007-04-09
[quote=PendragonUK]Has anyone had any luck with the newer Chrome hardware?[/quote]
To answer you question, VIA doesn't fully support your chipset under linux yet (see their [forum](http://forums.viaarena.com/messageview.aspx?catid=28&threadid=76991&enterthread=y)).  A post on thread mentions that the [Openchrome](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats) project is working on drivers for your chipset...
Hope this was useful

Now onto my problem...  ivanpulo, how do I install these drivers?  I've tried running the shell script that's included with the package (and a few other things...), but it doesn't seem to do much.  Are there any extra steps required to get these working?
link141

---

### Post by epidemiks on 2007-08-25
i'm using the openchrome instructions from here [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) to get my vn896 graphics working, but when i try to compile the 2d driver, with  i get this:
> rachel@edward:~/openchrome$ ./autogen.sh --prefix=/usr
**./autogen.sh: 9: autoreconf: not found**

what's the deal?

edit..

ok i installed autoreconf.
now i get this:
> rachel@edward:~/openchrome$ ./autogen.sh --prefix=/usr
Can't exec "aclocal": No such file or directory at /usr/bin/autoreconf2.50 line 182.
Use of uninitialized value in pattern match (m//) at /usr/bin/autoreconf2.50 line 182.
Can't exec "automake": No such file or directory at /usr/bin/autoreconf2.50 line 183.
Use of uninitialized value in pattern match (m//) at /usr/bin/autoreconf2.50 line 183.
autoreconf2.50: Entering directory `.'
autoreconf2.50: configure.ac: not using Gettext
autoreconf2.50: running: aclocal  --output=aclocal.m4t
Can't exec "aclocal": No such file or directory at /usr/share/autoconf/Autom4te/FileUtils.pm line 290.
autoreconf2.50: failed to run aclocal: No such file or directory
rachel@edward:~/openchrome$ ./autogen.sh
Can't exec "aclocal": No such file or directory at /usr/bin/autoreconf2.50 line 182.
Use of uninitialized value in pattern match (m//) at /usr/bin/autoreconf2.50 line 182.
Can't exec "automake": No such file or directory at /usr/bin/autoreconf2.50 line 183.
Use of uninitialized value in pattern match (m//) at /usr/bin/autoreconf2.50 line 183.
autoreconf2.50: Entering directory `.'
autoreconf2.50: configure.ac: not using Gettext
autoreconf2.50: running: aclocal  --output=aclocal.m4t
Can't exec "aclocal": No such file or directory at /usr/share/autoconf/Autom4te/FileUtils.pm line 290.
autoreconf2.50: failed to run aclocal: No such file or directory
rachel@edward:~/openchrome$ cd unichrome
rachel@edward:~/openchrome/unichrome$ ./autogen.sh --prefix=/usr
bash: ./autogen.sh: No such file or directory
rachel@edward:~/openchrome/unichrome$ cd ..
rachel@edward:~/openchrome$ ./autogen.sh --prefix=/usr
Can't exec "aclocal": No such file or directory at /usr/bin/autoreconf2.50 line 182.
Use of uninitialized value in pattern match (m//) at /usr/bin/autoreconf2.50 line 182.
Can't exec "automake": No such file or directory at /usr/bin/autoreconf2.50 line 183.
Use of uninitialized value in pattern match (m//) at /usr/bin/autoreconf2.50 line 183.
autoreconf2.50: Entering directory `.'
autoreconf2.50: configure.ac: not using Gettext
autoreconf2.50: running: aclocal  --output=aclocal.m4t
Can't exec "aclocal": No such file or directory at /usr/share/autoconf/Autom4te/FileUtils.pm line 290.
autoreconf2.50: failed to run aclocal: No such file or directory


---

### Post by epidemiks on 2007-08-29
ok, this is really starting to bug me..
i've got the screen displaying an appropriate resolution at least, but i CANNOT get this via/s3 driver to work...
surely there's an easy method to get this working - the viaarena.com drivers just won't work for me!!
I'm about 25 minutes from dumping ubuntu and reinstalling xp :(

---

### Post by link141 on 2007-09-10
Hey, take it easy there :)
You probably don't have the "build-essential" package installed (this package installs the necessary software for compiling source code and installing it on your machine).  
You can install it by typing "sudo apt-get install build-essential" in a terminal.  
So before you dump Ubuntu, and go for that other OS&#8482;,  just try this first, and someone can help you with any problems you run into.

---

### Post by ikey_d on 2007-09-15
Ok I'm running Feisty on a Gateway MX3210 laptop; followed the guide and everything went well with no errors... my chipset is VN800 and with all the modules loaded I get 4584 frames in 5.0 seconds = 916.751 FPS from glxgears. I can change my resolution and everything else seems to work EXCEPT I still cannot enable 3D Desktop Effects.... I have tried compiz and beryl and none of them will work... HELP!!... please :)

---

### Post by BoHu on 2007-09-19
you can't use VIA Chrome s3 with Ubuntu (or any Debian derivitive). Playing video for more than a few minutes causes a hard Xorg freeze.  Not even CTRL-ALT-DELETE will work. And this is on a System76 which was DESIGNED to run Ubuntu!!  So far, PCLOS and it's derivitives (SAM and the gnome remaster) are the only distros that can run this graphics chip without hard-freezing. I don't know why this is, but I wish the other distros would hurry up and figure it out, cuz I really dislike PCLOS. I want to run Ubuntu!!

---

### Post by Vox754 on 2007-09-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/linux/+bug/43154](https://bugs.launchpad.net/linux/+bug/43154) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
                > **BoHu said:**
> you can't use VIA Chrome s3 with Ubuntu (or any Debian derivitive). Playing video for more than a few minutes causes a hard Xorg freeze.  Not even CTRL-ALT-DELETE will work.

Of course you can use VIA S3 Unichrome Pro in Ubuntu, but let me say this once and for all: **this is not a powerful chipset. You may not do fancy stuff with it.** Do not attempt to use Beryl, Compiz or any other eye candy. Use the damn card to work on your plain 2D desktop and live with it.

Essentially, the "via" module supports 2D but it fails with 3D. Why? Because specifications from VIA are missing.
The fact that these cards hang the system is a know bug that has been around for ages (look at the date of the oldest threads you may find) and it has not been fixed because of lack of specifications.

The [Launchpad bug #43154]("https://bugs.launchpad.net/linux/+bug/43154") points to the bug trackers of Xorg and the Linux Kernel where you may read more about the problem, in which an issue with IRQs is relevant.

The simple solution that may work for some people is
```

Section "Device"
        Identifier      "*This is an identifier*"
        Driver          "via"
#       Option          "DisableIRQ"
        Option          "EnableAGPDMA"
        BusID           "*Your bus ID in here*"
EndSection

```
This is, of course, the relevant Section in "/etc/X11/xorg.conf"
Some people need to DisableIRQ, some people do not. It varies.
You may also avoid loading the "dri" module, also in "/etc/X11/xorg.conf"

For more information on what you can change
```

man via
man xorg.conf

```

My ultimate stance on this issue is simple: I do not expect much from this chipset.
If you want a true, powerful video card, capable of handling everything fancy, buy nVidia or ATI and move on.

Now, if you can wire yourself to the chipset, processor and all relevant motherboard buses, and understand what each electrical signal does, then by all means contact the people at Xorg, Openchrome or the Linux Kernel and they'll fix it in no time!

Another alternative, if you have the cash, is buying VIA and forcing them to release full specifications.

---

### Post by dcstar on 2007-09-21
> **Vox754 said:**
> 
..........
If you want a true, powerful video card, capable of handling everything fancy, buy nVidia or ATI and move on.
.........

Exactly, after wasting too much time on my old PC trying to get the inbuilt VIA Unichrome video to perform, I went out and purchased an old NVIDIA chipset video board (for just a few dollars) that suited my motherboard, all problems were then solved and I got much better video performance.

In my new PC, I made sure it had a NVIDIA chipset in it so it would be Linux compatible - and it runs fine.

---

### Post by PendragonUK on 2007-09-22
Nice move if you have the option... It's a little more tricky on a laptop. A lot of the budget laptops are VIA chipsets. I have always found it strange that there isn't better support for VIA from the Linux community, seeing how popular VIA is amongst the emerging markets around the world. You are not going to find too many American components in China for instance. Using the vesta drivers is fine for most things, but I don't know how it affects the battery life...

---

### Post by GuruX on 2007-11-05
I have an Acer laptop with the KM400 chipset on Gutsy. According to VIAArena this mainboard has the 7205 graphics driver, which is supported by the Unichrome driver. But after installing the unichrome drivers through synaptics X didnt want to start at all. Im now running with the live cd, so excuse me if some characters are wrong. I have a swedish keyboard.

Heres output of lspci
```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:07.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:09.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

```

Heres my xorg.conf
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```


And heres the Xorg.0.log
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux lillenubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov  5 11:48:54 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3205 card 1106,7205 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b168 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 104c,ac50 card 2000,0000 rev 02 class 06,07,00 hdr 02
(II) PCI: 00:08:0: chip 104c,8026 card 1025,0033 rev 00 class 0c,00,10 hdr 00
(II) PCI: 00:09:0: chip 168c,0013 card 144f,7064 rev 01 class 02,00,00 hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1025,0033 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1025,0033 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1025,0033 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1025,0033 rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1025,0033 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1025,0033 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1025,0033 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 1025,0033 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1025,0033 rev 74 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 1106,7205 card 1025,0033 rev 01 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf3ffffff (0x4000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (0:7:0), (0,2,5), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x40000000 - 0x43ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) unknown vendor (0x1106) unknown chipset (0x7205) rev 1, Mem @ 0xf0000000/26, 0xd1000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xefffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xd0014c00 - 0xd0014cff (0x100) MX[B]
	[1] -1	0	0xd0014800 - 0xd00148ff (0x100) MX[B]
	[2] -1	0	0xd0000000 - 0xd000ffff (0x10000) MX[B]
	[3] -1	0	0xd0010000 - 0xd0013fff (0x4000) MX[B]
	[4] -1	0	0xd0014000 - 0xd00147ff (0x800) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
	[8] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[9] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[10] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[11] -1	0	0x00001c60 - 0x00001c6f (0x10) IX[B]
	[12] -1	0	0x00001c40 - 0x00001c5f (0x20) IX[B]
	[13] -1	0	0x00001c20 - 0x00001c3f (0x20) IX[B]
	[14] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd0014c00 - 0xd0014cff (0x100) MX[B]
	[1] -1	0	0xd0014800 - 0xd00148ff (0x100) MX[B]
	[2] -1	0	0xd0000000 - 0xd000ffff (0x10000) MX[B]
	[3] -1	0	0xd0010000 - 0xd0013fff (0x4000) MX[B]
	[4] -1	0	0xd0014000 - 0xd00147ff (0x800) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
	[8] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[9] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[10] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[11] -1	0	0x00001c60 - 0x00001c6f (0x10) IX[B]
	[12] -1	0	0x00001c40 - 0x00001c5f (0x20) IX[B]
	[13] -1	0	0x00001c20 - 0x00001c3f (0x20) IX[B]
	[14] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0014c00 - 0xd0014cff (0x100) MX[B]
	[5] -1	0	0xd0014800 - 0xd00148ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xd000ffff (0x10000) MX[B]
	[7] -1	0	0xd0010000 - 0xd0013fff (0x4000) MX[B]
	[8] -1	0	0xd0014000 - 0xd00147ff (0x800) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[15] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[17] -1	0	0x00001c60 - 0x00001c6f (0x10) IX[B]
	[18] -1	0	0x00001c40 - 0x00001c5f (0x20) IX[B]
	[19] -1	0	0x00001c20 - 0x00001c3f (0x20) IX[B]
	[20] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "via"
(II) Loading /usr/lib/xorg/modules/drivers//via_drv.so
(II) Module via: vendor="http://unichrome.sf.net/"
	compiled for 7.2.0, module version = 0.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) VIA: driver for VIA Unichrome integrated graphics.
(II)     VT3122: CLE266 (CastleRock).
(II)     VT7205: KM400, KM400A, KN400, P4M800 (Unichrome).
(II)     VT3108: K8M800, K8N800, K8N800A (Unichrome Pro, aka Pro B).
(II)     VT3118: CN400, PM800, PM880, PN800 (Unichrome Pro A).
(II)     VT3344: VN800, P4M800Pro, CN700 (Unichrome Pro).
(II)     VT3157: CX700, CX700M (Unichrome Pro).
(II)     VT3230: K8M890 (Chrome9 IGP).
(II)     VT3343: P4M890 (Unichrome Pro).
(II)     VT3225: CN750, CN800 (Unichrome Pro).
(II)     VT3371: P4M900 (Chrome 9 HC IGP).
(II) 
(II)  Not all of the listed chips are actually supported currently.
(II) 
(II) Primary Device is: PCI 01:00:0
(--) Chipset VT7205 found
(!!) VIA Technologies does not support or endorse this driver in any way.
(!!) For support, please refer to http://unichrome.sf.net/ or your X vendor.
(II) Using development version of the unichrome driver.
(II) git SHA-ID: c420f04c.. (on master).
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0014c00 - 0xd0014cff (0x100) MX[B]
	[5] -1	0	0xd0014800 - 0xd00148ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xd000ffff (0x10000) MX[B]
	[7] -1	0	0xd0010000 - 0xd0013fff (0x4000) MX[B]
	[8] -1	0	0xd0014000 - 0xd00147ff (0x800) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[15] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[17] -1	0	0x00001c60 - 0x00001c6f (0x10) IX[B]
	[18] -1	0	0x00001c40 - 0x00001c5f (0x20) IX[B]
	[19] -1	0	0x00001c20 - 0x00001c3f (0x20) IX[B]
	[20] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0014c00 - 0xd0014cff (0x100) MX[B]
	[5] -1	0	0xd0014800 - 0xd00148ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xd000ffff (0x10000) MX[B]
	[7] -1	0	0xd0010000 - 0xd0013fff (0x4000) MX[B]
	[8] -1	0	0xd0014000 - 0xd00147ff (0x800) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[18] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[19] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[20] -1	0	0x00001c60 - 0x00001c6f (0x10) IX[B]
	[21] -1	0	0x00001c40 - 0x00001c5f (0x20) IX[B]
	[22] -1	0	0x00001c20 - 0x00001c3f (0x20) IX[B]
	[23] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[24] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[25] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) VIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) VIA(0): Depth 24, (--) framebuffer bpp 32
(==) VIA(0): RGB weight 888
(==) VIA(0): Default visual is TrueColor
(==) VIA(0): Using HW cursor
(--) VIA(0): Found VT7205 UniChrome/Chrome IGP
(--) VIA(0): Found KM400/KN400 HostBridge (rev. 0x03).
(--) VIA(0): Found Acer Aspire 135x.
(--) VIA(0): mapping MMIO @ 0xd1000000 with size 0x9000
(--) VIA(0): mapping BitBlt MMIO @ 0xd1200000 with size 0x10000
(--) VIA(0): Using 65536kB of RAM (133Mhz DDR - PC2100)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) VIA(0): I2C bus "I2C bus 1" initialized.
(II) VIA(0): I2C bus "I2C bus 2" initialized.
(II) VIA(0): I2C bus "I2C bus 3" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) VIA(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
(II) VIA(0): I2C device "I2C bus 1:ddc2" removed.
(II) VIA(0): Enabling panel from PCI-Subsystem Id information.
(II) VIA(0): Panel Native Resolution is 640x480.
(II) VIA(0): I2C device "I2C bus 3:CH7xxx" registered at address 0xEA.
(WW) VIA(0): Unknown TV Encoder found at I2C bus 3 EA.
(II) VIA(0): I2C device "I2C bus 3:CH7xxx" removed.
(II) VIA(0): Listing Outputs:
(II) VIA(0): Bus CRT: Output CRT: Active
(II) VIA(0): Bus DFP: Output Panel: Active
(II) VIA(0): "CRT - Generic Monitor": Imposing HSync values from config monitor "Generic Monitor".
(II) VIA(0): "CRT - Generic Monitor": Imposing VRefresh values from config monitor "Generic Monitor".
(II) VIA(0): Clock range:  20.00 to 230.00 MHz
(II) VIA(0): Validating Modes from X (config & built-in)
(II) VIA(0): Rejected mode "640x350" (640x350:31.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "320x175" (320x175:15.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "640x400" (640x400:31.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "320x200" (320x200:15.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "720x400" (720x400:35.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "360x200" (360x200:17.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "640x480" (640x480:25.2Mhz): illegal vertical timings
(II) VIA(0): Rejected mode "320x240" (320x240:12.6Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "640x480" (640x480:31.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "320x240" (320x240:15.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "640x480" (640x480:31.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "320x240" (320x240:15.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "640x480" (640x480:36.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "320x240" (320x240:18.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "800x600" (800x600:36.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "400x300" (400x300:18.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "800x600" (800x600:40.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "400x300" (400x300:20.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "800x600" (800x600:50.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "400x300" (400x300:25.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "800x600" (800x600:49.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "400x300" (400x300:24.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "800x600" (800x600:56.3Mhz): hsync out of range
(II) VIA(0): Rejected mode "400x300" (400x300:28.1Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1024x768" (1024x768:44.9Mhz): interlace mode not supported
(II) VIA(0): Rejected mode "512x384" (512x384:22.4Mhz): interlace mode not supported
(II) VIA(0): Rejected mode "1024x768" (1024x768:65.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "512x384" (512x384:32.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1024x768" (1024x768:75.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "512x384" (512x384:37.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1024x768" (1024x768:78.8Mhz): hsync out of range
(II) VIA(0): Rejected mode "512x384" (512x384:39.4Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1024x768" (1024x768:94.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "512x384" (512x384:47.2Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1152x864" (1152x864:108.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "576x432" (576x432:54.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1280x960" (1280x960:108.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "640x480" (640x480:54.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1280x960" (1280x960:148.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "640x480" (640x480:74.2Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1280x1024" (1280x1024:108.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "640x512" (640x512:54.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1280x1024" (1280x1024:135.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "640x512" (640x512:67.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1280x1024" (1280x1024:157.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "640x512" (640x512:78.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1600x1200" (1600x1200:162.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "800x600" (800x600:81.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1600x1200" (1600x1200:175.5Mhz): Memory bandwidth exceeded.
(II) VIA(0): Rejected mode "800x600" (800x600:87.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1600x1200" (1600x1200:189.0Mhz): Memory bandwidth exceeded.
(II) VIA(0): Rejected mode "800x600" (800x600:94.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1600x1200" (1600x1200:202.5Mhz): mode clock too high
(II) VIA(0): Rejected mode "800x600" (800x600:101.2Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1600x1200" (1600x1200:229.5Mhz): mode clock too high
(II) VIA(0): Rejected mode "800x600" (800x600:114.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1792x1344" (1792x1344:204.8Mhz): mode clock too high
(II) VIA(0): Rejected mode "896x672" (896x672:102.4Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1792x1344" (1792x1344:261.0Mhz): mode clock too high
(II) VIA(0): Rejected mode "896x672" (896x672:130.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1856x1392" (1856x1392:218.3Mhz): mode clock too high
(II) VIA(0): Rejected mode "928x696" (928x696:109.2Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1856x1392" (1856x1392:288.0Mhz): mode clock too high
(II) VIA(0): Rejected mode "928x696" (928x696:144.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1920x1440" (1920x1440:234.0Mhz): mode clock too high
(II) VIA(0): Rejected mode "960x720" (960x720:117.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1920x1440" (1920x1440:297.0Mhz): mode clock too high
(II) VIA(0): Rejected mode "960x720" (960x720:148.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "832x624" (832x624:57.3Mhz): hsync out of range
(II) VIA(0): Rejected mode "416x312" (416x312:28.6Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1280x768" (1280x768:80.1Mhz): hsync out of range
(II) VIA(0): Rejected mode "640x384" (640x384:40.1Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1280x800" (1280x800:83.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "640x400" (640x400:41.7Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1152x768" (1152x768:65.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "576x384" (576x384:32.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1152x864" (1152x864:121.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "576x432" (576x432:60.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1400x1050" (1400x1050:122.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "700x525" (704x525:61.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1400x1050" (1400x1050:151.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "700x525" (704x525:75.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1400x1050" (1400x1050:155.8Mhz): horizontal sync too wide
(II) VIA(0): Rejected mode "700x525" (704x525:77.9Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1400x1050" (1400x1050:184.0Mhz): Memory bandwidth exceeded.
(II) VIA(0): Rejected mode "700x525" (704x525:92.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1440x900" (1440x900:108.8Mhz): horizontal sync too wide
(II) VIA(0): Rejected mode "720x450" (720x450:54.4Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1600x1024" (1600x1024:106.9Mhz): horizontal sync too narrow
(II) VIA(0): Rejected mode "800x512" (800x512:53.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1680x1050" (1680x1050:147.1Mhz): hsync out of range
(II) VIA(0): Rejected mode "840x525" (840x525:73.6Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1920x1200" (1920x1200:193.2Mhz): Memory bandwidth exceeded.
(II) VIA(0): Rejected mode "960x600" (960x600:96.6Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1920x1200" (1920x1200:230.0Mhz): mode clock too high
(II) VIA(0): Rejected mode "960x600" (960x600:115.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1920x1440" (1920x1440:341.4Mhz): mode clock too high
(II) VIA(0): Rejected mode "960x720" (960x720:170.7Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "2048x1536" (2048x1536:266.9Mhz): mode clock too high
(II) VIA(0): Rejected mode "1024x768" (1024x768:133.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "2048x1536" (2048x1536:340.5Mhz): mode clock too high
(II) VIA(0): Rejected mode "1024x768" (1024x768:170.2Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "2048x1536" (2048x1536:388.0Mhz): mode clock too high
(II) VIA(0): Rejected mode "1024x768" (1024x768:194.0Mhz): doublescan mode not supported
(II) VIA(0): Validating Modes from Output "CRT - Generic Monitor"
(II) VIA(0): Rejected mode "640x350" (640x350:31.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "320x175" (320x175:15.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "640x400" (640x400:31.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "320x200" (320x200:15.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "720x400" (720x400:35.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "360x200" (360x200:17.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "640x480" (640x480:25.2Mhz): illegal vertical timings
(II) VIA(0): Rejected mode "320x240" (320x240:12.6Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "640x480" (640x480:31.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "320x240" (320x240:15.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "640x480" (640x480:31.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "320x240" (320x240:15.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "640x480" (640x480:36.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "320x240" (320x240:18.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "800x600" (800x600:36.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "400x300" (400x300:18.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "800x600" (800x600:40.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "400x300" (400x300:20.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "800x600" (800x600:50.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "400x300" (400x300:25.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "800x600" (800x600:49.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "400x300" (400x300:24.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "800x600" (800x600:56.3Mhz): hsync out of range
(II) VIA(0): Rejected mode "400x300" (400x300:28.1Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1024x768" (1024x768:44.9Mhz): interlace mode not supported
(II) VIA(0): Rejected mode "512x384" (512x384:22.4Mhz): interlace mode not supported
(II) VIA(0): Rejected mode "1024x768" (1024x768:65.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "512x384" (512x384:32.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1024x768" (1024x768:75.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "512x384" (512x384:37.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1024x768" (1024x768:78.8Mhz): hsync out of range
(II) VIA(0): Rejected mode "512x384" (512x384:39.4Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1024x768" (1024x768:94.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "512x384" (512x384:47.2Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1152x864" (1152x864:108.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "576x432" (576x432:54.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1280x960" (1280x960:108.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "640x480" (640x480:54.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1280x960" (1280x960:148.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "640x480" (640x480:74.2Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1280x1024" (1280x1024:108.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "640x512" (640x512:54.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1280x1024" (1280x1024:135.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "640x512" (640x512:67.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1280x1024" (1280x1024:157.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "640x512" (640x512:78.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1600x1200" (1600x1200:162.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "800x600" (800x600:81.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1600x1200" (1600x1200:175.5Mhz): Memory bandwidth exceeded.
(II) VIA(0): Rejected mode "800x600" (800x600:87.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1600x1200" (1600x1200:189.0Mhz): Memory bandwidth exceeded.
(II) VIA(0): Rejected mode "800x600" (800x600:94.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1600x1200" (1600x1200:202.5Mhz): mode clock too high
(II) VIA(0): Rejected mode "800x600" (800x600:101.2Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1600x1200" (1600x1200:229.5Mhz): mode clock too high
(II) VIA(0): Rejected mode "800x600" (800x600:114.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1792x1344" (1792x1344:204.8Mhz): mode clock too high
(II) VIA(0): Rejected mode "896x672" (896x672:102.4Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1792x1344" (1792x1344:261.0Mhz): mode clock too high
(II) VIA(0): Rejected mode "896x672" (896x672:130.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1856x1392" (1856x1392:218.3Mhz): mode clock too high
(II) VIA(0): Rejected mode "928x696" (928x696:109.2Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1856x1392" (1856x1392:288.0Mhz): mode clock too high
(II) VIA(0): Rejected mode "928x696" (928x696:144.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1920x1440" (1920x1440:234.0Mhz): mode clock too high
(II) VIA(0): Rejected mode "960x720" (960x720:117.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1920x1440" (1920x1440:297.0Mhz): mode clock too high
(II) VIA(0): Rejected mode "960x720" (960x720:148.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "832x624" (832x624:57.3Mhz): hsync out of range
(II) VIA(0): Rejected mode "416x312" (416x312:28.6Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1280x768" (1280x768:80.1Mhz): hsync out of range
(II) VIA(0): Rejected mode "640x384" (640x384:40.1Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1280x800" (1280x800:83.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "640x400" (640x400:41.7Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1152x768" (1152x768:65.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "576x384" (576x384:32.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1152x864" (1152x864:121.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "576x432" (576x432:60.8Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1400x1050" (1400x1050:122.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "700x525" (704x525:61.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1400x1050" (1400x1050:151.0Mhz): hsync out of range
(II) VIA(0): Rejected mode "700x525" (704x525:75.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1400x1050" (1400x1050:155.8Mhz): horizontal sync too wide
(II) VIA(0): Rejected mode "700x525" (704x525:77.9Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1400x1050" (1400x1050:184.0Mhz): Memory bandwidth exceeded.
(II) VIA(0): Rejected mode "700x525" (704x525:92.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1440x900" (1440x900:108.8Mhz): horizontal sync too wide
(II) VIA(0): Rejected mode "720x450" (720x450:54.4Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1600x1024" (1600x1024:106.9Mhz): horizontal sync too narrow
(II) VIA(0): Rejected mode "800x512" (800x512:53.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1680x1050" (1680x1050:147.1Mhz): hsync out of range
(II) VIA(0): Rejected mode "840x525" (840x525:73.6Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1920x1200" (1920x1200:193.2Mhz): Memory bandwidth exceeded.
(II) VIA(0): Rejected mode "960x600" (960x600:96.6Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1920x1200" (1920x1200:230.0Mhz): mode clock too high
(II) VIA(0): Rejected mode "960x600" (960x600:115.0Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "1920x1440" (1920x1440:341.4Mhz): mode clock too high
(II) VIA(0): Rejected mode "960x720" (960x720:170.7Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "2048x1536" (2048x1536:266.9Mhz): mode clock too high
(II) VIA(0): Rejected mode "1024x768" (1024x768:133.5Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "2048x1536" (2048x1536:340.5Mhz): mode clock too high
(II) VIA(0): Rejected mode "1024x768" (1024x768:170.2Mhz): doublescan mode not supported
(II) VIA(0): Rejected mode "2048x1536" (2048x1536:388.0Mhz): mode clock too high
(II) VIA(0): Rejected mode "1024x768" (1024x768:194.0Mhz): doublescan mode not supported
(II) VIA(0): Validating Modes from Output "Panel - TTL Panel"
(II) VIA(0): Rejected mode "640x480" (640x480:23.5Mhz): hsync out of range
(II) VIA(0): Rejected mode "640x480" (640x480:23.8Mhz): hsync out of range
(EE) VIA(0): No valid modes found
(II) UnloadModule: "via"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```


I hope someone can give me some useful tips about this.

---

### Post by lost_knight on 2007-12-15
Hi, everybody!
I hope this is useful since I have an older laptop with the same VIA S3 Unichrome integrated video card ( VT8378 ). I've looked into getting it to work the best way possible and that's what I've come up with so far: 
Using the via drivers: xserver-xorg-video-via (from synaptic)
with a video section in my xorg.conf looking like this: 

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"     <-#uncommenting this makes the 3d effects work with direct rendering
	Load	"extmod"  #but after I exit the 3d application xserver goes bunkers.. better to  
	Load	"freetype" #have slower 3d
	Load	"glx"
	Load	"int10"
	Load	"vbe"
	Load    "synaptics"
EndSection

.
.
.

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"via"
	BusID		"PCI:1:0:0"
#	Option       	"EnableAGPDMA"
	Option 		"DisableIRQ"
EndSection

.
.
.

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

.
.
.

Section "DRI"
	Mode	0666
EndSection



This works fine for me. It's much better than vesa drivers, but is not good for handling heavier or even medium 3D.. If someone else has a better solution please post.

---

### Post by Vox754 on 2008-01-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/43154](https://bugs.launchpad.net/bugs/43154) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
> **GuruX said:**
> 
I hope someone can give me some useful tips about this.
				> **lost_knight said:**
> 
This works fine for me. It's much better than vesa drivers, but is not good for handling heavier or even medium 3D.. If someone else has a better solution please post.

Haven't you read all these posts? there is no definite solution.

> **PendragonUK said:**
> A lot of the budget laptops are VIA chipsets. **I have always found it strange that there isn't better support for VIA from the Linux community**, seeing how popular VIA is amongst the emerging markets around the world. You are not going to find too many American components in China for instance. 
WHAT?
It's the other way around, VIA doesn't support the Linux community.
The Linux community supports every single piece of hardware there is, provided the hardware manufacturers release useful specifications to create drivers.
The Linux Community cannot magically "support" a chipset if they know nothing about how it works. In the case of VIA there are some specifications but they are not enough.

And VIA is a Taiwanese company, so it makes sense to sell their products in China.

Anyway...

Sign the petition
[http://www.PetitionOnline.com/vialinux/](http://www.PetitionOnline.com/vialinux/)

---

