---
title: "How To Get ffmpeg on 10.04 LTS (Lucid Lynx)?"
date: 2012-03-24
forum: Installation &amp; Upgrades
---

### Post by JSeymour on 2012-03-24
Can somebody explain how I'm to overcome this, short of hand-building everything (which rather defeats the whole point of bothering with a current Ubuntu release, in my mind):

```

> sudo apt-get install ffmpeg
...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ffmpeg: Depends: libavcodec52 (< 4:0.5.1-99) but it is not going to be installed or
                   libavcodec-extra-52 (< 4:0.5.1-99) but 4:0.6.2-1ubuntu2~ppa1~lucid1 is to be installed
          Depends: libavdevice52 (>= 4:0.5.1-1ubuntu1.3) but it is not going to be installed or
                   libavdevice-extra-52 (>= 4:0.5.1-1ubuntu1.3) but it is not going to be installed
          Depends: libavdevice52 (< 4:0.5.1-99) but it is not going to be installed or
                   libavdevice-extra-52 (< 4:0.5.1-99) but it is not going to be installed
          Depends: libavfilter0 (>= 4:0.5.1-1ubuntu1.3) but it is not going to be installed or
                   libavfilter-extra-0 (>= 4:0.5.1-1ubuntu1.3) but it is not going to be installed
          Depends: libavfilter0 (< 4:0.5.1-99) but it is not going to be installed or
                   libavfilter-extra-0 (< 4:0.5.1-99) but it is not going to be installed
          Depends: libavformat52 (< 4:0.5.1-99) but 4:0.6.2-1ubuntu1.1~ppa1~lucid1 is to be installed or

```So the ffmpeg that's in the repos wants versions of these that are *older* than what the repos have?

So I try this: [Install FFmpeg and x264 on Ubuntu Lucid Lynx 10.04 LTS]("http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289")

Get just this far:
```

sudo apt-get install build-essential git-core checkinstall texi2html libfaac-dev \
>     libopencore-amrnb-dev libopencore-amrwb-dev libsdl1.2-dev libtheora-dev \
>     libvorbis-dev libx11-dev libxfixes-dev zlib1g-dev
...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
  checkinstall: Depends: dpkg-dev but it is not going to be installed
  libvorbis-dev: Depends: libvorbis0a (= 1.2.3-3ubuntu1.1) but 1.3.1-1ubuntu1~ppa1~lucid1 is to be installed
                 Depends: libvorbisenc2 (= 1.2.3-3ubuntu1.1) but 1.3.1-1ubuntu1~ppa1~lucid1 is to be installed
                 Depends: libvorbisfile3 (= 1.2.3-3ubuntu1.1) but 1.3.1-1ubuntu1~ppa1~lucid1 is to be installed

```So it would appear that, again, the Ubuntu repos have packages that are dependent upon packages that are older than what's in the repos.

What is up with this?

Btw: I'm trying to do all this merely so I can get running again the serviio DLNA server I had running under good old 9.10... which I sometimes wish I'd just left alone.

Thanks,
Jim

---

### Post by JSeymour on 2012-03-24
So I figured I might as well proceed with trying to hand-build the stuff.  The Serviio page lists sources for ffmpeg, libRTMP and Lame MP3.  But wait: I already have Lame MP3, I just need the -dev package...
```

> sudo apt-get install libmp3lame-dev
...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libmp3lame-dev: Depends: libmp3lame0 (= 3.98.2+debian-0ubuntu3) but 3.98.4-0ubuntu1~ppa1~lucid1 is to be installed

```Again?!?!

What. The. Blue. Blazes. Is. Going. On with 10.04 LTS?

Thanks,
Jim

---

### Post by Pand5461 on 2012-03-24
Hi!

It seems that you use PPAs which have newer versions of packages than the ones in official repository. Can you install FFmpeg if you disable these PPAs?

---

### Post by mörgæs on 2012-03-24
Why does it have to be 10.04? There have been quite a few changes in ffmpeg (and supporting packages) during the latest two years.

---

### Post by BicyclerBoy on 2012-03-24
Building ffmpeg yourself is a sensible approach because:
- get latest ffmpeg functions/support
- do not break std packages that use libav*
- get std updates..
- no dependency hell..

The ffmpeg libs (libav*) are used by pulse, gstreamer, alsa-plugins, vlc everything etc etc...

There is a later ffmpeg & libav* ppa (J Severinsson)
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg?field.series_filter=lucid](https://launchpad.net/~jon-severinsson/+archive/ffmpeg?field.series_filter=lucid)

Note the problems with library abi changes..the above ppa has both ffmpeg versions. So tread carefully..

I use 4.09 version & libav-extra libraries on lucid without problem..
- alsa-1.0.25-plugins build okay
- std stuff (that's still installed) seems to work inc. pulse & vlc.

---

### Post by JSeymour on 2012-03-25
> **Pand5461 said:**
> Hi!

It seems that you use PPAs which have newer versions of packages than the ones in official repository. Can you install FFmpeg if you disable these PPAs?
It would seem so, Pand5461.  Only thing I can think of is the one got there from "bleed," when I temporarily added that PPA so I could get the non-very-broken version of JPilot.  (The version in 10.04's main repos can cause Palm users **much** grief.  It should be removed it it's not going to be updated to 1.8.x.)

> **mörgæs said:**
> Why does it have to be 10.04? There have been quite a few changes in ffmpeg (and supporting packages) during the latest two years.
I'm using 10.04 LTS precisely *because* it has long-term support.  Upgrading is always a miserable, frustrating experience, so I avoid it to the extent possible.

> **BicyclerBoy said:**
> Building ffmpeg yourself is a sensible approach because:
...
That's what I ultimately did.  I cleared-out the Lame MP3 problem, installed whatever else I could from the normal repos, then built the two packages I had to from tarballs.

Serviio is now working.

Thanks for your feedback, everybody!

Jim

---

### Post by mörgæs on 2012-03-25
Good, then please mark the thread 'solved'.

---

### Post by JSeymour on 2012-04-14
Done.  Sorry for the delay.

---

