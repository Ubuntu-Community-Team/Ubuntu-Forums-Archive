---
title: "NVIDIA 180.35 Released"
date: 2009-02-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-02-25
Big News! This driver release features:

VDPAU now supports VC-1/WMV acceleration on all GPUs supported by VDPAU

Yay :popcorn:

Amongst other changes ofcourse.

---

### Post by plun on 2009-02-25
Yup...:popcorn:


[http://www.nvnews.net/vbulletin/showthread.php?t=128939](http://www.nvnews.net/vbulletin/showthread.php?t=128939)


> **Release Highlights:**

    * Added support for the following GPUs:
          o GeForce GT 120
          o GeForce G100
          o Quadro FX 3700M
    * Fixed a bug that caused Maya to freeze when overlays are enabled.
    * Fixed an interaction problem with some applications that use memory tracking libraries.
    * Added support for RG renderbuffers in OpenGL 3.0.
    * Added support for OpenGL 3.0 floating-point depth buffers.
    * Fixed a problem that caused Valgrind to crash when tracing a program that uses OpenGL.
    * **VDPAU updates**:
          o VDPAU now supports VC-1/WMV acceleration on all GPUs supported by VDPAU; see the README for details.
          o Expand the documentation of VDPAU's VdpVideoMixer, in particular regarding how to use the deinterlacing algorithms. Explicitly document "half rate" deinterlacing, which should allow the advanced algorithms to run on more low-end systems. See vdpau.h.
          o Implement a "skip chroma deinterlace" option in VDPAU, which should allow the advanced deinterlacing algorithms to run on more low-end systems. See vdpau.h.
          o Enhance VDPAU to correctly handle some forms of corrupt/invalid MPEG streams on some GPUs.
          o Fix VDPAU to prevent some cases of "display preemption" in the face of missing H.264 reference frames on some GPUs.
          o Fix VDPAU to correctly handle VC-1 skipped pictures with missing start codes on some GPUs.
          o Fix VDPAU to correctly handle WMV "range reduction" on some GPUs. A minor backwards-compatible API change was made for this; see vdpau.h's documentation for structure field VdpPictureInfoVC1.rangered.
          o Fix VDPAU wrapper library to print dlerror() messages when problems occur, which will simplify debugging of driver loading issues.



Testing....):P

---

### Post by Nullack on 2009-02-25
Package bug request is here, someone please confirm it:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/334205](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/334205)

---

### Post by plun on 2009-02-25
> **Nullack said:**
> Package bug request is here, someone please confirm it:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/334205](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/334205)

Ok, done 

dkms and Ubuntus driver removed for a short test, works !

---

### Post by taavikko on 2009-02-25
> **Nullack said:**
> Package bug request is here, someone please confirm it:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/334205](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/334205)

Does it need to go through FFe since it is just an update to current version (180.) and not an major version change..?

But anyway, thanks :)
Want to get all the juice out of my 9800gtx+

---

### Post by mgsfan on 2009-02-25
just installed rebooted and won't load up for me..gives me the low graphics setup..

---

### Post by plun on 2009-02-25
Just a remark....

I lost my sound outputs after reboot.

Testing with alsa 1.0.19 if it comes back...;) 


@mgsfan

dkms must be removed and nvidia-glx-180 (dependency if dkms is removed)

---

### Post by Nullack on 2009-02-25
> **mgsfan said:**
> just installed rebooted and won't load up for me..gives me the low graphics setup..

Youve probably got cruft left over from your previous setting up conflicting with it....look around the README and ubuntu wiki on debugging tips.

---

### Post by plun on 2009-02-25
@Nullack

It might be breakage risk for the moment.

2.6.28 gives me a **busybox** and RC6 boots without sound.

HAL was also updated today, it might be a "brown bag" hidden somewhere..):P

[https://lists.ubuntu.com/archives/jaunty-changes/2009-February/thread.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-February/thread.html)

---

### Post by Nullack on 2009-02-25
RC6 isnt in the Ubuntu build :)

Yeah 2.6.28 needs diagnosis to identify the cause.

Keep in mind this is a stable release from NVIDIA, not beta.

---

### Post by plun on 2009-02-25
> **Nullack said:**
> RC6 isnt in the Ubuntu build :)

Yeah 2.6.28 needs diagnosis to identify the cause.

Keep in mind this is a stable release from NVIDIA, not beta.

Yup...

udev seems to be broken and the system cannot mount the root file system.
(works with RC6)

This has nothing todo with the nvidia driver. (as I sees it)

It might be **the Hal update**,  also a new kernel coming.

The consequense "smells" a chroot if someone updates and reboots... :rolleyes:

---

### Post by RaZoR1394 on 2009-02-25
My screensaver is acting up since this update. Either it gets stuck (keeps running but no input gets you back to the desktop) or it doesn't launch at all.

---

### Post by mgsfan on 2009-02-25
hmm it won't let me install the new drivers without removing xorg

---

### Post by caryb on 2009-02-25
I installed it last night on my 64 bit system & it borks as soon as it goes to startx! I checked the log & it says it cant find any screens. I just reloaded 180.29 & all is good.



Cary

---

### Post by eyelessfade on 2009-02-25
> **caryb said:**
> I installed it last night on my 64 bit system & it borks as soon as it goes to startx! I checked the log & it says it cant find any screens. I just reloaded 180.29 & all is good.
Cary

Think I will wait a bit to try it out then. :)

---

### Post by Nullack on 2009-02-25
I suspect those with x failing to start are not properly removing parts of the old driver before installing the new.

---

### Post by KhaaL on 2009-02-25
is there a PPA with this driver? just want to play safe :)

@Nullack, which parts are those that needs to be removed from the old driver...? also if you install this driver once, do you have to reinstall it for every other kernel?

---

### Post by RaZoR1394 on 2009-02-25
> **KhaaL said:**
> is there a PPA with this driver? just want to play safe :)

@Nullack, which parts are those that needs to be removed from the old driver...? also if you install this driver once, do you have to reinstall it for every other kernel?

I thought no proprietary drivers were allowed on ppa's :/.

---

### Post by cor2y on 2009-02-25
Yes will media playback for vdpau and 3d effects work.
Its borking my screensaver and its the basic gnome-screensaver i have installed on 8.10  and 9.04 not xscreensaver once it goes into screensaver mode i can't get back to the desktop without restarting X.

According to the official nvidia forums
It appears that 180.35 breaks signals with the xorg-server 1.5.2 and possibly other versions.
People who seem not to have this problem are using a release candidate of xorg (1.6)

Maybe in a few days they will issue a fix.
If you can't stand to be without your screensaver etc go back to 180.29

---

### Post by Nullack on 2009-02-25
On my Ubuntu jaunty build, I have no screensaver problem.

@Khaal - remove:

* VDPAU dev package (if installed)
* Previous Nvidia GLX driver
* Previous NVIDIA kernel header
* Ensure build-essential and kernel header packages are installed
* temporarily switch xorg.conf to NV, stop GDM, run the install shell script as root building the module. I dont run 32bit compatability on my AMD64 build for OpenGL.Make sure the dmesg module load works.
* Edit back the conf to enable nvidia
* Manually start GDM again

The commands for GDM are:

sudo /etc/init.d/gdm stop/start

---

### Post by Nullack on 2009-02-25
> **cor2y said:**
> It appears that 180.35 breaks signals with the xorg-server 1.5.2 and possibly other versions.

Jaunty has RC2 1.6, and I cannot replicate these reports.

---

### Post by Nirro on 2009-02-27
> **mgsfan said:**
> hmm it won't let me install the new drivers without removing xorg

I have the same problem.

I'm trying to install from avenard repository :
```
deb http://www.avenard.org/files/ubuntu-repos/ release/
```

apt-get install nvidia-glx-180 wants to remove xserver-xorg packages.

---

### Post by KhaaL on 2009-02-27
Thanks Nullack, but i have the same problem as Nirro and mgsfan... is it because of bad packaging on that repo? I'm going for .29 in the meanwhile.

---

### Post by mgsfan on 2009-02-27
aye thats the same repo I got it from since its also the one that I get mplayer.. I thought maybe it was from anders repo at first but he has'nt updated the drivers yet

---

### Post by philinux on 2009-02-27
Not being a vdpau expert, what does this new driver + xorg mean for my pc. Spec below in sig.

Is it better dvd playback or something else?

---

### Post by cl333r on 2009-02-27
It should upload the CPU load to the GPU, but I tested some of my h.264 movies and I can't spot any such change.

---

### Post by Nullack on 2009-02-27
cl333r you have a config error then in your test design.

It makes a massive difference. My low end test system with an AMD64 sempron chip and only an 8600gt can decode 1920x1080P level 4.2 high profile AVC footage, same with mpeg1/2. The cpu just idles as apposed to the sw decoder which peggs the cpu at 100% with massive frame drops.

Currently vdpau on vc-1 and wmv3 is broken in svn mplayer.

---

### Post by Technoviking on 2009-02-27
In the repos now.

---

### Post by eyelessfade on 2009-02-27
> **cl333r said:**
> It should upload the CPU load to the GPU, but I tested some of my h.264 movies and I can't spot any such change.

It depends on your GPU. Mine a 8800gts don't support to much of vdpau capability.

---

### Post by eyelessfade on 2009-02-27
Actually my card isn't supported at all...

[http://en.wikipedia.org/wiki/VDPAU]("http://en.wikipedia.org/wiki/VDPAU")

---

### Post by Nullack on 2009-02-28
> **eyelessfade said:**
> It depends on your GPU. Mine a 8800gts don't support to much of vdpau capability.

Incorrect. All second gen purevideo hardware now accelerates:

VC-1
WMV3
Mpeg 1
Mpeg 2
AVC

---

### Post by autocrosser on 2009-02-28
I did the update & it's running smooth---with one problem. Gnome-screen-saver became unresponsive after the update & would not release the desktop once in screensave--I tried a few things & ended up changing back to Xscreensaver--I've never liked Gnome-saver anyway, but has anyone seen this?

---

### Post by kurros on 2009-02-28
> **Nullack said:**
> Incorrect. All second gen purevideo hardware now accelerates:

VC-1
WMV3
Mpeg 1
Mpeg 2
AVC

Right, but the 8800 GTS eyelessfade mentioned is not PureVideo 2 capable.

---

### Post by Nullack on 2009-02-28
> **kurros said:**
> Right, but the 8800 GTS eyelessfade mentioned is not PureVideo 2 capable.

Yes, sorry. These marketing names NVIDIA uses generates confusion. The 8800 GTS uses the old G80 chip, but some later 8800 GTS's uses the newer G92 chip. For pci express cards you need either the G84, G86, G92, G94, G96, G98 or GT200 type chips.

---

### Post by IanW on 2009-02-28
Nullack is correct.

The marketing name for the 8800's that _don't_ accelerate (the G80 chip) is "8800GTS 320Mb" or "8800GTS 640Mb". ie. the first cards to use that name.
The marketing name for the G92-based cards was "8800GTS 512Mb".
The G92 chip also appears in the later 9800GT, and is rumored to be used in the forthcoming GTX250.

---

### Post by caryb on 2009-02-28
Just upgraded & copped it, now after 15 mins I loose mouse & keyboard. I have to hard shutdown to rectify.


Cary

---

### Post by JohnJackson on 2009-02-28
> **autocrosser said:**
> I did the update & it's running smooth---with one problem. Gnome-screen-saver became unresponsive after the update & would not release the desktop once in screensave--I tried a few things & ended up changing back to Xscreensaver--I've never liked Gnome-saver anyway, but has anyone seen this?

I have that problem with 180.29, I dare say it isn't just NVIDIA users who have the problem

---

### Post by autocrosser on 2009-02-28
> **JohnJackson said:**
> I have that problem with 180.29, I dare say it isn't just NVIDIA users who have the problem

Hmmm--did you file a bug report?

---

