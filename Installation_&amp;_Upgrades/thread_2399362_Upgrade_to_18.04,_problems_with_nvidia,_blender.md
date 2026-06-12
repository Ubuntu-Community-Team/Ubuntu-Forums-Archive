---
title: "Upgrade to 18.04, problems with nvidia, blender"
date: 2018-08-24
forum: Installation &amp; Upgrades
---

### Post by peterg17 on 2018-08-24
Hi,
After upgrading from version 17.something to 18.04, I had the following issues.

I could not log in to X11 as gdm kept crashing. I have an ASUS N53SV laptop, with dual nvidia/intel optimus graphics. I tried installing lightdm, but that refused to authenticate.
Finally I removed bumblebee and all nvidia packages, and it allows login. I am unsure what causes the conflict. I am not planning to use the nvidia graphics for a while, so I am moving on. But I thought I would report the problem.

The other problem I am having is a concern, as I wish to use blender. (I can always compile it from source though, but something I would rather avoid) The binary has two failed library dependencies:
```
**$ ldd /usr/bin/blender | grep found**   
    *libvpx.so.3 => not found*
*    libva-drm.so.1 => not found*

```
The file libvpx.so.5 is installed, but not version 3. I have not looked at the libva-drm.so.1 issue.

Some details about my system may be relevant. It is a 64 bit system.
```
**$ cat /etc/lsb-release**
*DISTRIB_ID=Ubuntu*
*DISTRIB_RELEASE=18.04*
*DISTRIB_CODENAME=bionic*
*DISTRIB_DESCRIPTION="Ubuntu 18.04.1 LTS"*
**$ uname -a**
[I]Linux Jupiter 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
[/I]
```
Although the install certainly did not run smoothly, eventually I got it to a state where apt/dpkg thinks all is ok.

---

### Post by peterg17 on 2018-08-24
I found missing libraries similar for other executables in /usr/bin, as the following script attests.
Perhaps this problem could be best addressed by supplying the libraries, or I am missing a package?
 
```
for xxx in /usr/bin/*; do if ( file $xxx | grep ELF > /dev/null) && ldd $xxx | grep 'not found'; then echo $xxx; fi; done
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/aegisub-3.2
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/blender
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/blenderplayer
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/DashCast
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/dump-gnash
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/ffmpeg
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/ffplay
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/ffprobe
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/ffserver
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/gmplayer
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/gpsbabelfe
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/gtk-gnash
    libguile.so.17 => not found
/usr/bin/lilypond.real
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/makemkvcon
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/mencoder
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/mplayer
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/tcdecode
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/tcprobe
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/x264
    libvpx.so.3 => not found
    libva-drm.so.1 => not found
/usr/bin/xjadeo
```

---

