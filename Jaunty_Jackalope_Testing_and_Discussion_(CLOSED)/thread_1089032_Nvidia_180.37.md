---
title: "Nvidia 180.37"
date: 2009-03-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-03-06
The goodness :popcorn:

Release Highlights:

    * Fixed a problem that caused signals to be blocked in some applications.
    * Fixed a problem that could cause Xid errors and display corruption in certain cases when OpenGL is used to render to redirected windows, for example when Java2D is used with the -Dsun.java2d.opengl=true option.
    * glGetStringi(GL_EXTENSIONS, i) no longer returns NULL in OpenGL 3.0 preview contexts.
    * Fixed a problem that caused the screen to flicker momentarily when OpenGL applications exit unexpectedly on GeForce 6 and 7 series GPUs.
    * Fixed an X server crash when an X client attempts to draw trapezoids and RenderAccel is disabled.
    * Improved recovery from certain types of errors.
    * VDPAU updates:
          o Fixed corruption on some H.264 clips.
          o Update documentation.
          o Fixed VC-1 decoding on 64-bit platforms.
          o Improved handling of invalid H.264 streams.
          o Fixed a problem that caused surfaces to be marked as visible too early when the blit presentation queue is in use.

The 180.37 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86 is available for download via FTP.
The 180.37 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86-64 is available for download via FTP.

Please see the README (x86, x86-64) for more information about this release.

Please note: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.

Please also note: If you encounter any problems with the 180.37 NVIDIA Linux graphics driver release, please start a new thread and include a detailed description of the problem, reproduction steps and generate/attach an nvidia-bug-report.log file (please see [http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678) for details).

---

### Post by ronacc on 2009-03-06
link please ,I'm not seeing it .

---

### Post by taavikko on 2009-03-06
> **ronacc said:**
> link please ,I'm not seeing it .

[http://www.nvnews.net/vbulletin/showthread.php?p=1951107](http://www.nvnews.net/vbulletin/showthread.php?p=1951107)

If you were referring to DL, [ftp://download.nvidia.com/XFree86/](ftp://download.nvidia.com/XFree86/)

Edit: FFe filed yet?

---

### Post by ronacc on 2009-03-06
I was looking for the d/l , thanks .

---

### Post by Nullack on 2009-03-07
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/339065](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/339065)

---

### Post by plun on 2009-03-07
Well, this "goodness" works just fine....:D


I need reference files for HD stuff... I lost my pirated stuff when I blow up my disk...:D

---

### Post by damis648 on 2009-03-07
Check out [this repo]("https://launchpad.net/~anders-kaseorg/+archive/ppa"), keeps the 180 driver easily managed with the drivers manager. Just install the modaliases and the kernel source, and reboot and install in the restricted drivers manager.

---

### Post by kurros on 2009-03-07
> **Nullack said:**
> 
* Fixed a problem that could cause Xid errors and display corruption in certain cases when OpenGL is used to render to redirected windows, for example when Java2D is used with the -Dsun.java2d.opengl=true option.
    

Yes! Finally!

---

### Post by taavikko on 2009-03-07
> **kurros said:**
> Yes! Finally!

This probably means that we can try 
[http://java.com/en/download/help/testvm.xml](http://java.com/en/download/help/testvm.xml)
again?

WARNING, after test my session seems to explode...

---

### Post by Nullack on 2009-03-07
> **taavikko said:**
> This probably means that we can try 
[http://java.com/en/download/help/testvm.xml](http://java.com/en/download/help/testvm.xml)
again?

WARNING, after test my session seems to explode...

Works fine for me using Sun JRE 6 U 12 and the Sun web plugin

---

### Post by taavikko on 2009-03-07
> **Nullack said:**
> Works fine for me using Sun JRE 6 U 12 and the Sun web plugin

yeap, the dancing duke whirls around the box, but after closing, my screen goes haywire... (x86_64)

Haven't tried to debug yet what causes it...

---

### Post by Sockerdrickan on 2009-03-07
I'm trying to learn how to write games using "pure" OpenGL 3.0 and I'm having a lot of problems due to lack of examples etc, anyone have a good link or two?

---

### Post by paul_in_london on 2009-03-08
Problems for me with the upgrade from 180.35 to 180.37.

Does anyone else have a conflict between xserver-xorg-core and v180.37 of nvidia-glx-180?

paul@jaunty-sdb:~$ sudo aptitude full-upgrade 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Reading extended state information      
Initialising package states... Done 
The following packages are BROKEN: 
  mplayer xserver-xorg-core 
The following packages will be upgraded: 
  nvidia-glx-180 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
Need to get 13.8MB of archives. After unpacking 1200kB will be used. 
The following packages have unmet dependencies: 
  mplayer: Depends: libamrnb3 which is a virtual package. 
           Depends: libamrwb3 which is a virtual package. 
           Depends: libartsc0 (>= 1.5.9) but it is not installable 
  xserver-xorg-core: Conflicts: xserver-xorg-video-4 which is a virtual package.

One of the initial things I tried to fix the broken package xserver-xorg-core was:

sudo dpkg -P --force-depends  xserver-xorg-core
sudo aptitude install xserver-xorg-core

I also tried purging 180.35 and then installing 180.37.

Still no good.

So then I looked at the entries in /var/lib/dpkg/status:

> Package: nvidia-glx-180 
Status: install ok installed 
Priority: optional 
Section: restricted/misc 
Installed-Size: 26176 
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com> 
Architecture: i386 
Source: nvidia-graphics-drivers-180 
Version: 180.35-0ubuntu1 
Replaces: nvidia-glx, nvidia-glx-173, nvidia-glx-177, nvidia-glx-180, nvidia-glx-71, nvidia-glx-96, nvidia-glx-envy, nvidia-glx-legacy, nvidia-glx-legacy-envy, nvidia-glx-new, nvidia-glx-new-envy, nvidia-glx-src 
Provides: nvidia-glx, xserver-xorg-video-5 
Depends: nvidia-180-kernel-source (>= 180.35), nvidia-180-libvdpau (>= 180.35), x11-common (>= 1:7.0.0), libc6 (>= 2.3.6-6~), libgcc1 (>= 1:4.1.1), libgl1-mesa | libgl1, libx11-6, libxext6, zlib1g (>= 1:1.1.4) 
Recommends: nvidia-settings 
Conflicts: nvidia-glx, nvidia-glx-src, xorg-driver-fglrx 

Package: xserver-xorg-core 
Status: install ok installed 
Priority: optional 
Section: x11 
Installed-Size: 4284 
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com> 
Architecture: i386 
Source: xorg-server 
Version: 2:1.6.0-0ubuntu1 
Replaces: xserver-common (<< 7), xserver-xfree86 (<< 1:7.0.0), xserver-xorg (<< 6.8.2-38) 
Provides: xserver 
Depends: xserver-common (>> 7), libc6 (>= 2.7), libdbus-1-3 (>= 1.0.2), libdrm2 (>= 2.3.1), libfontenc1, libgcc1 (>= 1:4.1.1), libhal1 (>= 0.5.8.1), libpciaccess0, libpixman-1-0 (>= 0.13.2), libssl0.9.8 (>= 0.9.8f-5), libxau6, libxdmcp6, libxfont1 (>= 1:1.2.9), xserver-xorg 
Recommends: xkb-data, xfonts-base, libgl1-mesa-dri (>= 7.1~rc1) 
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-scalable 
Breaks: xserver-xorg-input-evdev (<= 1:2.0.99+git20080912-0ubuntu2), xserver-xorg-input-synaptics (<= 0.15.2-0ubuntu3) 
Conflicts: xserver-common (<< 7), xserver-xfree86 (<< 1:7.0.0), xserver-xorg (<< 6.8.2-38), xserver-xorg-input, xserver-xorg-input-2, xserver-xorg-input-2.1, xserver-xorg-input-wacom (<< 0.7.8), xserver-xorg-video, xserver-xorg-video-1.0, xserver-xorg-video-1.9, xserver-xorg-video-2, xserver-xorg-video-4, xserver-xorg-video-psb (<< 0.15.0-0ubuntu1~804um5) 
Conffiles: 
 /etc/dbus-1/system.d/xorg-server.conf 70413875eaeca87b503c4445532ac231 


Backed up /var/lib/dpkg/status

Removed xserver-xorg-video-4 from conflict list of xserver-xorg-core (there were no other references to xserver-xorg-video-4 within /var/lib/dpkg/status, but many references to xserver-xorg-video-5).

It doesn't solve the underlying problem, but at least I was then able to force the upgrade to v180.37.

Now in /var/lib/dpkg/status:

> Package: nvidia-glx-180 
Status: install ok installed 
Priority: optional 
Section: restricted/misc 
Installed-Size: 26036 
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com> 
Architecture: i386 
Source: nvidia-graphics-drivers-180 
Version: 180.37-0ubuntu0 
Replaces: nvidia-glx, nvidia-glx-173, nvidia-glx-177, nvidia-glx-180, nvidia-glx-71, nvidia-glx-96, nvidia-glx-envy, nvidia-glx-legacy, nvidia-glx-legacy-envy, nvidia-glx-new, nvidia-glx-new-envy, nvidia-glx-src 
Provides: nvidia-glx, xserver-xorg-video-4 
Depends: nvidia-180-kernel-source (>= 180.37), nvidia-180-libvdpau (>= 180.37), x11-common (>= 1:7.0.0), libc6 (>= 2.1.3), libgcc1 (>= 1:4.1.1), libgl1-mesa | libgl1, libx11-6, libxext6, zlib1g (>= 1:1.1.4) 
Recommends: nvidia-settings 
Conflicts: nvidia-glx, nvidia-glx-src, xorg-driver-fglrx 


It seems strange that 180.35 “provides” xserver-xorg-video-5 and yet 180.37 “provides”  xserver-xorg-video-4?!

The reference to xserver-xorg-video-4 has not reappeared in xserver-xorg-core conflict list within /var/lib/dpkg/status, but it is still in the corresponding conflict list in /var/lib/dpkg/available of course.

So in my case the conflict between v180.37 of nvidia-glx-180 and xserver-xorg-core remains... :confused:

---

### Post by Yeeha on 2009-03-10
So whats the status with 180.37 anyone knows? When it will hit repos?

---

### Post by paul_in_london on 2009-03-10
> **Yeeha said:**
> So whats the status with 180.37 anyone knows? When it will hit repos?

Well you can use this ppa -  [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/

On my system, though, I have a conflict between xserver-xorg-core and v180.37 of nvidia-glx-180.

This was still true last night anyway. Won't be able to check until later whether an update has fixed things.

---

### Post by ruik on 2009-03-12
This one seems to take some time..

---

### Post by Sockerdrickan on 2009-03-12
:popcorn: I bet a new version is going to be released anytime next week.

---

### Post by mgsfan on 2009-03-12
you can also use this repo for them which installed fine
deb [http://ppa.launchpad.net/nferenc/ppa/ubuntu](http://ppa.launchpad.net/nferenc/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/nferenc/ppa/ubuntu](http://ppa.launchpad.net/nferenc/ppa/ubuntu) jaunty main

---

### Post by Kazade on 2009-03-12
> **Tux0r said:**
> I'm trying to learn how to write games using "pure" OpenGL 3.0 and I'm having a lot of problems due to lack of examples etc, anyone have a good link or two?

Hehe, shameless plug: [http://www.amazon.com/Beginning-OpenGL-Game-Programming-Second/dp/159863528X](http://www.amazon.com/Beginning-OpenGL-Game-Programming-Second/dp/159863528X)

It's not out for a couple of weeks, but I updated it to cover using OpenGL 3.0 without the deprecated features (so no immediate mode, display lists, vertex arrays etc. although it covers them all briefly) it also includes Linux source code compiled on Ubuntu which is something that the first edition didn't have.

For now, you can take a look at the code here: [http://www.gamedev.net/community/forums/topic.asp?topic_id=512890](http://www.gamedev.net/community/forums/topic.asp?topic_id=512890)

---

### Post by ruik on 2009-03-12
> **mgsfan said:**
> you can also use this repo for them which installed fine
deb [http://ppa.launchpad.net/nferenc/ppa/ubuntu](http://ppa.launchpad.net/nferenc/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/nferenc/ppa/ubuntu](http://ppa.launchpad.net/nferenc/ppa/ubuntu) jaunty main

Oh great, thanks!

---

### Post by SketchyClown on 2009-03-12
Updated drivers work fine here. No issues that I can see thus far.

---

### Post by paul_in_london on 2009-03-12
Ah! Thanks guys. I think I now have a solution to the problem I've been having with the upgrade of nvidia-glx-180 from 180.35 to 180.37.

Looking at the packages in [http://ppa.launchpad.net/nferenc/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/nferenc/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages) I see that v180.37 of nvidia-glx-180 provides the virtual package xserver-xorg-video-5 (as was the case with 180.35).

So if I use this repo, I should no longer have a conflict with xserver-xorg-core.

Still at work so can't test it yet.

---

### Post by diwas on 2009-03-12
Hey I dont know if its ok to post here but here it is. Can you please tell me how is NVIDIA 7050? What are its disadvantages mainly? I got this 512MB card in ECS GF7050VT-M motherboard..bt i dont know how is this one...

I am sorry if i posted in the wrong place.

---

### Post by taavikko on 2009-03-12
> **diwas said:**
> Hey I dont know if its ok to post here but here it is. Can you please tell me how is NVIDIA 7050? What are its disadvantages mainly? I got this 512MB card in ECS GF7050VT-M motherboard..bt i dont know how is this one...

I am sorry if i posted in the wrong place.

At a quick glance, supported cards on a new driver 180.35

```
zcat /usr/share/doc/nvidia-glx-180/README.txt.gz |grep -i 7050
    GeForce 7050 PV / NVIDIA nForce 630a                      0x053A
    GeForce 7050 PV / NVIDIA nForce 630a                      0x053B
    GeForce 7050 / NVIDIA nForce 610i                         0x07E3

```

---

### Post by Ryan Gardner on 2009-03-12
> **paul_in_london said:**
> Ah! Thanks guys. I think I now have a solution to the problem I've been having with the upgrade of nvidia-glx-180 from 180.35 to 180.37.

Looking at the packages in [http://ppa.launchpad.net/nferenc/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/nferenc/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages) I see that v180.37 of nvidia-glx-180 provides the virtual package xserver-xorg-video-5 (as was the case with 180.35).

So if I use this repo, I should no longer have a conflict with xserver-xorg-core.

Still at work so can't test it yet.
```
ryan@white-donkey:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  nvidia-180-kernel-source nvidia-180-libvdpau nvidia-glx-180 nvidia-glx-180-dev
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 3688kB/12.6MB of archives.
After this operation, 12.3kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  nvidia-180-kernel-source nvidia-180-libvdpau nvidia-glx-180-dev nvidia-glx-180
Install these packages without verification [y/N]? y
Get:1 http://ppa.launchpad.net jaunty/main nvidia-180-kernel-source 180.37-0ubuntu0 [2777kB]
Get:2 http://ppa.launchpad.net jaunty/main nvidia-180-libvdpau 180.37-0ubuntu0 [754kB]                                                                                                                                                        
Get:3 http://ppa.launchpad.net jaunty/main nvidia-glx-180-dev 180.37-0ubuntu0 [157kB]                                                                                                                                                         
Fetched 3688kB in 4min 17s (14.3kB/s)                                                                                                                                                                                                         
(Reading database ... 261720 files and directories currently installed.)
Preparing to replace nvidia-180-kernel-source 180.35-0ubuntu1 (using .../nvidia-180-kernel-source_180.37-0ubuntu0_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-180-kernel-source ...
Preparing to replace nvidia-180-libvdpau 180.35-0ubuntu1 (using .../nvidia-180-libvdpau_180.37-0ubuntu0_i386.deb) ...
Unpacking replacement nvidia-180-libvdpau ...
Preparing to replace nvidia-glx-180-dev 180.35-0ubuntu1 (using .../nvidia-glx-180-dev_180.37-0ubuntu0_i386.deb) ...
Unpacking replacement nvidia-glx-180-dev ...
dpkg: regarding .../nvidia-glx-180_180.37-0ubuntu0_i386.deb containing nvidia-glx-180:
 xserver-xorg-core conflicts with xserver-xorg-video-4
  nvidia-glx-180 provides xserver-xorg-video-4 and is to be installed.
dpkg: error processing /var/cache/apt/archives/nvidia-glx-180_180.37-0ubuntu0_i386.deb (--unpack):
 conflicting packages - not installing nvidia-glx-180
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-180_180.37-0ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It appears that there is still a conflict in the one in the ppa - but maybe I'm doing something wrong.

---

### Post by paul_in_london on 2009-03-12
@Ryan Gardner

It did work Ok for me actually.

First I removed the avenard ppa ([http://www.avenard.org/files/ubuntu-repos/](http://www.avenard.org/files/ubuntu-repos/) release/).

Next I added these entries to my Software Sources:

deb [http://ppa.launchpad.net/nferenc/ppa/ubuntu](http://ppa.launchpad.net/nferenc/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/nferenc/ppa/ubuntu](http://ppa.launchpad.net/nferenc/ppa/ubuntu) jaunty main

Imported the key with:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com ABF3B2646E619416

sudo aptitude update
sudo aptitude install nvidia-glx-180 (reinstall was no good) - to make sure I was now getting the correct version of this!
sudo aptitude update
sudo aptitude upgrade

and all was well - I was finally able to upgrade xserver-xorg-core. It sorted out a problem with an mplayer upgrade being held back as well.

v180.37 of nvidia-glx-180 in the "nferenc" ppa provides xserver-xorg-video-5. This is what resolved the conflict with xserver-xorg-core for me.

I notice your output from apt-get refers to xserver-xorg-video-4.

Which ppa/repo are you using to pick up 180.37?

---

### Post by Ryan Gardner on 2009-03-12
I tried it again with the same problem. Then I decided to delete the .deb that was stored in my apt cache and try again - and this time it redownloaded it and it applied fine. 

I haven't rebooted yet to see if it works, but I'm pretty sure it will. 

Is the deb in the ppa a dkms package? dkms didn't fire up and do anything after it installed:

```

ryan@white-donkey:~$ sudo aptitude install nvidia-glx-180
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  nvidia-glx-180 
0 packages upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 8885kB of archives. After unpacking 26.8MB will be used.
Writing extended state information... Done
Get:1 http://ppa.launchpad.net jaunty/main nvidia-glx-180 180.37-0ubuntu0 [8885kB]
Fetched 8885kB in 2min 49s (52.3kB/s)                                                                                                                                                                                                          
(Reading database ... 259034 files and directories currently installed.)
Unpacking nvidia-glx-180 (from .../nvidia-glx-180_180.37-0ubuntu0_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-glx-180 (180.37-0ubuntu0) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```

---

### Post by mgsfan on 2009-03-12
dkms fired up for me when installing from the ppa I posted

---

### Post by paul_in_london on 2009-03-12
Have a look for the most recent dkms messages in /var/log/apt/term.log

You could also try:

sudo aptitude reinstall nvidia-180-kernel-source nvidia-180-libvdpau nvidia-180-modaliases nvidia-glx-180 nvidia-common

and then you should see some dkms messages on the screen (as you do when you get a kernel update).

---

### Post by diwas on 2009-03-12
GeForce 7050 / NVIDIA nForce 610i                         0x07E3

I have this one. So the driver supports this card! But i want to know if anyone has used it and found any disadvantages..

---

### Post by Technoviking on 2009-03-13
180.37 is now in the main repo.
```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  nvidia-180-kernel-source nvidia-180-libvdpau nvidia-180-modaliases
  nvidia-glx-180 python-central screen-profiles
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.5MB of archives.
After this operation, 197kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com jaunty/main python-central 0.6.11ubuntu4 [44.2kB]
Get:2 http://archive.ubuntu.com jaunty/restricted nvidia-180-kernel-source 180.37-0ubuntu1 [2770kB]
Get:3 http://archive.ubuntu.com jaunty/restricted nvidia-180-libvdpau 180.37-0ubuntu1 [754kB]
Get:4 http://archive.ubuntu.com jaunty/main nvidia-180-modaliases 180.37-0ubuntu1 [11.4kB]
Get:5 http://archive.ubuntu.com jaunty/restricted nvidia-glx-180 180.37-0ubuntu1 [8888kB]
Get:6 http://archive.ubuntu.com jaunty/main screen-profiles 1.39-0ubuntu1 [25.9kB]
Fetched 12.5MB in 12s (987kB/s)                                                
(Reading database ... 132262 files and directories currently installed.)
Preparing to replace python-central 0.6.11ubuntu3 (using .../python-central_0.6.11ubuntu4_all.deb) ...
Unpacking replacement python-central ...
Preparing to replace nvidia-180-kernel-source 180.35-0ubuntu1 (using .../nvidia-180-kernel-source_180.37-0ubuntu1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-180-kernel-source ...
Preparing to replace nvidia-180-libvdpau 180.35-0ubuntu1 (using .../nvidia-180-libvdpau_180.37-0ubuntu1_i386.deb) ...
Unpacking replacement nvidia-180-libvdpau ...
Preparing to replace nvidia-180-modaliases 180.35-0ubuntu1 (using .../nvidia-180-modaliases_180.37-0ubuntu1_i386.deb) ...
Unpacking replacement nvidia-180-modaliases ...
Preparing to replace nvidia-glx-180 180.35-0ubuntu1 (using .../nvidia-glx-180_180.37-0ubuntu1_i386.deb) ...
Unpacking replacement nvidia-glx-180 ...
Preparing to replace screen-profiles 1.37-0ubuntu1 (using .../screen-profiles_1.39-0ubuntu1_all.deb) ...
Leaving `diversion of /usr/bin/screen to /usr/bin/screen.real by screen-profiles'
Unpacking replacement screen-profiles ...
Processing triggers for man-db ...
Setting up python-central (0.6.11ubuntu4) ...

Setting up nvidia-180-kernel-source (180.37-0ubuntu1) ...
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
driver version= 180.37
Doing initial module build
Installing initial module
Done.

Setting up nvidia-180-libvdpau (180.37-0ubuntu1) ...

Setting up nvidia-180-modaliases (180.37-0ubuntu1) ...
Setting up nvidia-glx-180 (180.37-0ubuntu1) ...

Setting up screen-profiles (1.39-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

---

### Post by rudenko_ruslan on 2009-03-13
> **Tux0r said:**
> :popcorn: I bet a new version is going to be released anytime next week.

;)
[QUOTE=AaronP]**185.13 (beta) for Linux x86/x86-64 released**

This is the first driver from the release 185 series, which is the upcoming release cycle as described in [this post]("http://www.nvnews.net/vbulletin/showpost.php?p=1948791&postcount=61"). Please note that this is a beta driver. Use at your own risk.

The 185.13 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86 is available for download via [FTP]("ftp://download.nvidia.com/XFree86/Linux-x86/185.13/").
The 185.13 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86-64 is available for download via [FTP]("ftp://download.nvidia.com/XFree86/Linux-x86_64/185.13/").

Please see the README ([x86]("ftp://download.nvidia.com/XFree86/Linux-x86/185.13/README/index.html"), [x86-64]("ftp://download.nvidia.com/XFree86/Linux-x86_64/185.13/README/index.html")) for more information about this release.

Please note: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.

Please also note: If you encounter any problems with the 185.13 NVIDIA Linux graphics driver release, please start a new thread and include a detailed description of the problem, reproduction steps and generate/attach an nvidia-bug-report.log file (please see [http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678) for details).[/QUOTE]
But I couldn't find a changelog, that's strange... :-k

---

### Post by Nullack on 2009-03-13
Hmm, the repo install of 180.37 didnt go so well. I did it through synaptic and the problems were:

1. No user instruction for rebooting or restarting gdm
2. No modification of xorg.conf to load the driver
3. Hence no driver working

I sorted it all out manually but if anyone else has these issues I'll bug it since I fiddled with my config from a manual install of .37 previously.

---

### Post by cariboo on 2009-03-14
I installed the driver, and did as I normally do hit Ctrl-Alt-Baclspace to restart X, and was greeted with a black screen and a message that there was a problem with the driver. The solution I found was to reboot, and then the driver was loaded normally. 

It looks like Ubuntu is getting more Windows-like all the time. There should be no need to reboot, just because a new driver has been installed.

Jim

---

### Post by taavikko on 2009-03-14
> **rudenko_ruslan said:**
> ;)

But I couldn't find a changelog, that's strange... :-k

```
zcat /usr/share/doc/nvidia-glx-180/NVIDIA_Changelog.gz |less
```
Haven't checked if the new drivers changelog is included

And as always, good place to watch changes,
```
aptitude changelog <package>
```

---

### Post by jocheem67 on 2009-03-14
Did an install using the run-file ( the ctrl-alt-F1 method )...

Works fine.

This is my laptop, I got an ati-card in my desktop and it really strikes me how much better nvidia-drivers are....especially 2d....

---

### Post by plun on 2009-03-14
Just a proposal.... avoiding a mess.

**If a moderator can split this thread to a new about 185.13 ???**

(185.13 is also a beta driver and was a little tricky to install)

---

### Post by Nullack on 2009-03-14
Ive installed 185.17, so far so good.

---

### Post by el-mar01 on 2009-03-14
Is 2D performance even better in 185.17 ??

---

