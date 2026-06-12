---
title: "Avidemux 2.5 In Karmic?"
date: 2009-07-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Col-1023 on 2009-07-15
While googling around I found this, [http://www.mail-archive.com/karmic-changes@lists.ubuntu.com/msg03688.html](http://www.mail-archive.com/karmic-changes@lists.ubuntu.com/msg03688.html)



[ubuntu/karmic] avidemux 1:2.5.0-0.0ubuntu1 (Accepted)

Alessio Treglia
Mon, 13 Jul 2009 08:05:22 -0700

avidemux (1:2.5.0-0.0ubuntu1) karmic; urgency=low

  * Merge with debian-multimedia, Ubuntu remaining changes:
    - debian/{control,rules}:
      + Drop ccache support.
  * Remove libopencore-amrnb-dev build-dependency.
  * Refresh avidemux-compile.patch.

avidemux (1:2.5.0-0.0) experimental; urgency=low

  * New upstream release.

Date: Mon, 13 Jul 2009 16:56:09 +0200
Changed-By: Alessio Treglia <quadris...@ubuntu.com>
Maintainer: Ubuntu Developers <ubuntu-devel-disc...@lists.ubuntu.com>
[https://launchpad.net/ubuntu/karmic/+source/avidemux/1:2.5.0-0.0ubuntu1](https://launchpad.net/ubuntu/karmic/+source/avidemux/1:2.5.0-0.0ubuntu1)

-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

Format: 1.8
Date: Mon, 13 Jul 2009 16:56:09 +0200
Source: avidemux
Binary: avidemux avidemux-qt avidemux-cli avidemux-common libavidemux
Architecture: source
Version: 1:2.5.0-0.0ubuntu1
Distribution: karmic
Urgency: low
Maintainer: Ubuntu Developers <ubuntu-devel-disc...@lists.ubuntu.com>
Changed-By: Alessio Treglia <quadris...@ubuntu.com>
Description: 
 avidemux   - a free video editor - gtk version
 avidemux-cli - a free video editor - command line version
 avidemux-common - a free video editor - Internationalization files
 avidemux-qt - a free video editor - qt version
 libavidemux - a free video editor - gtk version
Changes: 
 avidemux (1:2.5.0-0.0ubuntu1) karmic; urgency=low
 .
   * Merge with debian-multimedia, Ubuntu remaining changes:
     - debian/{control,rules}:
       + Drop ccache support.
   * Remove libopencore-amrnb-dev build-dependency.
   * Refresh avidemux-compile.patch.
 .
 avidemux (1:2.5.0-0.0) experimental; urgency=low
 .
   * New upstream release.
Checksums-Sha1: 
 0ff3a9c589fe6cbd039cf12b7f0ea33323c87984 1514 avidemux_2.5.0-0.0ubuntu1.dsc
 d75a1be51fcdc3d7551eae940dbbf670ccb12437 12702910 avidemux_2.5.0.orig.tar.gz
 9f946cd14693cf294f46d2e2ec0f04f4a615dfcc 13524 
avidemux_2.5.0-0.0ubuntu1.diff.gz
Checksums-Sha256: 
 c8c7bb6c3838316644296c1c66ed10eae4c87c631927a7006ab54bf72e2e748a 1514 
avidemux_2.5.0-0.0ubuntu1.dsc
 94cc121839df7d68b50a87030a306e180fcd3566827f87cf53ba84b3e3317460 12702910 
avidemux_2.5.0.orig.tar.gz
 d4143849cae587a642effe8b6aade792156567dabfd61d9055a838672bbc0a2a 13524 
avidemux_2.5.0-0.0ubuntu1.diff.gz
Files: 
 bb623c05def30bb28370da2058904d99 1514 graphics optional 
avidemux_2.5.0-0.0ubuntu1.dsc
 837dd39b7a8b423bb3bc0fa85a31c0dc 12702910 graphics optional 
avidemux_2.5.0.orig.tar.gz
 b3f6089f0fbbf23e4925d9924c57a9f8 13524 graphics optional 
avidemux_2.5.0-0.0ubuntu1.diff.gz
Original-Maintainer: Christian Marillat <maril...@debian.org>

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEARECAAYFAkpbSzoACgkQRdSMfNz8P9C0IQCfZHUkDoakzf9111sNGyUqxRep
jLMAni0qlWxASI3JBUbgt1cWjvU5FD4I
=KwER
-----END PGP SIGNATURE-----

-- 
Karmic-changes mailing list
[email]Karmic-changes@lists.ubuntu.com[/email]
Modify settings or unsubscribe at: 
[https://lists.ubuntu.com/mailman/listinfo/karmic-changes](https://lists.ubuntu.com/mailman/listinfo/karmic-changes)


If this does mean Karmic will have avidemux 2.5 that would be cool since I use avidemux alot on my i7 machine.

---

### Post by nhasian on 2009-07-15
> karmic ia64   Failed to build

when i type:

```
apt-cache policy avidemux
```

it says:

> avidemux:
  Installed: (none)
  Candidate: 1:2.4.4-0.3ubuntu1
  Version table:
     1:2.4.4-0.3ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages

---

### Post by taavikko on 2009-07-15
It's been rejected for some reason:
[https://edge.launchpad.net/ubuntu/karmic/+queue?queue_state=4&queue_text=avidemux](https://edge.launchpad.net/ubuntu/karmic/+queue?queue_state=4&queue_text=avidemux)
But based on that announce, Karmic fill feature avidemux 2.5=< in the repos.

---

### Post by martinpm24 on 2009-07-15
I want the same :D

from debian-multimedia.org:
> Well... this version can't be packaged completely (plugins are missing).
  I'm waiting for a fix from the upstream author.

---

### Post by Col-1023 on 2009-07-15
This doom9 forum post [http://forum.doom9.org/showthread.php?t=108784&page=60](http://forum.doom9.org/showthread.php?t=108784&page=60) has this changelop for avidemux,

 Avidemux 2.5 SVN-r5065 (2009-07-12)
[http://www.avidemux.org/](http://www.avidemux.org/)

Quote:
Revision 5065 (12 Jul 2009)
# Updated Vorbis to version 1.2.3.
# Updated x264 to r1181.
Quote:
5065 - [win32] fix linking
5064 - [x264/Xvid] use button boxes on Qt config windows
5063 - [vidEnc] tidy up memory allocation for video encoder options
5050 - [bootStrap] Fix install path, have to specify twice
5049 - [BooStrap] Fix mixup
5046 - [vidEnc] Linux compilation fixes
5042 - [Build] Gcc 4.4 fixes by whaevr
5036 - [Patch] wrong include
5035 - [Patch] plf underlinking
5034 - [Patch] Plf format string patch
5033 - [Build] Bootstrap script
5032 - [Build Fix] Build fix for karmic koala + simple build script for main (not for plugins yet)
Download Mirror #1: [http://mulder.dummwiedeutsch.de/](http://mulder.dummwiedeutsch.de/)
Download Mirror #2: [http://avidemux.razorbyte.com.au/](http://avidemux.razorbyte.com.au/)


#5032 is a build fix for karmic, but it I don't know whether its the change that makes it possible to include 2.5.

---

### Post by Col-1023 on 2009-07-18
You Beauty, t's in Karmic, [https://launchpad.net/ubuntu/karmic/+package/avidemux-qt](https://launchpad.net/ubuntu/karmic/+package/avidemux-qt).

The x264 version in karmic is quite recent too, [https://launchpad.net/ubuntu/karmic/+package/libx264-67](https://launchpad.net/ubuntu/karmic/+package/libx264-67).

---

### Post by hikaricore on 2009-08-13
It's in there.... but there are no damn filters.
I can't even rotate a video from my phone for uploading.. :p

For now you're probably best off using: [http://www.getdeb.net/release/4619](http://www.getdeb.net/release/4619)

---

### Post by quadrispro on 2009-08-23
avidemux 2.5.1 is available for Karmic:

```
avidemux (1:2.5.1+repack-0ubuntu1) karmic; urgency=low

  * New upstream bugfix release (LP: #416066):
    - Re-enabled several video and audio encoders (regression introduced
      in 2.5.0)
    - Updated the FFmpeg libraries
    - More video encoders are now plugins
    - DV video encoder now supports more profiles
    - Fixed loading and saving issues with LAME, x264 and Xvid options
      (regression introduced in 2.5.0)
    - Fraps video decoding support
    - Lowpass-5 mode added to libavcodec deinterlacer filter plugin
    - Fixed formatting of parameters for various filters on 64-bit platforms
    - Updated libass
    - Fixed sizing of the bitrate control on various video encoder configure
      windows (regression introduced in 2.5.0)
    - Improved filter dialog for GTK+ interface
    - New navigation icons for GTK+ interface
    - Fixed the behaviour of several GTK+ open/save dialogs (regression
      introduced in 2.5.0)
    - asharp filter's Block Adaptive mode can now be disabled using the Qt
      interface
    - Re-enabled the colour chooser dialog using the Qt interface (regression
      introduced in 2.5.0)
    - GCC 4.4 support
    - Fixed issues with CMake build scripts when using multiple make jobs
      (regression introduced in 2.5.0)
  * Remove debian/patches dir and drop all patches, now applied by upstream.
  * Drop quilt support.
  * debian/libavidemux0.install: Also install missing libraries.
  * Move debian/install to debian/avidemux.install.
  * debian/rules:
    - Build the internal ffmpeg version properly (thanks to Christian Marillat).
    - A bit of cleanup.
  * debian/control:
    - Bump Standards-Version.
    - Update Homepage field.
    - Adjust libavidemux0 short description.
    - gtk -> GTK, qt -> QT.
    - Set myself as Maintainer.
  * Repack the tarball to remove the debian/ dir provided by upstream:
    - Create debian/README.source.
    - Update debian/watch.
    - Add get-orig-source target to debian/rules.
```

---

### Post by selimhilmi on 2009-08-23
[SIZE=3]hello everybody. my problem is about filtering the videos. i want to filter a specified area on the video by using ''contrast''. despite adjusting the brightness and contrast as i like for example pure black, this doesnt appear pure black; just blue blueish. and it occurs to all the video not the part i have selected.[/SIZE]
[SIZE=3]Also i get confused by many options by luma, chroma u and v and postprocessing, filter strenght deringing? it makes no sense to me. please anyone help me and thank u in advance.[/SIZE]

---

### Post by DougieFresh4U on 2009-08-23
double post sorry:confused:

---

### Post by DougieFresh4U on 2009-08-23
> **selimhilmi said:**
> [SIZE=3]hello everybody. my problem is about filtering the videos. i want to filter a specified area on the video by using ''contrast''. despite adjusting the brightness and contrast as i like for example pure black, this doesnt appear pure black; just blue blueish. and it occurs to all the video not the part i have selected.[/SIZE]
[SIZE=3]Also i get confused by many options by luma, chroma u and v and postprocessing, filter strenght deringing? it makes no sense to me. please anyone help me and thank u in advance.[/SIZE]
'Yelling' for help won't get you far  :lolflag:

---

