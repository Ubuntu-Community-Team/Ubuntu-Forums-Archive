---
title: "VLC/Mplayer Uninstallable?"
date: 2009-02-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mempf on 2009-02-04
Is anyone else getting the following if they try to install either mplayer or vlc?

```
vlc:
 Depends: libx264-59 (>=1:0.svn20080408) but it is not installable

```

It seems libx264-65 is the only one in the repositories.

I looked for a bug report but couldn't find one.

---

### Post by techdude3177 on 2009-02-04
i have VLC already installed with no issues.

---

### Post by Neural oD on 2009-02-04
have you installed the medibuntu repositories - I would recommend these!

---

### Post by ajcham on 2009-02-04
Nm.

---

### Post by biasquez on 2009-02-04
same error and i have enabled this too:
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

---

### Post by cariboo on 2009-02-04
I'm not sure if this has anything to do with it, but I always install the ubuntu-restricted-extras meta package before installing vlc.

Jim

---

### Post by taavikko on 2009-02-04
> **cariboo907 said:**
> I'm not sure if this has anything to do with it, but I always install the ubuntu-restricted-extras meta package before installing vlc.

Jim

Nope, apt knows how to pull the dependencies when needed (pkg says so)


Both *-59 & *-65 are automatically installed, and I'll suspect some kind of an diversion between those two. (dependency issue)

```
dpkg -l libx264-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libx264-59     1:0.svn2008040 x264 video coding library
ii  libx264-65     1:0.svn2008123 x264 video coding library
jumala@helvetti:~$ aptitude search libx264-*
i A libx264-59                      - x264 video coding library                 
i A libx264-65                      - x264 video coding library                 
p   libx264-dev                     - development files for libx264 
```

---

### Post by biasquez on 2009-02-04
i fixed problem with this repo:
deb [http://ppa.launchpad.net/mrpouit/ppa/ubuntu](http://ppa.launchpad.net/mrpouit/ppa/ubuntu) jaunty main

---

### Post by taavikko on 2009-02-06
If anyone having this, please confirm.

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/325720](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/325720)

---

### Post by btdown on 2009-02-07
AMD64, still can't install vlc, even with the new repo above.

---

### Post by TpyKv on 2009-02-07
I'm having the same problem on jaunty alpha 3.... wireless works... 3g modem also... but now no DVD!

---

### Post by jp_coll2003 on 2009-02-07
same here. getting the error message and cannot install any multimedia player such as VLC or any of the others. Still, this is an Alpha version.

---

### Post by cariboo on 2009-02-07
I have libx264-59 marked as Installed (local or obsolete). If I try to remove it, it wahts to uninstall vlc and one of the gstreamer-bad codecs.

Jim

---

### Post by Eclipse. on 2009-02-07
Fixed as of 2 hours ago, all you need to do now is wait for the fix to filter down the repo.

---

### Post by Nullack on 2009-02-08
Good, I hope that fixes the gstreamer plugin problem as well

---

### Post by btdown on 2009-02-08
> **Eclipse. said:**
> Fixed as of 2 hours ago, all you need to do now is wait for the fix to filter down the repo.
Thanks for the info!

---

### Post by TpyKv on 2009-02-09
Thanks, will try it out tonight.... :D

---

### Post by btdown on 2009-02-09
Repo updates today fixed the problem.

---

### Post by mempf on 2009-02-09
mplayer/mencoder still remain uninstallable.

Problem fixed for vlc though which is good.

---

### Post by taavikko on 2009-02-09
> **mempf said:**
> mplayer/mencoder still remain uninstallable.

Problem fixed for vlc though which is good.


```
mplayer (2:1.0~rc2-0ubuntu18) jaunty; urgency=low

  * No-change rebuild against new x264 (LP: #327136).


```

---

### Post by yelo3 on 2009-02-10
finally vlc is installable!!! But I get choppy audio... is this the same for you?

---

### Post by taavikko on 2009-02-10
> **yelo3 said:**
> finally vlc is installable!!! But I get choppy audio... is this the same for you?

If using pulseaudio, check that vlc's plugin for that is installed.
(vlc-plugin-pulse)

---

### Post by yelo3 on 2009-02-10
thanks it worked! So I can ask you another thing: how to get the video window embedded in the totem window instead of having 2 different windows?

---

### Post by taavikko on 2009-02-10
> **yelo3 said:**
> thanks it worked! So I can ask you another thing: how to get the video window embedded in the totem window instead of having 2 different windows?

Totem is working, video screen is embedded.

VLC is broken for the moment: [https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/314038](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/314038)

Those two are two completely different programs.

---

### Post by yelo3 on 2009-02-10
Oh I wrote totem by mistake! thanks for the bug link

---

### Post by btdown on 2009-02-10
>  how to get the video window embedded in the vlc window instead of having 2 different windows?yeah this really bugs me too...coulnt find an option that would fix it.

---

### Post by ugkbunb on 2009-02-10
> **taavikko said:**
> ```
mplayer (2:1.0~rc2-0ubuntu18) jaunty; urgency=low

  * No-change rebuild against new x264 (LP: #327136).


```

perhaps the fix hasnt filtered into the AMD64 libs because I can confirm that mplayer is still uninstallable as of 8:30 cst 02/10/09. vlc on the other hand now installs/runs just fine.

I did some more research... here is the PPA for the person who made that comment:
[https://launchpad.net/~quadrispro/+archive/ppa](https://launchpad.net/~quadrispro/+archive/ppa)

You can see that mplayer (2:1.0~rc2-0ubuntu18) is still having build errors... if you look at the log it shows:
```

libx264.c: In function 'X264_init':
libx264.c:165: error: 'x264_param_t' has no member named 'b_bframe_adaptive'
libx264.c:228: error: 'struct <anonymous>' has no member named 'b_bidir_me'
libx264.c:229: error: 'struct <anonymous>' has no member named 'b_bframe_rdo'
libx264.c:254: error: 'struct <anonymous>' has no member named 'psz_rc_eq'
make[3]: *** [libx264.o] Error 1
make[3]: Leaving directory `/build/buildd/mplayer-1.0~rc2/libavcodec'
make[2]: *** [libavcodec/libavcodec.a] Error 2
make[2]: Leaving directory `/build/buildd/mplayer-1.0~rc2'
make[1]: *** [build-gui-stamp] Error 2
make[1]: Leaving directory `/build/buildd/mplayer-1.0~rc2'
make: *** [install] Error 2
dpkg-buildpackage: failure: /usr/bin/fakeroot debian/rules binary-arch gave error exit status 2
******************************************************************************
Build finished at 20090209-1203
FAILED [dpkg-buildpackage died]
Purging chroot-autobuild/build/buildd/mplayer-1.0~rc2

```

---

