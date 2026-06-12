---
title: "nVidia driver 177.82 released"
date: 2008-11-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by plun on 2008-11-12
Edit new release

**180.06** is out.....

Release Highlights

* Added support for CUDA 2.1.
* Added initial support for PureVideo-like features on Linux via the new VDPAU API (see the vdpau.h header file installed withthe driver).
* Added new workstation performance optimizations.
* Enabled the X Render "GlyphCache" by default.
* Disabled shared memory X pixmaps by default; see the&#8220;AllowSHMPixmaps" option.
* Fixed a regression that could result in window decorationcorruption when running Compiz using Geforce 6 and 7 series GPUs.
* Improved X pixmap placement on GeForce 8 series and later GPUs.
* Improved compatibility with recent Linux kernels.
* Improved stability on some GeForce 8 series and newer GPUs.

[http://www.nvnews.net/vbulletin/showthread.php?t=123072](http://www.nvnews.net/vbulletin/showthread.php?t=123072)







Release Highlights:177.82

    * Added support for the following new GPUs:
          o Quadro NVS 450
          o Quadro FX 370 LP
          o Quadro FX 5800
          o Quadro FX 4800
          o Quadro FX 470
          o Quadro CX
    * Fixed a problem on recent mobile GPUs that caused a power management resume from S3 to take 30+ seconds.
    * Fixed a problem with hotkey switching on some recent mobile GPUs.
    * **Fixed an image corruption issue seen in FireFox 3.**

[http://www.nvnews.net/vbulletin/showthread.php?p=1842773](http://www.nvnews.net/vbulletin/showthread.php?p=1842773)

---

### Post by jfernyhough on 2008-11-13
Ah, nice. I notice you're on nvnews now too. :)

It also didn't seem to take as long to get a patch for 28-rc for this driver. Which again is good.

---

### Post by el-mar01 on 2008-11-13
Will this driver be an update in Intrepid ??

---

### Post by autocrosser on 2008-11-13
Not unless it gets backported....You could do a feature request, but but with Intrepid's "real" lifespan being 6 months--------

---

### Post by plun on 2008-11-14
The 180 series driver is soon also out and with this driver
compiz/plasma/AWN will be fixed.

[http://www.nvnews.net/vbulletin/showthread.php?t=104822&page=6](http://www.nvnews.net/vbulletin/showthread.php?t=104822&page=6)

 
@jfernyhough

Well...patches...:lolflag:

Still 10 degrees lower GPU core temp.

---

### Post by plun on 2008-11-14
**180.06 is out**.....:)

Release Highlights

    * Added support for CUDA 2.1.
    * Added initial support for PureVideo-like features on Linux via the new VDPAU API (see the vdpau.h header file installed withthe driver).
    * Added new workstation performance optimizations.
    * Enabled the X Render "GlyphCache" by default.
    * Disabled shared memory X pixmaps by default; see the&#8220;AllowSHMPixmaps" option.
    * **Fixed a regression that could result in window decorationcorruption when running Compiz using Geforce 6 and 7 series GPUs.**
    * Improved X pixmap placement on GeForce 8 series and later GPUs.
    * Improved compatibility with recent Linux kernels.
    * Improved stability on some GeForce 8 series and newer GPUs.

[http://www.nvnews.net/vbulletin/showthread.php?t=123072](http://www.nvnews.net/vbulletin/showthread.php?t=123072)

(find the patch again....:)  )   EDIT  no need for patch, 2.6.28 kernel  !

---

### Post by Gourgi on 2008-11-14
> **plun said:**
> **180.06 is out**.....:)
    * **Fixed a regression that could result in window decorationcorruption when running Compiz using Geforce 6 and 7 series GPUs.**
At last !!!

i hope it really works..

---

### Post by plun on 2008-11-14
> **Gourgi said:**
> At last !!!

i hope it really works..

Yup... its fixed !

Ongoing Launchpad "bug", I cannot see any reasons for 177.82

[https://bugs.launchpad.net/bugs/297543](https://bugs.launchpad.net/bugs/297543)


RGBA trashing is also fixed....  Murrine challenge.

KDE4/Plasma ?

Just great !   Better then "Windoooze  7 "... :)

---

### Post by MacUntu on 2008-11-14
Just installed it and seems to work fine (using a G70M). Is there a proper way to tell dkms to stop looking/building 177.80 (I'm not yet on Jaunty)?

---

### Post by Grant A. on 2008-11-14
Thank God! That damn driver is finally fixed. Um, is 180.06 in the arch repositories?

---

### Post by plun on 2008-11-14
> **MacUntu said:**
> Just installed it and seems to work fine (using a G70M). Is there a proper way to tell dkms to stop looking/building 177.80 (I'm not yet on Jaunty)?

Yup, you can uninstall nvidia-glx-177 and DKMS will stop arguing.

But then you always needs to reinstall the driver if the kernel is changed.

---

### Post by MacUntu on 2008-11-14
Uhm, haha. I just tried "dkms uninstall" and "dkms remove" - forgot about the package. Thanks! :D

I'm using a customized kernel so I'm used to reinstall things, that's ok. :)

---

### Post by plun on 2008-11-14
"Software development is an extreme form of masochism." :lolflag:

---

### Post by Gina on 2008-11-14
Oooh I know!! :lolflag:

---

### Post by krausest on 2008-11-14
Wow - I can't believe it. Just downloaded the 180.06 driver and I could install it!!! (no xen errors) - something that has never worked since 8.10 alpha.

---

### Post by Gourgi on 2008-11-14
i was waiting  for an 'official' deb but this is not going to happen for intrepid 
[QUOTE=Alberto Milone]I will provide 177.82 in Intrepid (SRU) and maybe 180.06 in Jaunty.[/QUOTE] 

so I'm going to install 180,06 now !!

**Gourgi hugs Alberto nevertheless

---

### Post by jdeslip on 2008-11-14
Awww, I was hoping 180.06 would make envy... I am scared or install the binary from nvidia.

---

### Post by perfectska04 on 2008-11-14
Since Intrepid includes DKMS now, is there a way to use it with the binary Nvidia drivers?

I already removed Ubuntu's drivers and installed 180.06, but it'd be great if I could make it play nice with DKMS.

---

### Post by plun on 2008-11-14
> **jdeslip said:**
> Awww, I was hoping 180.06 would make envy... I am scared or install the binary from nvidia.

Well... its just software.  


@perfectska04

Just remove nvidia-glx-177

Look a few messages above about  "Software development is an extreme form of masochism." :)

---

### Post by stinger30au on 2008-11-14
well fingers crossed they should have the legacy drivers in final soon too... yippie

---

### Post by plun on 2008-11-15
nVidia VDPAU Benchmarks

[http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau&num=1)

> We had used the latest MPlayer SVN code and used the NVIDIA-supplied patches that add VDPAU support to mplayer, libavcodec, libavutil, and ffmpeg. This was done on an Ubuntu 8.10 system with the Linux 2.6.27 kernel, X Server 1.5.2, and the NVIDIA 180.08 driver.


> Well, as you can see from the results, the CPU usage of the Intel Core 2 Duo E8400 running at 1.80GHz was dramatically lower when using VDPAU as opposed to GL2 and X-Video with the GeForce 9800GTX. **There is clearly a night and day difference.** Sadly since NVIDIA doesn't support XvMC on GPUs newer than the GeForce 7 series, we weren't able to provide any XvMC vs. VDPAU comparison benchmarks with MPEG-2 decoding. We are continuing our exploration of VDPAU and will report back with any other findings. Once AMD officially introduces X-Video Bitstream Acceleration it should make for an interesting comparison. 


As I understands it a G92 chip or above is also required for accelerated video. Nevertheless no problem playing a H.264 file.

(more at nVidias forum)

---

### Post by itsStephen on 2008-11-15
Just wondering, does 177.82 now work with the geforce 6100 on (k)ubuntu?

---

### Post by perfectska04 on 2008-11-15
> **plun said:**
> Well... its just software.  


@perfectska04

Just remove nvidia-glx-177

Look a few messages above about  "Software development is an extreme form of masochism." :)

Hey, thanks for the response but I meant something along the lines of adding the new driver to DKMS (so that it rebuilds automatically after kernel upgrades). I already managed to install it by removing all the previous Nvidia drivers, but I was just wondering if I could use the included DKMS to rebuild 180.06 modules when necessary.

---

### Post by plun on 2008-11-15
> **perfectska04 said:**
> Hey, thanks for the response but I meant something along the lines of adding the new driver to DKMS (so that it rebuilds automatically after kernel upgrades). I already managed to install it by removing all the previous Nvidia drivers, but I was just wondering if I could use the included DKMS to rebuild 180.06 modules when necessary.

Ok, I don't know but maybe we can figure it out....:)

This is DKMS manpage

[http://linux.dell.com/dkms/manpage.html](http://linux.dell.com/dkms/manpage.html)

---

### Post by autocrosser on 2008-11-15
Short answer--"should" be yes---Look at:

[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

> **itsStephen said:**
> Just wondering, does 177.82 now work with the geforce 6100 on (k)ubuntu?

---

### Post by leandir on 2008-11-20
If you find out a way to achieve auto-recompiling of the nvida-driver with DKMS, please post it. I am installing the 180.06 driver now :)

---

### Post by xebian on 2008-11-20
> **leandir said:**
> If you find out a way to achieve auto-recompiling of the nvida-driver with DKMS, please post it. I am installing the 180.06 driver now :)

Unless 06 is better for you there is an 08 already.

---

### Post by jfernyhough on 2008-11-20
Has anyone got any word from Alberto on how the packaging for 180.x is going?

---

### Post by plun on 2008-11-20
> **jfernyhough said:**
> Has anyone got any word from Alberto on how the packaging for 180.x is going?

He is working with this....

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/297543](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/297543)

I also added 180.08... the challenge is that its betas...[-X

I cannot see any meaning with 177.82 which doesn't solve any major bug which the 180 drivers do.

The VDPAU script works...:)
[http://www.nvnews.net/vbulletin/showthread.php?t=123091](http://www.nvnews.net/vbulletin/showthread.php?t=123091)

I build it also with Gmplayer as GUI.... time for a new graphic card maybe..

---

### Post by alazou on 2008-11-21
works great for me too (180.08). the installation took less than one minute and it fixed all of my problems. this is so great. it's a pity that it won't be available for intrepid. It makes the expenrience so much smoother

---

### Post by amano on 2008-11-21
Please backport 177.82 to Intrepid. Those are just bugfixed that will not do too much harm...

180+ should go straight to the Jaunty repos.

---

### Post by phenest on 2008-11-21
I'm using 180.06 and the issue with artefacts in AWN has been resolved. Now to see if it crashes like the previous drivers.

---

### Post by ronacc on 2008-11-21
I went to d/l the 180.06 64bit driver and it dosen't come up for any 7xxx or 8xxx cards only for 9xxx cards ??? even though the description specificly mentions fixes for 6,7 and 8 series cards . I'll give it a spin on my 7600le and see what happens .

---

### Post by plun on 2008-11-21
> **ronacc said:**
> I went to d/l the 180.06 64bit driver and it dosen't come up for any 7xxx or 8xxx cards only for 9xxx cards ??? even though the description specificly mentions fixes for 6,7 and 8 series cards . I'll give it a spin on my 7600le and see what happens .

ronacc... its a beta and therefore you dont see it.

180.08 is latest

[http://www.nvnews.net/vbulletin/showthread.php?p=1847941](http://www.nvnews.net/vbulletin/showthread.php?p=1847941)

Have Fun...!  Works great on my 7600 card.

---

### Post by perfectska04 on 2008-11-21
> **ronacc said:**
> I went to d/l the 180.06 64bit driver and it dosen't come up for any 7xxx or 8xxx cards only for 9xxx cards ??? even though the description specificly mentions fixes for 6,7 and 8 series cards . I'll give it a spin on my 7600le and see what happens .

Just download it from the FTP in the nv news forums. It should work, although in my 6800 gs card I notice that the screen goes black for a few seconds every time compiz is started. On my 8600m gt laptop suspend doesn't work, so perhaps it's a bit more unstable than previous Nvidia betas.

---

### Post by ronacc on 2008-11-21
> **plun said:**
> ronacc... its a beta and therefore you dont see it.

180.08 is latest

[http://www.nvnews.net/vbulletin/showthread.php?p=1847941](http://www.nvnews.net/vbulletin/showthread.php?p=1847941)

Have Fun...!  Works great on my 7600 card.

I was looking on the betas page . and it does show if I tell the selector I have a 9 series card atleast the 180.06 does so I d/l'd that one , I'll check the link ou provided and get the 08 .

---

### Post by ronacc on 2008-11-21
ok got the .08 driver up and running , I had to use recovery mode to do it , my usual trick of killing the low graphics warning with ctrl>alt>bkspc and then droping to  a shell resulted in a corrupt display and no ability to bring up a term , same result letting low graphics start and then stopping GDM .

---

### Post by jfernyhough on 2008-11-21
I don't think the corrupted display is anything do do with the nvidia driver - I had the same thing after removing 177 using jockey so I could install 180.08. A reboot fixed it, weirdly.

Of course, when I rebuilt 2.6.28-rc6 for Jaunty and went to reinstall 180.08 I got the same corrupted display. Thankfully the console is nice and predictable. :D

all blind:
log in
sudo /etc/init.d/gdm stop
cd downloads/drivers
sudo sh ./N[tab]
right-arrow to accept, enter
enter to install anyway, enter to get kernel, enter to build, (enter again?), hard disc starts chugging
when it stops, right-arrow so it doesn't alter xorg.conf, enter
enter a couple of times to check it exited - the corrupted display changes a little
sudo /etc/init.d/gdm start

w00!

---

### Post by ronacc on 2008-11-21
that was the problem , the only way I could get a console was recovery mode , nothing else worked , and yes the corupted display was after I had removed the 177.80 driver using dkms --remove .I'm still on the .27-7 kernel I'll see what happens when .28 hits the repos .

---

### Post by PRGUY85 on 2008-11-22
I wanna try to stick with the jaunty repos and updates.  Maybe I haven't noticed if this is said anywhere, but when will the new drivers be included in the jaunty repos?

---

### Post by autocrosser on 2008-11-22
as soon as Alberto has them built---next week <shrug?>

I E'd him last week & he said as soon as possible......

---

### Post by phenest on 2008-11-22
Sorry for going off-topic, but...

> **autocrosser said:**
> ...I E'd him last week...

E'd him? Emailed him, right? Jeez, if all terminology gets reduced to a single letter...:lolflag:

---

### Post by Gina on 2008-11-22
The mind boggles!! :lolflag:

---

### Post by autocrosser on 2008-11-22
But then we could only talk about 26 things :)

HMMMM--sounds like the current, outgoing US president:lolflag:

really--really off-topic :)

> **phenest said:**
> Sorry for going off-topic, but...



E'd him? Emailed him, right? Jeez, if all terminology gets reduced to a single letter...:lolflag:

---

### Post by PRGUY85 on 2008-11-23
So, if I try to install this right now on my Intrepid box, what major problems will i get?  What will DKMS do?

---

### Post by perfectska04 on 2008-11-23
> **PRGUY85 said:**
> So, if I try to install this right now on my Intrepid box, what major problems will i get?  What will DKMS do?

What I did:
sudo apt-get remove nvidia-glx-177 nvidia-177-kernel-source nvidia-settings

That should take care of unloading the DKMS module and whatnot, just install Nvidia's driver now. To revert back, uninstall the Nvidia driver and:
sudo apt-get install nvidia-glx-177 nvidia-177-kernel-source nvidia-settings

As for problems you can expect, suspend doesn't seem to work in my laptop and my desktop has some minor display issues, but that's somethin I figure NVIDIA will fix in later versions.

Still looking for a way to use DKMS with Nvidia's package. I noticed that the new virtualbox 2.0.6 uses DKMS to recompile their module, so I don't know why we can't do that with 180.08.

---

### Post by PRGUY85 on 2008-11-23
Thanks, trying it now.   By the way, Shiki-Dust is what Darkroom should have been.

Edit:

I just tried installing it on a root terminal and after successfully doing so, screen now is all weird.  When I installed it it couldn't contact nvidia.com for a preconfigured kernel...

---

### Post by PRGUY85 on 2008-11-23
How can I uninstall this thing?

---

### Post by perfectska04 on 2008-11-23
> **PRGUY85 said:**
> How can I uninstall this thing?

It's normal for it to say there's no preconfigured kernel. You have to let it compile it on its own, so it might have failed if you don't have the build-essential package.

If you want to uninstall, just run the script again and add --uninstall at the end. Then, install Ubuntu's nvidia packages that you removed earlier.

---

### Post by PRGUY85 on 2008-11-23
Thanks, I'll wait for a deb package or something I guess.

---

### Post by ronacc on 2008-11-23
its not hard to install the nvidia driver just accept everything except the last where it asks if you want to run the nvidia config utility say not to that . you need to have the headers for your kernel installed and the build-essentials , both are in synaptic . note you will have to reinstall it after a kernel or xorg update . but after a few times it becomes second nature .

---

### Post by PRGUY85 on 2008-11-24
I tried it just as you all said but couldn't get it to work.  Login screen works fine but once I enter my user info, I get a weird looking screen.  I know it is responding to my actions based on changes in screen color but nothing else.  I am using the pkg0.run one, should I use pkg1.run?

EDIT:

I tried the pkg1.run file.  It installed properly but when I reached my desktop I was still using the no effects open source non-restricted nvidia drivers.  I uninstalled and went back to 177.77...sigh...

---

### Post by plun on 2008-11-24
> **PRGUY85 said:**
> I tried it just as you all said but couldn't get it to work.  Login screen works fine but once I enter my user info, I get a weird looking screen.  I know it is responding to my actions based on changes in screen color but nothing else.  I am using the pkg0.run one, should I use pkg1.run?

EDIT:

I tried the pkg1.run file.  It installed properly but when I reached my desktop I was still using the no effects open source non-restricted nvidia drivers.  I uninstalled and went back to 177.77...sigh...

tty  (Ctrl-Alt-F1-F6) is broken and you must use recovery mode for driver install

Filed this bug against tty  (if someone can confirm ?  )

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/301737](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/301737)

---

### Post by ronacc on 2008-11-24
if you are 64bit you need the pkg2.run for 32bit use pkg1.run .

---

### Post by Gourgi on 2008-11-25
> **ronacc said:**
> if you are 64bit you need the pkg2.run for 32bit use pkg1.run .

????
i 've downloaded the pkg1.run on my 64 bit installation and it worked ! :confused:

---

### Post by vgrisham on 2008-11-25
So I'm trying to install the new driver using the recovery mode root shell. The nvidia installer tells me something about needing to use level 3 something or other; when I type the suggested command of telenit 3, my computer reboots. 

What am I supposed to do once I get to the shell prompt?

EDIT: By the way, I'm running 64-bit Intrepid.

---

### Post by ronacc on 2008-11-25
it will install just fine from the root shell , atleast it did for me . if I recall I just ran it again a second time and it went ahead and ran the second time .

---

### Post by plun on 2008-11-25
I installed it twice for an hour ago and the first message
from the installer is just a warning about Sysinit level 3

No problem to install

After install  > Ctrl-Alt-Del for reboot

---

### Post by vgrisham on 2008-11-25
I logged out then did crtl-alt-f4 and was able to install from the command line. It works great! No more crappy "artifacts" on my awn dock and my windows look perfect for the first time since upgrading to Intrepid.

---

### Post by krausest on 2008-11-26
> **vgrisham said:**
> So I'm trying to install the new driver using the recovery mode root shell. The nvidia installer tells me something about needing to use level 3 something or other; when I type the suggested command of telenit 3, my computer reboots. 

What am I supposed to do once I get to the shell prompt?

EDIT: By the way, I'm running 64-bit Intrepid.

sudo /etc/init.d/gdm stop

Then run the nvidia installer (say no when it asks whether it should search for a download - make sure you've got the prerequisites installed, if not sudo apt-get install build-essential)

After the installation run sudo /etc/init.d/gdm start

---

### Post by vgrisham on 2008-11-28
Update manager installed the new linux kernel last night. After rebooting, x was broken. I reinstalled the 180.06 driver and everything is good again. My question is, am I going to have to do that every time a new kernel is released? Is there anything I can do to make the new kernel play nice with the beta driver automatically?

---

### Post by ronacc on 2008-11-28
if you hand install the driver you will have to reinstall with a kernel update ( that changes version #) .

---

### Post by vhaarr on 2008-12-01
> 
Driver 180.08 (nvidia-glx-180) has been uploaded to Jaunty. The same package works if you install it in Intrepid.


[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/297543/comments/39](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/297543/comments/39)

---

### Post by vgrisham on 2008-12-01
So does that mean that 180.06 will be available in the restricted drivers manager in Intrepid?

---

### Post by vhaarr on 2008-12-01
No, 180.08 will be.

---

### Post by xat_ on 2008-12-01
> **vgrisham said:**
> Update manager installed the new linux kernel last night. After rebooting, x was broken. I reinstalled the 180.06 driver and everything is good again. My question is, am I going to have to do that every time a new kernel is released? Is there anything I can do to make the new kernel play nice with the beta driver automatically?

The drivers build their own kernel module specific to the kernel you currently use, so when a new kernel update comes out you must recompile the kernel module (by reinstalling the drivers) as the module that is built will be built using the linux kernel headers that are specific to your kernel.

---

### Post by ronacc on 2008-12-01
once 180.08 hits the repos jockey and dkms will take care of building the module when a new kernel is installed , until then you will have to hand install it .

---

### Post by vhaarr on 2008-12-01
So, I see it in [https://launchpad.net/ubuntu/jaunty/+queue](https://launchpad.net/ubuntu/jaunty/+queue) -- how long until it will actually be built? It has been in the queue for 8 hours now.

---

### Post by plun on 2008-12-01
> **vhaarr said:**
> So, I see it in [https://launchpad.net/ubuntu/jaunty/+queue](https://launchpad.net/ubuntu/jaunty/+queue) -- how long until it will actually be built? It has been in the queue for 8 hours now.

173, 177 and 96 was accepted but not 180, no idea why not  ?:confused:

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/thread.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/thread.html)

.

---

### Post by vhaarr on 2008-12-01
plun, 180 is still in the New queue, it hasn't been rejected. So how long does it take before it's accepted (and then built) or rejected?

---

### Post by plun on 2008-12-01
> **vhaarr said:**
> plun, 180 is still in the New queue, it hasn't been rejected. So how long does it take before it's accepted (and then built) or rejected?

Without an accept message,  forever in queue as I understands it.

It is not allowed to be built.  Some of the core developers or dist-manager must approve. I don´t know exactly...

---

### Post by vhaarr on 2008-12-01
> 
I need someone from the SRU team to approve this FFE. Then driver 180 will have to be copied to the backports repository.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/297543/comments/42](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/297543/comments/42)

I have no idea what either SRU or FFE means.

I tried downloading the 3 files listed at [https://launchpad.net/ubuntu/jaunty/+queue](https://launchpad.net/ubuntu/jaunty/+queue) (.dsc, .diff.gz and .orig.tar.gz) to build it myself, but seems I need to read a lot of tutorials to navigate this deb system.

---

### Post by plun on 2008-12-02
> **vhaarr said:**
> [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/297543/comments/42](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/297543/comments/42)

I have no idea what either SRU or FFE means.

I tried downloading the 3 files listed at [https://launchpad.net/ubuntu/jaunty/+queue](https://launchpad.net/ubuntu/jaunty/+queue) (.dsc, .diff.gz and .orig.tar.gz) to build it myself, but seems I need to read a lot of tutorials to navigate this deb system.

What you are seeing is source files before building a deb package.

SRU, Stable Release Update
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

FFe, Feature Freeze Exceptation    EDIT it was feature
[https://wiki.ubuntu.com/FreezeExceptionProcess](https://wiki.ubuntu.com/FreezeExceptionProcess)

[https://wiki.ubuntu.com/FeatureFreeze](https://wiki.ubuntu.com/FeatureFreeze)

For Jaunty it cannot be any trouble.:confused:  Should be in testing...

Intrepid is more difficult and it is a beta driver....my personal opinion is that this should be avoided.  nVidia also probably releases a new driver this week.  But...this is indeed difficult.

---

### Post by ShockME on 2008-12-02
For the impatient:

I downloaded 
* nvidia-180-kernel-source  NVIDIA binary kernel module source
* nvidia-180-modaliases Modaliases for the NVIDIA binary X.Org driver
* nvidia-glx-180 NVIDIA binary Xorg driver

from [https://edge.launchpad.net/~anders-kaseorg/+archive](https://edge.launchpad.net/~anders-kaseorg/+archive) and installed them (had to deactivate the previously installed driver using Jockey before I could install). After installation I rebooted, enabled the 180 driver in Jockey and rebooted again.

The packages are for Jaunty but I installed them on Intrepid which seems to work OK for me. The OOo issues and the logout screen garbage are fixed for me, the systray icon background issue is still there (I'm using KDE4).
The only weird thing I've notices so far is a slight font problem in that sometimes it looks like some pixels from the caracters aren't drawn. I prefer this to the other issues with the older drivers.

-----
This info is provided AS IS and I make absolutely NO WARRANTIES whether express or implied. If you decide to use the info you do so at your own risk!

---

### Post by pferraro on 2008-12-02
Now that 180.08 is finally in the repos, 180.11 (beta) just came out:
[http://www.nvnews.net/vbulletin/showthread.php?t=124059](http://www.nvnews.net/vbulletin/showthread.php?t=124059)

---

### Post by plun on 2008-12-02
> **pferraro said:**
> Now that 180.08 is finally in the repos, 180.11 (beta) just came out:
[http://www.nvnews.net/vbulletin/showthread.php?t=124059](http://www.nvnews.net/vbulletin/showthread.php?t=124059)

Well...   ^ ^  

Someone else can maybe file a upgrade bug....my mailbox is spammed with comments.....:KS

---

### Post by plun on 2008-12-03
Just for the records a filed one...

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/304773](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/304773)

Works just fine with Jaunty.

---

### Post by vhaarr on 2008-12-03
[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001512.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001512.html)

180.11 accepted and in build queue.

---

### Post by Chareos on 2008-12-03
What about a backport to Intrepid ?

---

### Post by vhaarr on 2008-12-03
Why can't I see the 180 drivers in synaptic?

---

### Post by ronacc on 2008-12-03
because it hasn'thit the repos yet , be patient or hand install the one from Nvidia .

---

### Post by vgrisham on 2008-12-15
I installed 180.16 on Saturday (by hand on Intrepid). Afterwards, Firefox couldn't draw it's window borders. On a hunch, I went into the Hardware Drivers manager in the Administration menu and deactivated the old driver. That did the trick and my borders are good again.

---

