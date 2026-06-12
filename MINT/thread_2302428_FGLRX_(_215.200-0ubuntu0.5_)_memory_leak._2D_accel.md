---
title: "FGLRX ( 2:15.200-0ubuntu0.5 ) memory leak. 2D accelration not working."
date: 2015-11-10
forum: MINT
---

### Post by vidiot-x on 2015-11-10
Hi,

I am unable to get the fglrx driver working for Linux Mint 17.2 (Ubuntu 14.04 LTS). The fglrx driver ( Canonical repos) has a memory leak for any OpenGL context and 2D is not accelerated (software rendering). In searching the problem I found the issue is that there is a link is missing to /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so. See this bug report:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1442921?comments=all](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1442921?comments=all)

Using  $ sudo ln -s /usr/lib/libXvBAW.so.1.0 /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so  to add the link does not help. 

I have also submitted a bug report regarding a fglrx memory leak appearing to effect any OpenGL context (possibly related to above).
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1492682](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1492682)

I am interested in a solution to the missing link issue. I would also like to know if I should try using a version of the fglrx driver currently being tested to fix the issue. I am a developer that has moved from Windows to Linux for development and a little 'green/new' to Linux so any help would be greatly appreciated. :)

Thanks.

Using:
Linux Mint 17.2 KDE
Radeon HD5770 1gb
Asus MB, AMD Phenom II X4

---

### Post by howefield on 2015-11-10
Thread moved to the "*MINT*" forum.

---

### Post by vidiot-x on 2015-11-10
^Thanks.. I'm new here. :)

---

### Post by Rob Sayer on 2015-11-11
You can generate a better overview of what your video card and driver are with:

sudo lshw -C video

in terminal.

But the AMD Phenom II gpus are all at least 5 years old.  AMD's linux support isn't all that great, and fglrx is not going to work on that machine.  You can submit as many bug reports as you want but the AMD devs aren't going to spend a lot of time reading them.

The only thing that would work at all would be downgrading the x server, and that isn't going to work all that well either.

Really the best choice is the open source radeon driver and a DE that doesn't need a lot of horsepower by itself.

---

### Post by vidiot-x on 2015-11-11
> But the AMD Phenom II gpus are all at least 5 years old.  AMD's linux  support isn't all that great, and fglrx is not going to work on that  machine.
Although the Phenom II does include a GPU I am not using it at this time. I am instead using a Radeon HD5770 (listed above) which as I understand it 'is' still supported.

> Really the best choice is the open source radeon driver and a DE that doesn't need a lot of horsepower by itself.
DE?

---

### Post by Rob Sayer on 2015-11-12
A DE is a desktop environment.

AFAIK fglrx doesn't work for 5xxx or older cards, so I don't think a 5770 is going to work any better.

---

### Post by QIII on 2015-11-12
fglrx works with HD 5000 models and up.  It doesn't work with HD 4000 models or earlier.

The Phenom II is not an APU, so it shouldn't have a GPU.  There may be integrated graphics on your mobo, however.

There is no need to use a driver from a PPA.  If Mint is using the Canonical repos, it can be installed from there.  There is no guarantee that anything from a PPA will work properly.

---

### Post by vidiot-x on 2015-11-12
> fglrx works with HD 5000 models and up.  It doesn't work with HD 4000 models or earlier.
That is exactly what I have read.

> If Mint is using the Canonical repos , it can be installed from there
That is what Mint is doing, getting fglrx from the Canonical repos ( note - 2:15.200-0ubuntu0.5 ). Mint will give you a choice of which driver to load (open source or proprietary) through system settings/device manager. So the fglrx proprietary driver I am using is from Canonical repos. That driver has the bugs and issues listed above and is what I am seeking to fix.

I have to say that the video driver issues in Linux are (and have been) the thing that holds it back IMHO. This might be to some extent beyond the control of Canonical or other distributions of Linux but until it becomes 'the' priority we will always have these issues. I just want to address the issues I am having with the fglrx driver and to this point not one issue has been addressed, instead the discussion has focused on unrelated issues of GPU series support and alike.

---

### Post by vidiot-x on 2015-11-29
Well,

I have fixed the memory leak by booting Mint into recovery and selecting fix broken dpkg (enable networking first). :)

I have also applied some of the remedies I have come across to fix the broken link (see bug report above) all of which will not enable 2D accelerated rendering so from my point of view this will have to be fixed from the repository end. Looks like we will have to hope and wait they get it fixed.

---

### Post by vidiot-x on 2015-11-29
> all of which will not enable 2D accelerated rendering
I might have spoke to soon. Firefox is not accelerated rendering HTML5 video but Chromium is. So may be I have 2D fixed. Still testing.

---

### Post by vidiot-x on 2015-11-29
A scan of 'xorg.0.log reveals all is well including 'AIGLX' errors not mentioned in this thread. So if you have a Radeon HD5770 or have the same issues posted in this thread I would recommend first switching to the open source driver ((Ubuntu repository, reboot after), purging fglrx, then boot Mint into recovery and selecting fix broken dpkg (enable networking first) and then finally reinstalling fglrx (Ubuntu repository). I'm fairly new to Linux so take my advice with a grain-of-salt, but my issues seem fixed. 

I'll monitor this thread as I have seen many others with the same issues (perhaps they will try this solution).

---

