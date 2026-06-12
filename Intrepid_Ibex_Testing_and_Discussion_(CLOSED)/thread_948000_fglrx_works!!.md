---
title: "fglrx works!!"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bpl07 on 2008-10-14
Version 8.543 is in the queue:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/247376](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/247376)

---

### Post by rbmorse on 2008-10-14
Have you actually tried it? Does it really work?

---

### Post by bpl07 on 2008-10-14
> **rbmorse said:**
> Have you actually tried it? Does it really work?

Yup:

```
brad@ubuntu /home/brad> fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.8087 Release
```

---

### Post by inportb on 2008-10-14
w00t! I shall be installing that shortly; thanks for the heads-up.

Does anyone know anything about the status of Nvidia drivers? (I don't use Nvidia, but I know people who do.)

---

### Post by fbleagh on 2008-10-14
Which package should I install to try this ? xorg-driver-fglrx ??

---

### Post by bpl07 on 2008-10-14
> **fbleagh said:**
> Which package should I install to try this ? xorg-driver-fglrx ??

Install it through System>Administration>Hardware Drivers.  If it's not there, wait for updates to make it appear.

---

### Post by inportb on 2008-10-14
Yes. Then reboot.

It didn't work for me immediately. I had to run *kdesudo jockey-kde* and activate it there. For Gnome users: *gksudo jockey-gtk*

### EDIT ###
And that is what bpl07 is suggesting =p

---

### Post by fbleagh on 2008-10-14
This is what I get when I try to "aptitude install xorg-driver-fglrx"

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  xserver-xorg-core 
The following NEW packages will be installed:
  fglrx-amdcccle{a} fglrx-kernel-source{a} xorg-driver-fglrx 
0 packages upgraded, 3 newly installed, 0 to remove and 4 not upgraded.
Need to get 20.0MB of archives. After unpacking 54.6MB will be used.
The following packages have unmet dependencies:
  xserver-xorg-core: Conflicts: xserver-xorg-video-2 which is a virtual package.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
fglrx-amdcccle [Not Installed]
xorg-driver-fglrx [Not Installed]

Score is -9872

---

### Post by bpl07 on 2008-10-14
You should have waited and done it through hardware drivers, you probably didn't have the upgraded fglrx in your repo yet.

---

### Post by fbleagh on 2008-10-14
cool i'll leave it for a bit then :) I knew running aptitude -s was a good idea.

---

### Post by inportb on 2008-10-14
Hm... I like how performance has gone down the drain compared to the opensource drivers. But hey, support for the new Xorg interface is still new we're getting somewhere :)

---

### Post by Saint Angeles on 2008-10-14
i was running intrepid alpha until they upgraded xorg and i couldnt get any direct rendering going on... then i went through driver hell and could only load into a console no matter what i tried. luckily i was able to backup and reinstall hardy (which I'm using now).

If I do an upgrade again to intrepid at this point, will fglrx work? what else would i have to do to ensure i get direct rendering?

(i really don't wanna have to re-backup and install hardy yet again)

---

### Post by ktp on 2008-10-14
> **inportb said:**
> Hm... I like how performance has gone down the drain compared to the opensource drivers. But hey, support for the new Xorg interface is still new we're getting somewhere :)

I hear you...I also miss the video playback, which was working great with opensource driver.

---

### Post by rbmorse on 2008-10-15
All I did was a normal check for updates.  Restricted driver mangler (or whatever they call it now) popped up and announced that a restricted video driver for my card was available but not in use.  There was a button to use the restricted driver, which when selected began the download and install sequence.  When it was done, it told be I needed to reboot. Which, I did. 

The not-a-benchmark glxgears indicates about 10% lower performance compared to FGLRX on Hardy, but I can watch full screen video (XV) in VLC without tearing or other artifacts with CPU usage down around 12% on one core and nonimal on the other using my HD 3870. 

Just works!

---

### Post by inportb on 2008-10-15
> **ktp said:**
> I hear you...I also miss the video playback, which was working great with opensource driver.

EXA was awesome. Hm... fglrx overwrites some radeon files, so the way to get radeon back would be to remove fglrx and reinstall radeon. But I guess I'll stick with fglrx at least until 08.10.30 and make a decision then. Still, propz to AMD for releasing this driver, which would no doubt be very useful to many people :)

###  EDIT ###
Hmm weird... the atieventsd bug is back and it kept me from shutting down or reinitializing X properly until I removed it from the startup. It was fixed earlier, I remember.

---

### Post by bpl07 on 2008-10-15
For anyone looking for additional options for xorg.conf:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

---

### Post by inportb on 2008-10-15
Ooh, thanks for the awesome resource.

---

### Post by hardyn on 2008-10-15
has anybody, for giggles, tried the radeonHD driver?

---

### Post by mullenrbock on 2008-10-15
Hey, if under Hardware Drivers when I press "Activate" and a window pops up and says:

"Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid."

how do I work around that? It seems counterintuitive that a file that exists doesn't exist.

---

### Post by wgrant on 2008-10-15
> **mullenrbock said:**
> Hey, if under Hardware Drivers when I press "Activate" and a window pops up and says:

"Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid."

how do I work around that? It seems counterintuitive that a file that exists doesn't exist.

"is invalid" != "doesn't exist"

Rename your xorg.conf to something else and try again. Something in it is broken.

---

### Post by mullenrbock on 2008-10-15
> **wgrant said:**
> "is invalid" != "doesn't exist"

Rename your xorg.conf to something else and try again. Something in it is broken.

I just renamed it to "asdf.conf", still gives the same message. Should I uninstall/reinstall jockey?

---

### Post by wgrant on 2008-10-15
> **mullenrbock said:**
> I just renamed it to "asdf.conf", still gives the same message. Should I uninstall/reinstall jockey?

Try a 'sudo dpkg-reconfigure -phigh xserver-xorg'

---

### Post by mullenrbock on 2008-10-15
> **wgrant said:**
> Try a 'sudo dpkg-reconfigure -phigh xserver-xorg'

Still the same error...

---

### Post by bobnutfield on 2008-10-15
Just installled...works with only a minimal improvement.  Lost X temporarily but it was restored on a reboot.  I, like a previous poster, will continue to work with it until the final release and decide whether to keep it or restore the open source driver.  I don't usually mess with xorg.conf too much, and I only use compiz when demonstrating to possible Windows converts, so it is not much of an issue to me.

---

### Post by mick222 on 2008-10-15
The open source driver has been working great for me,Radeon 9600 amd athlon 64 3400+ 512mb ram 80gig hdd.
I think i'll leave fglrx for now , it always had problems in Hardy. Compiz runs great even with the sphere emerald and lots of bells and whistles , i cant freeze this comp

---

### Post by pressureman on 2008-10-15
Is anyone seeing errors like the following when fglrx loads?

```

fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 430 MBytes.
[fglrx:drm_alloc] *ERROR* [driver] Allocating 0 bytes
[fglrx:firegl_init_device_list] *ERROR* Out of memory when allocating device heads
[fglrx:firegl_init_module] *ERROR* firegl_init_devices failed

```

X doesn't start, since the fglrx xorg driver fails to load. Even if I just try to manually modprobe fglrx kernel module, the above error occurs.

---

### Post by hardhu on 2008-10-15
> **inportb said:**
> Hm... I like how performance has gone down the drain compared to the opensource drivers. But hey, support for the new Xorg interface is still new we're getting somewhere :)

I have an Ati Mobility Radeon X700, and I tried to play a an xvid encoded movie with totem, but performance was poor compared with radeon driver, so I switched back to it. Has anybody experienced the same symptoms?

---

### Post by double1116 on 2008-10-15
> **pressureman said:**
> Is anyone seeing errors like the following when fglrx loads?

```

fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 430 MBytes.
[fglrx:drm_alloc] *ERROR* [driver] Allocating 0 bytes
[fglrx:firegl_init_device_list] *ERROR* Out of memory when allocating device heads
[fglrx:firegl_init_module] *ERROR* firegl_init_devices failed

```

X doesn't start, since the fglrx xorg driver fails to load. Even if I just try to manually modprobe fglrx kernel module, the above error occurs.

Yes, I am seeing the exact same thing. I did not find a solution either :(

---

### Post by rbmorse on 2008-10-15
> **hardyn said:**
> has anybody, for giggles, tried the radeonHD driver?

I've been using it since Intrepid Alpha1 with my HD 3870 as the Radeon driver doesn't work with that card, for some reason (my be a config error on my end, but I quit worrying about it when the radeonhd worked. 

No 3D, 2D or video hardware acceleration, of course because of my hardware (R680), but it was fast and stable for me otherwise.

---

### Post by biasquez on 2008-10-15
> **pressureman said:**
> Is anyone seeing errors like the following when fglrx loads?

```

fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 430 MBytes.
[fglrx:drm_alloc] *ERROR* [driver] Allocating 0 bytes
[fglrx:firegl_init_device_list] *ERROR* Out of memory when allocating device heads
[fglrx:firegl_init_module] *ERROR* firegl_init_devices failed

```

X doesn't start, since the fglrx xorg driver fails to load. Even if I just try to manually modprobe fglrx kernel module, the above error occurs.


i have same error

---

### Post by marmuta on 2008-10-15
> **hardhu said:**
> I have an Ati Mobility Radeon X700, and I tried to play a an xvid encoded movie with totem, but performance was poor compared with radeon driver, so I switched back to it. Has anybody experienced the same symptoms?

Had that too with a Radeon X800 because XVideo isn't enabled by default. You have to add either

Option "VideoOverlay" "on"
or 
Option "TexturedVideo" "on"

to the device section of your xorg.conf.

With these cpu usage is down, but to actually watch video you would probably have to use metacity. For me with compiz, the former only shows a faint blue glow where the video should be, and the latter flickers wildly and always paints on top of all windows.

Apart from that everything seems good. Virtual consoles and suspend to RAM work, flash videos, scrolling and resizing in compiz are clearly faster than with os radeon. It just utterly fails to play video in compiz...

Oh well, back to the open source radeon driver I guess. It just works (if a bit sluggishly).

---

### Post by biasquez on 2008-10-15
i have this error installing catalyst 8.10 downloaded from ati website

make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.542/build modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /var/lib/dkms/fglrx/8.542/build/firegl_public.o
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function ‘__ke_printk’:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:1915: warning: format not a string literal and no format arguments
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function ‘__ke_vm_phys_addr_str’:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:3522: warning: return makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:3523: warning: return makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:3524: warning: return makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:3526: warning: return makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function ‘KCL_enable_pat’:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:4063: error: too many arguments to function ‘smp_call_function’
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function ‘KCL_disable_pat’:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:4082: error: too many arguments to function ‘smp_call_function’
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: At top level:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:5774: warning: initialization from incompatible pointer type
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:5800: warning: initialization from incompatible pointer type
make[2]: *** [/var/lib/dkms/fglrx/8.542/build/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.542/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [kmod_build] Error 2

---

### Post by bpl07 on 2008-10-15
From your output the version you have is 8.542.  Since the version in ubuntu is 8.543, it makes me think that the ubuntu version is patched to work with xorg 7.4 and xserver 1.5.  I would use the ubuntu package if I were you.

---

### Post by wingsuit on 2008-10-15
i have a problem - restricted drivers manager appeared and it does contain FGLRX driver, but when I press Activate, it shows progressbar with 0% for a couple of seconds and nothing more, driver is still disabled.

internet connection is ok, xorg-driver-fglrx package is installed

tried also running jockey-gtk from terminal to see if it shows any error messages, nothing.

```
root@erik-desktop:~# jockey-gtk -l
xorg:fglrx - ATI/AMD proprietary FGLRX graphics driver (Proprietary, Disabled, Not in use)
root@erik-desktop:~# jockey-gtk -e xorg:fglrx
root@erik-desktop:~# jockey-gtk -l
xorg:fglrx - ATI/AMD proprietary FGLRX graphics driver (Proprietary, Disabled, Not in use)
```

any ideas?

---

### Post by rbmorse on 2008-10-15
When I did it, the progress bar sat at zero for a LONG time before it suddenly jumped to 50%, where it sat again for a LONG time before completing. Might want to try again, and let it cook longer.

---

### Post by wingsuit on 2008-10-15
I've tryed itnumerous times :(

it just shows progress bar for couple of seconds and then it disapears without me klicking anywhere...

---

### Post by grigio on 2008-10-15
when you say "it works", could you please specify your video card?
What about Video Flickering with Compiz?

---

### Post by wingsuit on 2008-10-15
> **wingsuit said:**
> I've tryed itnumerous times :(

it just shows progress bar for couple of seconds and then it disapears without me klicking anywhere...

ok, got it fixed.

all it took was to install linux-headers-generic package and it took care of creating kernel module in post-install.

a bit strange for me is, that i do have build-essential package installed, shouldn't that be dependent of headers package?

---

### Post by Markuz Nightwind on 2008-10-15
Works fine here, except for the performances :|
Since i upgraded from the old 8.9 catalyst @ hardy i lost almost 4/5 performance wise. Hope it can get better with time cause at the moment on my old x1650pro it's almost unplayable (even 6-7 years old games like Diablo II/Warcraft III under wine) while before with 8.9 I was getting good framerates :|

---

### Post by night-wing on 2008-10-16
To me, it worked fine. Also powerdvd (linux) plays without problems.

Ok. The installation program of the driver (hardware drivers) freezed three times, till it managed to download & install the driver. But now... fine ... also with compiz.

---

### Post by steino on 2008-10-16
Two thumbs up to the devs for patching fglrx so that it works with the new xorg ABI. I'm real happy for those of you who got the drivers to work =) I'm not getting any fglrx love (horrible 2D acceleration and no 3D) =(

fglrxinfo:
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  159 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

I really was looking forward to the latest version of fglrx as the radeon driver results in decent 2D, but no compiz =/ (OpenGL Direct Rendering works, but 3D Acceleration doesn't?). And radeonhd results in epic fail (no device detected). I didn't expect my card, a 4870, to be fully supported in the open source alternative. I did expect partial support, basic 3D and compiz, as both drivers (radeon and radeonhd) now use AtomBIOS.

---

### Post by Gaat on 2008-10-16
For steino : My card is an ATI HD4870 and it works fine with the latest update of the fglrx packages (and worked also with the radeonhd driver, git version). Try to purge all packages related to fglrx then install them again.

Good luck

PS. Compiz works too.

---

### Post by Odur on 2008-10-16
> **Gaat said:**
> For steino : My card is an ATI HD4870 and it works fine with the latest update of the fglrx packages (and worked also with the radeonhd driver, git version). Try to purge all packages related to fglrx then install them again.

Good luck

PS. Compiz works too.
Can you (or someone else) please try to switch user and see if X freezes. Don't log out, just switch.
See _[this post]("http://ubuntuforums.org/showpost.php?p=5974770&postcount=2")_ for more information.

---

### Post by wingsuit on 2008-10-16
> **Odur said:**
> Can you (or someone else) please try to switch user and see if X freezes. Don't log out, just switch.
See _[this post]("http://ubuntuforums.org/showpost.php?p=5974770&postcount=2")_ for more information.

Works like a charm, no problem whatsoever.

ATI Technologies Inc RV505 CE [Radeon X1550 64-bit]
fglrx 8.54.3

---

### Post by sdowney717 on 2008-10-16
> 
when you say "it works", could you please specify your video card?
What about Video Flickering with Compiz?


yes it will so set the video output module to use x11, NOT xv.

---

### Post by Odur on 2008-10-16
> **wingsuit said:**
> 
[QUOTE=Odur;5975283]Can you (or someone else) please try to switch user and see if X freezes. Don't log out, just switch.
See _[this post]("http://ubuntuforums.org/showpost.php?p=5974770&postcount=2")_ for more information.
Works like a charm, no problem whatsoever.
ATI Technologies Inc RV505 CE [Radeon X1550 64-bit]
fglrx 8.54.3[/QUOTE]

Thanks for testing, not that suprisingly though. It first happend to me when my old X600 was fried and I bought a HD3870.
Anyone with a HD24xx or above (R600 and up) who care to test?

---

### Post by screaminj3sus on 2008-10-16
wewt :)

works perfectly on the 2600 in my laptop.

---

### Post by eyelessfade on 2008-10-16
Interesting since ATI don't specify xorg 7.4 at all.
8.10 - Oct. 15, 2008 - Automated installer and Display Drivers for X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3.

If it works, yey! I can finaly upgrade my laptop

---

### Post by double1116 on 2008-10-16
> **eyelessfade said:**
> Interesting since ATI don't specify xorg 7.4 at all.
8.10 - Oct. 15, 2008 - Automated installer and Display Drivers for X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3.

If it works, yey! I can finaly upgrade my laptop

The Ubuntu 8.10 version is actually ATI Catalyst 8.11, which won't be released by ATI to the public until November. See [http://www.phoronix.com/vr.php?view=12957](http://www.phoronix.com/vr.php?view=12957) for some info.

---

### Post by eyelessfade on 2008-10-16
Interesting a beta driver. As long as it works I'll be happy.

---

### Post by sdowney717 on 2008-10-16
beta Ibex and beta FGLRX, it fits.
ATI had to do something about it eventually. Best to do it with a beta Ibex than a final release.

---

### Post by [S]Duke on 2008-10-17
Is anyone else having trouble with videos? I'm on a 2600 Radeon HD, with the fglrx driver, everything works fine, except videos. They seem to freeze for like half a second, creating some kind of "flicker".

I have tried both TexturedVideo and Video Overlay, with OpenGLOverlay off. I'm using mplayer and telling it to use X11 instead of XV (XV crashed the system under Textured Video and didn't work under Video Overlay).

Is there any fix to this?

---

### Post by sdowney717 on 2008-10-17
how does VLC work for you?
I found mplayer lately to be glitchy and VLC smooth.
It could be a codec issue.

---

### Post by Tares on 2008-10-17
I've installed fglrx from repos, but I have crappy performance on my HD4850. Q3 gets like 70 fps ;/

I've found something interesing, my CCC reports that OpenGL is in mesa mode :
[[IMG]http://img220.imageshack.us/img220/4561/cccgc5.th.png[/IMG]](http://img220.imageshack.us/my.php?image=cccgc5.png)[[IMG]http://img220.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)
It's in polish, but I've marked the most important thing.

Anyway fglrxinfo says :
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 1.4 (2.1.8087 Release)

```

---

### Post by sdowney717 on 2008-10-17
here is mine showing it working on an x1300

what are the 'EE' errors in /var/log/xorg log?

---

### Post by Tares on 2008-10-17
> **sdowney717 said:**
> here is mine showing it working on an x1300

what are the 'EE' errors in /var/log/xorg log?

Nothing special :
```

cat /var/log/Xorg.0.log | grep EE

	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Failed to load module "dcc" (module does not exist, 0)
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load module "type1" (module does not exist, 0)

```

---

### Post by sdowney717 on 2008-10-17
I just got another fglrx update and read this on fglrx
I wonder if perhaps your card is not officially supported yet for this beta driver??

Video driver for the ATI Radeon and FireGL graphics accelerators.
This version of the ATI driver officially supports:
* RADEON X1300, X1600, X1800, X1900
* RADEON 8500, 9000, 9100, 9200, 9500, 9550, 9600, 9700, 9800
* RADEON X800, X700, X600, X550, X300 series (AGP and PCI Express)
* MOBILITY RADEON 9000, 9200, 9600, 9800, X700
* MOBILITY RADEON 9000/9100 IGP Series
* FireGL 8700, 8800, E1, E2, X1, X2, X3, Z1, T2
* MOBILITY FireGL 9100, T2
* RADEON XPRESS 200
This package provides 2D display drivers and hardware accelerated OpenGL.

---

### Post by hardhu on 2008-10-19
> **'[S]Duke said:**
> Is anyone else having trouble with videos? I'm on a 2600 Radeon HD, with the fglrx driver, everything works fine, except videos. They seem to freeze for like half a second, creating some kind of "flicker".

I have tried both TexturedVideo and Video Overlay, with OpenGLOverlay off. I'm using mplayer and telling it to use X11 instead of XV (XV crashed the system under Textured Video and didn't work under Video Overlay).

Is there any fix to this?

I have also similar symptoms: my video card is an Ati Mobility Radeon X700, and when I try to play videos (actually I tried only with xvid encoded movies) they play jerkily. 
I have then added the line   Option "VideoOverlay" "on" in xorg.conf, but in that case I can only listen to audio track of movies, and there's no video output at all.

---

### Post by hardhu on 2008-10-19
> **sdowney717 said:**
> yes it will so set the video output module to use x11, NOT xv.


May I ask you what do you mean exactly to "set the video output module to use x11, NOT xv"? Is this a configuration I can do adding some lines in xorg.conf to see if I can solve my problems?

---

### Post by hardhu on 2008-10-19
> **marmuta said:**
> Had that too with a Radeon X800 because XVideo isn't enabled by default. You have to add either

Option "VideoOverlay" "on"
or 
Option "TexturedVideo" "on"

to the device section of your xorg.conf.

With these cpu usage is down, but to actually watch video you would probably have to use metacity. For me with compiz, the former only shows a faint blue glow where the video should be, and the latter flickers wildly and always paints on top of all windows.


I have in fact the same problems as you described (no video output with VideoOverlay on, and video flickering with TexturedVideo on) but not only with Compiz, also with kde 4 and desktop effects enabled.

---

### Post by aamukahvi on 2008-10-19
> **hardhu said:**
> I have in fact the same problems as you described (no video output with VideoOverlay on, and video flickering with TexturedVideo on) but not only with Compiz, also with kde 4 and desktop effects enabled.
They both use Composite so that's why.

---

### Post by Mozai on 2008-10-19
Still busted here.  I'd rather not downgrade back to hardy.  I guess this is what beta testing is all about.

> root@jomi:~# lspci |grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
root@jomi:~# modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.27-7-generic/updates/dkms/fglrx.ko): Cannot allocate memory
[60341.391889] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[60341.497330] [fglrx] Maximum main memory to use for locked dma buffers: 926 MBytes.
[60341.498571] [fglrx:drm_alloc] *ERROR* [driver] Allocating 0 bytes
[60341.498584] [fglrx:firegl_init_device_list] *ERROR* Out of memory when allocating device heads
[60341.498595] [fglrx:firegl_init_module] *ERROR* firegl_init_devices failed


---

### Post by marmuta on 2008-10-19
@hardhu: xv is the xservers XVideo extension which does color-space conversion and scaling with the video hardware.
x11 is an alternative way to display video that has to do everything in software which makes it cpu intensive. 

Most video players try xv first and failing that fall back to x11 automatically. So to get x11 either configure all your players individually to use it or just disable xv altogether by removing the Options TexturedVideo and VideoOverlay from xorg.conf. That's right, back where you started with high cpu use...

The disappearing and flickering video actually turned out to be wellknown fglrx problems. I'm not sure if compiz could or should work around it, most likely only ATI can fix them for good. After all the opensource driver does video just fine. 
The Ubuntu devs are apparently choosing the lesser of two evils with disabling xv by default. 

Some (slightly depressing) reading material:
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/197639](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/197639)
[http://ati.cchtml.com/show_bug.cgi?id=875](http://ati.cchtml.com/show_bug.cgi?id=875)
[http://ati.cchtml.com/show_bug.cgi?id=887](http://ati.cchtml.com/show_bug.cgi?id=887)
[http://www.phoronix.com/forums/showthread.php?t=13218](http://www.phoronix.com/forums/showthread.php?t=13218)

---

