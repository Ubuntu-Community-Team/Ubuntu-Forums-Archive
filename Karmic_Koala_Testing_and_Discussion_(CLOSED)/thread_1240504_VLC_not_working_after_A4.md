---
title: "VLC not working after A4"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jackhynes on 2009-08-14
I'm getting this:
```
libvlc2: Depends: libvlccore2 (>= 1.0.0~rc1) but it is not installed
E: Unmet dependencies. Try using -f.

```
after the latest update to alpha 4, can't seem to get audio or video to work. Should I just wait for more updates to be pushed out or is there a fix?

---

### Post by wayne_cat on 2009-08-14
> **jackhynes said:**
> I'm getting this:
```
libvlc2: Depends: libvlccore2 (>= 1.0.0~rc1) but it is not installed
E: Unmet dependencies. Try using -f.

```after the latest update to alpha 4, can't seem to get audio or video to work. Should I just wait for more updates to be pushed out or is there a fix?

you need this package

```
root@macbook:~# dpkg -l |grep libvlccore2
ii  libvlccore2                                    1.0.1-1ubuntu1                             base library for VLC and its modules
root@macbook:~# 

```try this:

```
sudo apt-get install -f
```

---

### Post by jackhynes on 2009-08-14
> **wayne_cat said:**
> you need this package

```
root@macbook:~# dpkg -l |grep libvlccore2
ii  libvlccore2                                    1.0.1-1ubuntu1                             base library for VLC and its modules
root@macbook:~# 

```try this:

```
sudo apt-get install -f
```

Now I get:
```
Unpacking libvlccore2 (from .../libvlccore2_1.0.1-1ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libvlccore2_1.0.1-1ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libvlccore.so.2.0.0', which is also in package libvlccore0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libvlccore2_1.0.1-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ronacc on 2009-08-14
try using the dpkg --force option to install it , or you could rename the existing /usr/lib/libvlccore.so.2.0.0 to something else and run wayne_cat's cmd again . Its ok here on amd64 so mabye its a problem with the 386 deb.

---

### Post by jocko on 2009-08-15
> **jackhynes said:**
> Now I get:
```
Unpacking libvlccore2 (from .../libvlccore2_1.0.1-1ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libvlccore2_1.0.1-1ubuntu1_i386.deb (--unpack):
[COLOR=Red] trying to overwrite `/usr/lib/libvlccore.so.2.0.0', which is also in package libvlccore0[/COLOR]
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libvlccore2_1.0.1-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Uninstall the package libvlccore0. It's for an older version of vlc.

---

### Post by jackhynes on 2009-08-15
> **jocko said:**
> Uninstall the package libvlccore0. It's for an older version of vlc.

Thanks all for the help. I couldn't uninstall libvlccore0 and renaming the files in /usr/lib/ didn't make a difference. I fixed the problem in the end by doing:
```
sudo apt-get remove vlc-nox vlc libvlc2 sopcast-player
```

---

### Post by jackhynes on 2009-08-15
Okay now the problem I'm having is with playing videos. VLC just says:
```
no suitable decoder module for fourcc `XVID'.
VLC probably does not support this sound or video format.
```
It's the same with other codecs. Which packages do I need to get videos working again?

---

### Post by jocko on 2009-08-15
> **jackhynes said:**
> Okay now the problem I'm having is with playing videos. VLC just says:
```
no suitable decoder module for fourcc `XVID'.
VLC probably does not support this sound or video format.
```It's the same with other codecs. Which packages do I need to get videos working again?
As far as I can see, many codecs are in the vlc-nox package (which is the package that contains the actual vlc binary), and all others are listed as dependencies for that package. 

A few non-free codecs are available if you install ubuntu-restricted-extras (which will replace a few stripped down codec packs with complete versions).

But if vlc can't play xvid, you must have done something to some library file which causes vlc to malfunction. xvid support is part of the standard codecs that are installed with vlc.
Try to search synaptic for vlc (search just for name, not name and description), mark all installed packages for complete removal and apply.
If you have renamed any of the files as someone suggested in an earlier post, you must make sure you delete those files, to make sure there is nothing left of your broken vlc install.
Also check that there is no old package related to vlc in the "uninstalled but remaining configuration" category in synaptic.

Once that's done, reinstall vlc and keep your fingers crossed.

---

### Post by jackhynes on 2009-08-15
Yeah I did mess with the config files. Did a complete removal of vlc, vlc-nox, vlc-data, libvlccore2, libvlc2 in Synaptic, then reinstalled everything. Still having the same problem though. How do I get the original config files back?

---

### Post by blakamin on 2009-09-09
Having these issues too... did you get it working?
EDIT: nevermind... installed libavcodec

---

### Post by wfp on 2009-09-11
Vlc Crashing on startup. Error output messages from terminal. 
VLC media player 1.0.1 Goldeneye
[0xb0d0a8] main interface error: no interface module matched "globalhotkeys,none"
[0xb0d0a8] main interface error: no suitable interface module
[0xb0c888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0xb0c888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

---

### Post by mc4man on 2009-09-11
@ wfp
More often than not when vlc segfaults it's due to an audio and or video output issue, though if you upgraded from 8.10 you could possibly include the existing config and cache files.

the line about global hotkeys would be expected if vlc was built in the absence of libxcb-keysyms0-dev or run without libxcb-keysyms0 installed.
( it **appears** the packager for the karmic vlc didn't enable globalhotkeys by including libxcb-keysyms0-dev in the build-deps - saying appears due to being on hardy, would need to ck. to confirm

The package vlc-plugin-pulse  has been removed as an install dep, you may want to try installing it.

To get a more useful debug use ```
vlc -vv
``` 

To reset the rc and plugins cache use 
```
vlc --reset-config --reset-plugins-cache
```

or delete manually the vlc folders in 
~/.config and ~/.cache

---

### Post by wfp on 2009-09-11
Thanks.

---

### Post by blakamin on 2009-09-11
Having the same issue now on a fresh install

```
VLC media player 1.0.1 Goldeneye
[0x9a4b200] main interface error: no interface module matched "globalhotkeys,none"
[0x9a4b200] main interface error: no suitable interface module
[0x9932140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x9932140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 133.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  133 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  103
  Current serial number in output stream:  104
```


Any ideas?

---

### Post by mc4man on 2009-09-12
@ blakamin
With these type issues it's good to post what your display adapter is and what drivers are in use ( if any

If you don't know these can help
```
sudo lshw -C display
```

and this (only first 5 lines are important atm
```
glxinfo
```

Anyway you could try changing your video output and possibly even your audio output ( audio can cause a video error

For vlc go tools -> preferences, click on the video icon and and in the output box change from default to X11 video output. Click save or enter on keyboard, and try vlc again. You could experiment with the same for audio.

To reset to defaults click the button and save or run above posted commands in previous post

There are also some extended settings for video output avail., I'd find/post/search based on your video adapter and driver info first if the above is to no avail.

---

### Post by blakamin on 2009-09-12
thanks mc4man


outputs

```
  *-display               
       description: VGA compatible controller
       product: C67 [GeForce 7000M / nForce 610M]
       vendor: nVidia Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:23 memory:f3000000-f3ffffff memory:d0000000-dfffffff(prefetchable) memory:f2000000-f2ffffff memory:40000000-4001ffff(prefetchable)
```

and

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
```


> For vlc go tools -> preferences, click on the video icon and and in the output box change from default to X11 video output. Click save or enter on keyboard, and try vlc again. You could experiment with the same for audio.

That didn't work either, but I'm trying everything!

---

### Post by andreya on 2009-10-21
I have the same problem ;(

Have you found any solution?

Thanks.

More info:

Rendering with XVideo results:

```

VLC media player 1.0.2 Goldeneye
[????????] x11 video output error: X11 request 133.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  133 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  101
  Current serial number in output stream:  102
```

Rendering with X11:
```

[????????] x11 video output error: X11 request 142.3 failed with error code 8:
 BadMatch (invalid parameter attributes)
[????????] x11 video output notice: buggy X11 server claims shared memory
[????????] x11 video output notice: support though it does not work (OpenSSH?)
[????????] x11 video output error: X11 request 142.3 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  142 (MIT-SHM)
  Minor opcode of failed request:  3 (X_ShmPutImage)
  Serial number of failed request:  61
  Current serial number in output stream:  62
```

glxinfo:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
```

lshw -C display:
```
  *-display               
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
```

System: the latest up-to-date karmic from the repository.

The bug persists since upgrade to karmic (some alpha).

---

### Post by mc4man on 2009-10-21
I've got a 8400m which, while a fairly average card at best, works fine, both in hardy and karmic with any of the possible video outputs. (though I prefer Xv
The info displayed is quite similar to yours
> *-display               
       description: VGA compatible controller
       product: G86 [GeForce 8400M GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:e0000000-efffffff(prefetchable) memory:fa000000-fbffffff ioport:ef00(size=128) memory:fc000000-fc01ffff(prefetchable)


( not a factor but is interesting I have a 8400 reported as G86 and you have a 8600 as G84

Anyway you should be able to use any available output, you could try OpenGl though Xv should work
For this laptop I'm using the repo 185 drivers.

> The bug persists since upgrade to karmic

Did you upgrade or do a fresh install?



If no solution arises you could test from a livecd and see if the Xv works there ( better if you have 2Gb or more memory

(if you don't have a beta livecd then burn a daily build
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

While the nvidia drivers may be on the livecd I'd use the repo ones

To do so
After booting up to live cd enable internet access. Then go to software sources and disable the cdrom source and enable all the 'Ubuntu Software' sources, close and reload.

After that install just the restricted drivers,( don't run an update), it will say you need to restart, but don't. Instead log out and back in again, the drivers will be loaded. Then install and test vlc (install libdvdcss2 also if using a commercial dvd.

(if you try this don't use a username or password when booting into livecd, just press enter

---

### Post by nanog on 2009-10-21
Did you try installing (or reinstalling:

```

```$ dpkg -l | grep libavcodec
ii  libavcodec-extra-52                        4:0.5+svn20090706-2ubuntu3                               ffmpeg codec library

---

### Post by andreya on 2009-10-22
Thanks for the reply.

I upgraded to karmic by means of gnome-updater, not fresh install. And before it I also upgraded to jaunty in the same way.

Right now I've finished trying your experiment with boot cd.
But unfortunately I've failed to complete it.
The thing is my internet connection is via PPTP or L2TP based gateway and I found no way to activate it from boot cd. 
NetworkManager shows no available VPN connections.
And pptp-linux client says that the kernel has no MMPE support built in. 
It seems that current daily build is very unstable, I even failed to start gedit, it caused core dumped. And error reporter many times said that modprobe was terminated.

I think I'll make fresh install right after Karmic release will be available.

ps: currently vlc is playing video only via OpenGL. X11 and Xvideo both come to crash.

---

