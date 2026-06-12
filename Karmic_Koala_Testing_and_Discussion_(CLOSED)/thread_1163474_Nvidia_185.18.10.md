---
title: "Nvidia 185.18.10"
date: 2009-05-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-05-18
Release Highlights:

    * Moved kernel module loading earlier in the X driver's initialization, to facilitate more graceful fallbacks if the kernel module cannot be loaded. Removed the LoadKernelModule X configuration option.
    * Add support for new horizontal interlaced and checkerboard passive stereo modes.
    * Fixed occasional X server crashes when running an OpenGL-based composite manager.
    * Fixed crashes in Bibble 5.

---

### Post by plun on 2009-05-19
Works just fine...perhaps a little faster. (glxgears and glxdragon)

Tested with Gnome, gnome-shell and KDE 4.3

;)

---

### Post by tad1073 on 2009-05-19
I manually installed ver. 180.51 and want o install ver. 185.18.10. What do I need to do to uninstall ver. 180.51?

---

### Post by Nullack on 2009-05-19
stop gdm, --uninstall

---

### Post by tad1073 on 2009-05-19
After i drop to the shell and stop gdm, I would do sh ./NVIDIA-Linux-x86_64-pkg2. run --uninstall or just --uninstall?

---

### Post by alexv75 on 2009-05-19
Nope, you have to write

> sudo nvidia-installer --uninstall

As for the new driver i see slight improvement over 185.18.08 (few more fps on doom's timedemo, and my glmark score went up with ~400 points

---

### Post by tad1073 on 2009-05-19
Thanks for the help. Got it installed.

---

### Post by syko21 on 2009-05-19
It seems to be faster due to the "Loose Binding" option that compiz uses since I sometimes have video refresh issues with that option enabled on the old driver and without that option enabled on the new driver. It might just be a coincidence but I thought I'd throw it out there and see if anyone else is seeing issues.

---

### Post by ktp on 2009-05-19
anyone know if this is going to show up in UbuntuX PPA.

---

### Post by autocrosser on 2009-05-19
> **ktp said:**
> anyone know if this is going to show up in UbuntuX PPA.

You can get from:  deb [http://ppa.launchpad.net/thefirstm/ppa/ubuntu](http://ppa.launchpad.net/thefirstm/ppa/ubuntu) jaunty main

Working very well here....

---

### Post by ktp on 2009-05-19
> **autocrosser said:**
> You can get from:  deb [http://ppa.launchpad.net/thefirstm/ppa/ubuntu](http://ppa.launchpad.net/thefirstm/ppa/ubuntu) jaunty main

Working very well here....

Thanks!!

---

### Post by maxim99 on 2009-05-27
> **autocrosser said:**
> You can get from:  deb [http://ppa.launchpad.net/thefirstm/ppa/ubuntu](http://ppa.launchpad.net/thefirstm/ppa/ubuntu) jaunty main

Working very well here....

Thank you for this.

---

### Post by ubername on 2009-05-27
> **autocrosser said:**
> You can get from:  deb [http://ppa.launchpad.net/thefirstm/ppa/ubuntu](http://ppa.launchpad.net/thefirstm/ppa/ubuntu) jaunty main

Working very well here....

Where can I get the public key for this repository?

---

### Post by CylnZ on 2009-05-27
> **ubername said:**
> Where can I get the public key for this repository?

[https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

---

### Post by ktp on 2009-05-27
> **ubername said:**
> Where can I get the public key for this repository?

Here is general method I use to add key for PPA:

> sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A0D47AB4E99FF9F9C0EA949A26F4EF8440618B66

The last argument, really long hex number, is found on the PPA site.  Each PPA site has following on it:

> This repository is signed with  [1024R/40618B66]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0xA0D47AB4E99FF9F9C0EA949A26F4EF8440618B66&op=index") OpenPGP key.

If you look at the link for "1024R/40618B66", the search query has the hex number you need.

---

### Post by psyke83 on 2009-05-27
> **ktp said:**
> Here is general method I use to add key for PPA:



The last argument, really long hex number, is found on the PPA site.  Each PPA site has following on it:



If you look at the link for "1024R/40618B66", the search query has the hex number you need.

Just a quick heads-up: apt-key will also accept the shortened version you quoted (however, omit the 1024R/ prefix). No need to grab the full key string :).

---

### Post by Darkshade on 2009-05-27
> **psyke83 said:**
> Just a quick heads-up: apt-key will also accept the shortened version you quoted (however, omit the 1024R/ prefix). No need to grab the full key string :).

Rawr, I was about to post the same thing :D

---

### Post by lithorus on 2009-05-28
And now 185.18.14 is here... :)
> 
Release highlights since 185.19:

[LIST]
[*] Fixed a Xinerama drawable resource management problem that can cause GLXBadDrawable errors in certain cases, such as when Wine applications are run.
[*] Fixed XineramaQueryScreens to return 0 screens instead of 1 screen with the geometry of screen 0 when XineramaIsActive returns false. This conforms to the Xinerama manual page and fixes an interaction problem with Compiz when there is more than one X screen.
[*] Moved kernel module loading earlier in the X driver's initialization, to facilitate more graceful fallbacks if the kernel module cannot be loaded. Removed the LoadKernelModule X configuration option.
[*] Added support for new horizontal interlaced and checkerboard passive stereo modes.
[*] Fixed an OpenGL driver crash while running Bibble 5.
[*] Fixed a DisplayPort interaction problem with power management suspend/resume events.
[*] Fixed occasional X driver memory management performance problems when a composite manager is running.
[*] Fixed a bug with VT-switching or mode-switching while using Compiz; the bug could lead to a corrupted desktop (e.g., a white screen) or in the worst case an X server crash.
[*] Fixed a bug that could cause GPU errors in some cases while driving Quadro SDI products.
[*] Fixed a several second hang when VT-switching while OpenGL stereo applications were running on pre-G80 Quadro GPUs.
[*] Added support for multiple swap group members on G80 and later Quadro GPUs.
[*] Fixed the behavior of the NV_CTRL_FRAMELOCK_SYNC_DELAY NV-CONTROL attribute on Quadro G-Sync II.
[*] Fixed a problem with Quadro SDI where transitioning from "clone mode" to "OpenGL mode" would fail.
[*] Fixed VDPAU to eliminate some cases of corruption when decoding H.264 video containing field-coded reference frames on G84, G86, G92, G94, G96, or GT200 GPUs. Such streams are commonly found in DVB broadcasts.
[*] Slightly improved the performance of the VDPAU noise reduction algorithm.
[*] Enhanced VDPAU to validate whether overlay usage is supported by the current hardware configuration, and to automatically fall back to the blit-based presentation queue if required.
[*] Fixed error checking in VdpVideoMixerRender, to reject calls that specify more layers than the VdpMixer was created with.
[*] Modified VDPAU's VDPAU_DEBUG code to emit a complete backtrace on all platforms, not just on 32-bit Linux.
[*] Improved interaction between VDPAU and PowerMizer; appropriate performance levels should now be chosen for video playback of all standard resolutions on all supported GPUs.
[*] Fixed a bug in VDPAU that sometimes caused "display preemption" when the VdpDecoderCreate function failed.
[*] Fixed a potential segfault in the VDPAU trace library, triggered by a multi-threaded application creating a new VdpDevice in one thread, at the same time that another thread detected "display preemption".
[*] Improved compatibility with recent Linux kernels.
[/LIST]


---

### Post by autocrosser on 2009-05-29
It's now on the firsts PPA...Cheers everyone!!!!

---

### Post by ktp on 2009-05-29
> **autocrosser said:**
> It's now on the firsts PPA...Cheers everyone!!!!

Installing now!!! :lolflag:

---

### Post by ubername on 2009-05-30
> **CylnZ said:**
> [https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

Thanks (and to the others for the other suggestions)

---

### Post by autocrosser on 2009-05-30
Yes---I really like using a package as opposed to the manual install---keeps the system cleaner & when the "official" drivers arrive--tis' much simpler ;)

---

### Post by ktp on 2009-05-30
> **autocrosser said:**
> Yes---I really like using a package as opposed to the manual install---keeps the system cleaner & when the "official" drivers arrive--tis' much simpler ;)

Me too!!  This new drivers seems to be pretty good...my card is running lot cooler now.

---

### Post by yoasif on 2009-06-09
thefirstm's ppa doesn't seem to have karmic builds for the newest nvidia drivers -- anyone know how to get the latest nvidia drivers from a ppa on karmic?

---

### Post by crjackson on 2009-06-09
Why does this ppa show build errors?

> 
lpia build of nvidia-graphics-drivers-180 185.19.1~really185.18.14-0ubuntu0 in ubuntu jaunty RELEASE
Changes file: 	not available
Archive: 	Michael Marley PPA
Component: 	main
Status: 	Failed to build
Queued: 	2009-05-29
Started: 	2009-05-29
Builder: 	thorium (virtual)
Build log: 	buildlog_ubuntu-jaunty-lpia.nvidia-graphics-drivers-180_185.19.1~really185.18.14-0ubuntu0_FAILEDTOBUILD.txt.gz
Finished: 	2009-05-29 (took three minutes)

    * View PPA
    * View build records

Build details
Package: 	nvidia-graphics-drivers-180 - 185.19.1~really185.18.14-0ubuntu0 in Michael Marley PPA
Built on: 	Ubuntu Jaunty lpia
Status: 	Failed to build
Queued: 	2009-05-29
Finished: 	2009-05-29


---

### Post by crjackson on 2009-06-09
I went ahead and updated to the new driver on one of my systems. It seems fine so far. I'll run it for a few days before updating other systems.

---

