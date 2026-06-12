---
title: "libstdc++5 removed from karmic?"
date: 2009-09-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by portis on 2009-09-13
I couldn't find it any more.
So I have to manually install it?

---

### Post by wfp on 2009-09-13
I think it's libstdc++6 now. It's in synaptic.

---

### Post by portis on 2009-09-13
> **wfp said:**
> I think it's libstdc++6 now. It's in synaptic.

Yeah, there was libstdc++6 and libstdc++5 in parallel. But now only libstdc++6.
I have some binaries which depend on libstdc++5.

---

### Post by trulan on 2009-09-13
Like, for instance, the w32 codecs from medibuntu?  They depend on libstdc++5 and won't install in Karmic.

---

### Post by mc4man on 2009-09-14
> 32 codecs from medibuntu? They depend on libstdc++5 and won't install in Karmic

You can use libstdc++5 from jaunty or install the codecs manually if some realmedia playback isn't needed.

The dep on libstdc++5 is from 2 files, -  cook.so and drvc.so

I don't think cook.so is of much value, libavcodec decodes it fine and I believe most apps will go that way.

drvc.so is used on some realmedia files and while some apps can use libavcodec to decode, drvc.so seems to work better, (and may be only option for some players

Ex. mplayer with drvc.so in place

> realvideo codec id: 0x30202002  sub-id: 0x010B9030
[COLOR="Blue"]opening shared obj '/usr/lib/codecs/drvc.so'[/COLOR]
realvideo: using cmsg24 with 3 elements.
INFO: RealVideo codec init OK!
Selected video codec: [rv3040] vfm: realvid (Linux RealPlayer 10 RV30/40)


With it not installed mplayer needs to be forced to avcodec

> Forced video codec: ffrv30
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffrv30] vfm: ffmpeg (FFmpeg RV30)


You don't need a deb to install, they can be manually extracted and put in /usr/lib/codecs or 'installed' as outlined here from mplayer site (under installing codecs section

[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

It does appear that drvc.so will not work unless libstdc++5 is installed (screen shows relevant code in the .so

---

### Post by jocko on 2009-09-14
As far as I know, libstdc++5 was replaced with libstdc++6 during gutsy development, so this is nothing new. But what has happened at some point during gutsy, hardy, intrepid, jaunty and apparently now in karmic development is that they have forgotten to make a symlink. (they fixed it before the final releases of all previous versions).
To fix it:
```
sudo ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.5
```Someone should probably post a bug about this.

---

### Post by bonsiware on 2009-09-14
w32codecs has been updated to be compatible with libstdc++6!!!
:)

---

### Post by mc4man on 2009-09-14
> w32codecs has been updated to be compatible with libstdc++6

Well, actually what they did is remove the files cook.so and drvc.so ,so no libstdc++ is needed at all

not an issue for cook, may or may not be an issue on some realmedia, to late to test here

from the new diff
> 
 * debian/control:
+    - refreshed for karmic
+    - drop old unused conflits/replaces
+    - bump debhelper b-d to (>= 7.0.50~) for the overrides
+    - drop b-d on libstdc++5, removed from karmic.
+  * debian/rules: delete drvc.so and cook.so that require libstdc++5.
+    (LP: #428775)

Edit 
If so probably a minor loss, I believe drvc.so would only be needed for rv30 or less, rv40 is probably handled by avcodec

---

### Post by FunkyRes on 2009-09-14
> **bonsiware said:**
> w32codecs has been updated to be compatible with libstdc++6!!!
:)

Good for them!
But there are other vendors who have software that has not been rebuilt, including companies no longer in business.

A symbolic link to a different version of the shared library is asking for a segmentation fault.

maybe crusty libs for compatibility shouldn't be in main repo, but they should be available as security maintained packages somewhere.

---

### Post by FunkyRes on 2009-09-14
Let me give a real world example.
I'm a light LaTeX user, producing maybe four or five documents a year.

I started with teTeX but when it went to the land of the un-maintained, I switched to TeXLive 2007.

Many of my documents would not compile in TL2007 so I asked for suggestions and was told to install TL2004 in parallel and use that for teTeX documents.

I did that, and it worked perfectly.

I currently have 3 TeX Installs - TL2004, TL2007, TL2009

When I have to make a minor edit to a document I originally authored in teTeX - I can make a minor edit and run it through the TL2004 system. Ditto with stuff originally authored in TL2007.

TL2004 depends upon the libstdc++5

For me to run a system without that library would mean I would have to spend several hours porting one of those older documents to TL2009. Unfortunately I can not just boot off of the TL2004 DVD because my motherboard is too new, I'd have to rebuild the DVD.

Keeping legacy versions of standard libraries is thus necessary for me, and I'd much rather have them in a security maintained repo.

---

### Post by mc4man on 2009-09-14
> I'd much rather have them in a security maintained repo
unless they restore it to karmic repo than you can always get here as a direct download and  install. There are no additional dependencies than the 2 shown which you'll already have installed by default.

[http://packages.ubuntu.com/jaunty/libstdc++5](http://packages.ubuntu.com/jaunty/libstdc++5)

Do not run a link command on it ( libstdc++.so.5 is actually a link to the actual lib, libstdc++.so.5.0.7. The package installs installs both.

---

### Post by strycore on 2009-09-20
i managed to find a copy of the library in my Doom3 folder, I copied it in /lib32 (i'm on x64) and ran ldconfig in order to get Unreal Tournament 2004 running. 

Getting the version from Jaunty is also another (and better) solution.

---

### Post by cylverbak on 2009-09-20
The "Lightning" plug-in for ThunderBird (if downloaded from mozilla) is dependant on finding libstcd++5 installed on your system.

There is a "Lightning" plug-in available in the karmic koala repositories that will install without needing libstcd++5 but it also installs a gmail tie-in and some ubuntu tweaks. It is also unremovable with an uninstall through the ThunderBird Addons menu which is not really a problem as you can easily remove it through the repositories.

Choose your poison :D

---

### Post by modmadmike on 2009-10-11
I installed it with the force option in dpkg but now amyops still reports libstdc++.so.5 as missing!! Is this cause i haven't installed GCC 3.3???

---

### Post by jpmrblood on 2009-10-13
With the libstdc++5 missing, I have applications in my workplace cease to function. I hope Ubuntu maintains the libstdc++5 maybe in universe or multiverse, because many libraries (non-free) still linked into libstdc++5.

---

### Post by rykel on 2009-10-19
Hi all,

I am reading this thread because I cannot run my vcdgear anymore thanks to the missing libstdc++5 (see error below)...

[INDENT][B]$./vcdgear
./vcdgear: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
[/B][/INDENT]

What is the solution again... to install the file from the Jaunty link, or to create the symlink?

---

