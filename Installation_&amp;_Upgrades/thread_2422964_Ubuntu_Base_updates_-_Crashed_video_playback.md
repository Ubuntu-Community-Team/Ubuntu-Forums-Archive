---
title: "Ubuntu Base updates - Crashed video playback"
date: 2019-07-15
forum: Installation &amp; Upgrades
---

### Post by tmlake on 2019-07-15
Greetings wise Ubuntu community,

I'm having a video playback issue with Kodi 2:17.6+git20180430.1623-final-0bionic on Ubuntu 18.04.2 LTS.

Everything was running fine until yesterday when I decided to apply the latest Ubuntu updates.
When I try to play a video with Kodi it immediately crashes or plays with a totally black image.

I don't remember exactly what were the updates, but I recall being Ubuntu base upgrades and graphics related (VDPAU, radeon, Gstreamer, X.Org, imagemagick, etc..). It was a small size update and not large driver files.


Kodi's Crashlog:
[https://paste.kodi.tv/qicihizoyu](https://paste.kodi.tv/qicihizoyu)

I'm using Radeon graphics and Kodi give me these errors:

#3  0x00007f47676c60aa in ?? () from /usr/lib/x86_64-linux-gnu/dri/radeonsi_dri.so
#4  0x00007f47676c5dd7 in ?? () from /usr/lib/x86_64-linux-gnu/dri/radeonsi_dri.so

Repeated several times

#3  0x00007f475ce2c5a6 in ?? () from /usr/lib/x86_64-linux-gnu/libLLVM-8.so.1
#4  0x00007f475ce2c425 in ?? () from /usr/lib/x86_64-linux-gnu/libLLVM-8.so.1

#5  0x00007f47a8f223c9 in ?? () from /usr/lib/x86_64-linux-gnu/libpulse.so.0
#6  0x00007f47a0aa2318 in ?? () from /usr/lib/x86_64-linux-gnu/pulseaudio/libpulsecommon-11.1.so

#1  0x00007f47a936f83a in ?? () from /usr/lib/x86_64-linux-gnu/libavahi-common.so.3

ERROR: Failed to determine egl config for visual info

ERROR: GetDirectory - Error getting
ERROR: Previous line repeats 2 times.


Team-Kodi stated these errors are related to 'Not supported GPU drivers' and politely asked us to direct this issue to Ubuntu forums.

There's anothers user with the same problem, but he's using Nvidia graphics.
[https://forum.kodi.tv/showthread.php?tid=345379](https://forum.kodi.tv/showthread.php?tid=345379)


If I install the Latest Kodi 18.3 version, it works without issues.

But not with 17.6 Krypton version that I use.


I've just reinstalled Ubuntu from scratch, the 18.04.2 LTS version available from the website and what I was using without issues.
On the first launch I didn't upgrade anything from the huge list of available packages and just performed an installation of Kodi and its required packages.
I still get the same window crash or black image on videos.

Maybe there's a package here that needs to be downgraded in order to return Kodi's playback, if you guys could help me and point a direction:

curl 
i965-va-driver 
kodi
kodi-bin
libaacs0
libass9
libbdplus0
libbluray2
libcec4
libcrossguid0
libcurl4
libgif7
libllvm8
libmad0
libmicrohttpd12
libmysqlclient20
libnfs11
libp8-platform2
libpcrecpp0v5
libshairplay0
libtinyxml2.6.2v5
libva-drm2
libva-x11-2
libva2
libvdpau1
mesa-utils
mesa-va-drivers
mesa-vdpau-drivers
mysql-common
python-bluez
python-olefile
python-pil
python-simplejson
va-driver-all
vdpau-driver-all

Any comment will be of great help.
Thank you for your time

---

### Post by tmlake on 2019-07-15
I've downgraded mesa-vdpau-drivers without success.

I figured that Kodi plays a very simple .webm video, but not high-def codecs.

---

### Post by tmlake on 2019-07-16
I've found one solution:

If I install the latest open-source drivers that are not available on bionic repositories through the PPA:

sudo add-apt-repository ppa:oibaf/graphics-drivers
sudo apt-get update
sudo apt upgrade

The following packages will be upgraded:
  libdrm-amdgpu1 libdrm-common libdrm-intel1 libdrm-nouveau2 libdrm-radeon1
  libdrm2 libegl-mesa0 libegl1-mesa libgbm1 libgl1-mesa-dri libgl1-mesa-glx
  libglapi-mesa libglx-mesa0 libllvm8 libwayland-egl1-mesa libxatracker2
  mesa-va-drivers mesa-vdpau-drivers mesa-vulkan-drivers

(In my case for radeon graphics, just accept them all)

Afterwards, reconfigure these packages just to be safe:

sudo dpkg --configure -a
sudo dpkg-reconfigure gdm3 ubuntu-session

Reboot your computer.

And voilà, Kodi player is returned.


However I'd prefer to use the default drivers available in the repository, that were released specifically optimized for Ubuntu 18 environment and made with hard effort.
These oibaf drivers don't give a good video quality.

Has anyone figured a way to return this graphic issue back to normality?

---

### Post by tmlake on 2019-07-16
Found what caused the issue:

[https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its](https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its)

I've learn that recently, on this month, Ubuntu added the latest releases of the proprietary Nvidia driver through the regular Ubuntu updates channel. They are now available on the 'Additional Drivers' section.

I'm pretty sure that small adjustments made for this upgrade messed with my Kodi playback, sent through that Ubuntu base updates I described.
And it's not only for AMD, another user with nvidia graphics is having this same issue.

Just check yourselves, install Kodi 17.6 Krypton (not 18) through the official ppa or Ubuntu repository and it will crash on every video you play.

Anyone has a clue?

---

### Post by tmlake on 2019-07-16
Bug report created:

[https://bugs.launchpad.net/ubuntu/+source/kodi/+bug/1836828](https://bugs.launchpad.net/ubuntu/+source/kodi/+bug/1836828)

---

### Post by tmlake on 2019-07-17
Someone please help.
I'm sure your expertise can figure out this in a min. :-({|=

---

### Post by tmlake on 2019-07-17
If I disable VDPAU from Settings/Player and leave enabled just VAAPI, Kodi works.

So it must be a specific misconfiguration with VDPAU.

---

### Post by tmlake on 2019-07-17
Kodi can't load radeonsi_dri.so

There used to occur this same issue with Steam, 
maybe we have here conflicting libraries?

---

### Post by tmlake on 2019-07-18
Solution found:

This bug is caused after an update for the latest version of libdrm-amdgpu1

Changelog
Version: 2.4.97-1ubuntu1~18.04.1     2019-07-03 15:07:54 UTC

  libdrm (2.4.97-1ubuntu1~18.04.1) bionic; urgency=medium

  * Backport to bionic for 18.04.3 HWE stack update. (LP: #1824111)

 -- Timo Aaltonen <email address hidden> Wed, 10 Apr 2019 13:54:06 +0300


Download the previous version from 
[https://mirror.transip.net/ubuntu/ubuntu/pool/main/libd/libdrm/](https://mirror.transip.net/ubuntu/ubuntu/pool/main/libd/libdrm/)

Install libdrm-amdgpu1_2.4.95-1~18.04.1_amd64.deb

and Kodi will return.


Bug reports here
[https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/1837170](https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/1837170)

and here
[https://bugs.launchpad.net/ubuntu/+source/kodi/+bug/1836828](https://bugs.launchpad.net/ubuntu/+source/kodi/+bug/1836828)

Please join us and hope they fix it for the next PointRelease.

---

### Post by uRock on 2019-07-19
I saw you talking about this on the IRC. I am glad you were able to find a workaround and very thankful you added it to the bug report. Hopefully they get it fixed!

---

### Post by tmlake on 2019-07-19
> **uRock said:**
> I saw you talking about this on the IRC. I am glad you were able to find a workaround and very thankful you added it to the bug report. Hopefully they get it fixed!

Oh really? Yes I dug deep, examined 8327493 packages updates and found the little prick causing this bug. :lolflag:

Ubuntu IRC support is simply, amazing. You can't find anywhere this disposition and willingness to help others, making it possible to attract more users to the community and always making it better.

---

### Post by tmlake on 2019-07-19
Different problem situation:

I first applied the downgrade of libdrm-amdgpu1 2.4.97-1ubuntu1~18.04.1 to 2.4.95-1ubuntu1~18.04.1, on the first launch of a newly installed Ubuntu 18.04.2 without any of the 400 updates packages available.
This way I got package Kodi working.

Now, after I update everything to the latest version, with libdrm-amdgpu1 as well, I can no longer downgrade it. If you force it, the system will crash.

I've figured that the removal of mesa-vdpau-drivers (which also removes vdpau-driver-all) gets kodi running normally again, even with VDPAU activated on settings/player.

So for the moment, that's the new solution for kodi's bug:

sudo apt remove mesa-vdpau-drivers
sudo apt-mark hold mesa-vdpau-drivers


Please follow the dev workaround at
[https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/1837170]("https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/1837170")

---

### Post by tmlake on 2019-07-23
A better workaround is to downgrade these packages

libgl1-mesa-dri_18.2.8-0ubuntu0~18.10.2_amd64.deb
mesa-vdpau-drivers_18.2.8-0ubuntu0~18.10.2_amd64.deb

Get them from 
[https://mirrors.d-l.fr/archive.ubuntu.com/ubuntu/pool/main/m/mesa/](https://mirrors.d-l.fr/archive.ubuntu.com/ubuntu/pool/main/m/mesa/)

These are versions packed with the PointRelease 18.04.2 and are just as good as the latest.

Because uninstalling mesa-vdpau-drivers considerably changes the picture quality of Kodi, disabling hw acceleration. 

Let's wait for a fix in the next Ubuntu updates.

---

