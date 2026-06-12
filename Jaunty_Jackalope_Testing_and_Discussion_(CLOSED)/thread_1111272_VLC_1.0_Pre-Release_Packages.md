---
title: "VLC 1.0 Pre-Release Packages"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kow on 2009-03-30
I have uploaded a VLC 1.0 snapshot to my PPA. This includes a (slightly) newer version of x264 which the snapshot is built against. The new x264 will not interfere with the (slightly) older x264-65 currently in the jaunty repos. As of 1.0, VLC will no longer provide the vlc-plugin-esd. Ubuntu or any of it's variants should not be using ESD (Esound) anymore anyways. It appears to be working fine for me, however I have not extensively tested it. The devs have apparently re-enabled embedded video so that should no longer be a problem with the QT interface (default for Ubuntu.)

Here is the info:
[https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa)

I will try and update this about every week and beyond 1.0 release if no other maintainer supersedes it. If you are an intrepid user then see [http://nightlies.videolan.org/](http://nightlies.videolan.org/) for 1.0 packages.

[COLOR="Red"]**NOTE**: Ubuntu or VideoLan will NOT provide support for these packages![/COLOR]

---

### Post by Kow on 2009-03-30
```
between 0.9.8a and 1.0.0-pre1:
--------------------------------------

Important notes:
----------------
 * Alsa and OSS audio capture has been removed from the v4l and v4l2 accesses.
   See 'Access:' for more info.

Playback:
 * Instantaneous pausing
 * Frame-by-Frame playback
 * Finer speed control
 * Timeshift for most medias
 * On-the-fly recording for all medias
 * RTSP trickplay support

New Decoders:
 * AES3 (SMPTE 302M)
 * Dolby Digital Plus - E-AC-3 (A/52b)
 * True HD/MLP
 * Blu-Ray Linear PCM
 * QCELP (Qualcomm PureVoice)
 * Real Video 3.0 & 4.0
 * WMA v1/2 fixed point integer
 * Close Caption under SCTE-20 standard

Demuxers:
 * Support for Dirac and RealVideo in Matroska files
 * Major improvements in RealMedia files opening (.rm and .rmvb)
 * Improvements of the TS demuxer for M2TS files from Blu-Ray and AVCHD

Encoders:
 * Dirac encoding using libdirac (supported in Ogg and in TS)
 * Shine mp3 fixed-point encoder

Access:
 * RTSP authentication with Darwin Streaming Server
 * On-the-fly gzip and bzip2 file decompression (except on Windows)
 * Playback for video in uncompressed multi-RAR archives
 * DVB-S and ATSC cards support on Windows
 * New OSS and Alsa accesses. The v4l2 and v4l modules no longer support
   OSS or Alsa audio input. Use --input-slave alsa:// or oss:// if needed.
 * DVB scanning on linux
 * EXPERIMENTAL Blu-Ray Disc and AVCHD Folders support
 * On-the-fly zip file decompression and browsing (MRL of the form zip://file.zip|file.avi to specify the file)
 * Opening of any file descriptor using 'fd://'
 * MTP device access on Unix
 * CD-Text support on the cdda module (CD-Audio)

Inputs:
 * Mouse cursor support in x11 and win32 screen modules
 * Screen module now features partial screen capture and mouse following on
   Windows.

Playlist:
 * Export the playlist in HTML
 * Lua script for BBC radio playback
 * Better metadata handling and reading

Linux/Windows interface:
 * Global Hotkeys on Windows and Linux
 * Various fixes for skins2 interface
 * Recently played items list
 * Interface toolbar customizations
 * Various Improvements on the Qt interface:
    - More menus actions
    - Finer speed slider
    - Improvements on many dialogs
    - New dialog for plugins listing
    - Fixed-size mode for videos
    - Better teletext, trickplay and encrypted streams control
 * Better integration in GTK environments

Mac OS X Interface:
 * Reveal-in-Finder functionality for locally stored items.
 * Easy addition of Subtitles through the Video menu
 * Additional usability improvements

Stream output:
 * Restored the old mpeg2 transrating module.
 * Multiple bridge-in instances are now possible.
 * bridge-in can be used to configure a placeholder stream.
 * Remote Audio Output Protocol (AirTunes) module.

Maemo Port:
 * New Maemo port with:
   - an interface based on Hildon framework.
   - scaler based on the swscale_nokia770 library.

Windows CE Port:
 EXPERIMENTAL work for the winCE port has been done.

Mac OS X Port:
 * Support for Mac OS X 10.4.x was dropped due to its technical limitations
 * Speed improvements by using llvm-gcc

Audio output:
 * Removed obsolete Esound and aRts plugins
 * Surround support for PulseAudio

Video output:
 * Effects (cube, torus, etc.) removed from OpenGL video output
 * Video is able to stay in original size and to zoom in fullscreen (hotkey 'o') while keeping black borders
 * Image video output has been rewritten into a video-filter named 'scene'. The old image video output has been removed.

Miscellanous:
 * Invmem, a fake codec to display images from external applications
```

---

### Post by Polygon on 2009-03-30
and with this release, realplayer just became obsolete. Can't wait till it gets released =)

frame by frame playback is going to be good too!

---

### Post by IanW on 2009-03-30
My favourite line from the changelog:-

"* EXPERIMENTAL _Blu-Ray Disc_ and AVCHD Folders support"

Looking forward to them removing the "EXPERIMENTAL" part :D

---

### Post by plun on 2009-03-30
Thanks Kow for sharing your ppa...:guitar:


No more annoying double windows..seems to function just fine:popcorn:

---

### Post by xens on 2009-03-30
thanks for the files, downloading... :]

---

### Post by Marat89 on 2009-03-30
works perfectly :guitar: THX

---

### Post by binbash on 2009-03-30
I was getting an error after upgrade but after purge i got it working :) Thanks

---

### Post by Darkshade on 2009-03-30
Sweet! Thank you for sharing this, I was missing VLC already (stopped using it when the embedded video broke).

---

### Post by kde4-core-user on 2009-03-30
wow ... this Version work very, very well. Thanks for sharing this in your ppa!

---

### Post by SuperSonic4 on 2009-03-30
Any chance of making a pkgbuild for arch (A)

---

### Post by ubu-for on 2009-03-30
> **Kow said:**
> I have uploaded a VLC 1.0 snapshot to my PPA.
Thank you!

Works great!

---

### Post by vaskark on 2009-03-30
Sweet! You're a lifesaver.
Many thanks.

---

### Post by AaronMT on 2009-03-30
Why do I get no updates after adding this repository and key?

Edit: nm, just did a reinstall of VLC and it found the new packages.

---

### Post by KhaaL on 2009-03-30
is the VLC team planning on including VDPAU support to this release? would be awesome :)

---

### Post by BwackNinja on 2009-03-30
Surround sound support for pulseaudio!!?? Finally!!! This is now the first video player with dvd menus that will have surround sound pulseaudio support :D (that I know of, I'm surprised it doesn't work with mplayer dvdnav considering it works without dvd menus).

EDIT: Pics or it didn't happen :D

---

### Post by hype on 2009-04-02
Thanks for PPA !
Real improvements, many small bugs/issues i had with previous builds are gone. All good. :D

---

### Post by olskar on 2009-04-02
Any chance getting this into Jaunty without the PPA, updated in the repos?

---

### Post by smbm on 2009-04-02
> **olskar said:**
> Any chance getting this into Jaunty without the PPA, updated in the repos?

You could file a feature freeze exception, I'm not sure how but I'm guessing it'll be in the wiki somewhere.

---

### Post by andrewabc on 2009-04-02
> **smbm said:**
> You could file a feature freeze exception, I'm not sure how but I'm guessing it'll be in the wiki somewhere.

[https://wiki.ubuntu.com/FreezeExceptionProcess](https://wiki.ubuntu.com/FreezeExceptionProcess)

Would be interesting, similarly to the firefox 3.5 being in repositories.

---

### Post by Martiini on 2009-04-04
Big Thanks from me too! I had been waiting for this.

---

### Post by kansasnoob on 2009-04-04
Working great here also!

Many thanks!

---

### Post by Longinus00 on 2009-04-04
Does VLC 1.0 have multithreaded decoding of h264/x264 content?

---

### Post by binbash on 2009-04-05
> **Longinus00 said:**
> Does VLC 1.0 have multithreaded decoding of h264/x264 content?

I do not know the vlc part but latest svn of mplayer supports this if you compile it from the source.There is a howto about this multithread at howto section.

---

### Post by hexion on 2009-04-05
For those who want to stick to Jaunty's version (0.98a) and only fix the embedded window issue, you can use this ppa:
deb [http://ppa.launchpad.net/medigeek/ppa/ubuntu](http://ppa.launchpad.net/medigeek/ppa/ubuntu) jaunty main

The version in this thread seems to run smoothly here. I still cannot set VLC to use my multimedia keys (XF86AudioPlay, XF86AudioPrev, ...) in this version though..

---

### Post by Polygon on 2009-04-05
> **hexion said:**
> For those who want to stick to Jaunty's version (0.98a) and only fix the embedded window issue, you can use this ppa:
deb [http://ppa.launchpad.net/medigeek/ppa/ubuntu](http://ppa.launchpad.net/medigeek/ppa/ubuntu) jaunty main

The version in this thread seems to run smoothly here. I still cannot set VLC to use my multimedia keys (XF86AudioPlay, XF86AudioPrev, ...) in this version though..

why would you want to? 1.0 is so much better, and i have not had any crashes with it yet

---

### Post by binbash on 2009-04-05
> **hexion said:**
> For those who want to stick to Jaunty's version (0.98a) and only fix the embedded window issue, you can use this ppa:
deb [http://ppa.launchpad.net/medigeek/ppa/ubuntu](http://ppa.launchpad.net/medigeek/ppa/ubuntu) jaunty main

The version in this thread seems to run smoothly here. I still cannot set VLC to use my multimedia keys (XF86AudioPlay, XF86AudioPrev, ...) in this version though..

I removed vlc because of embedded window issue, thanks i hope this ppa works!

---

### Post by BXCracer on 2009-04-05
Thank you so much. This fixed the embedded window issue and the slow forwarding issue.

---

### Post by hexion on 2009-04-05
> **Polygon said:**
> why would you want to? 1.0 is so much better, and i have not had any crashes with it yet
It's all about options. I'm using the alpha 1.0 version myself but someone might want to stick to Jaunty's version.

---

### Post by Polygon on 2009-04-05
thats still not a very good reason, nothing about the user interface has changed, almost all of it is under the hood

unless someone wants a buggier release and less features.....

---

### Post by hexion on 2009-04-05
If you want a good reason it's enough to point that 0.98a is a release while 1.0 is in alpha state which happens to be stable at the moment but still completely unsupported.

Plus given the fact that the PPA owner will recompile the package regularly, breakage is more than expected.

Plus I guess there's a chance of the owner of the PPA I pointed will sync with Jaunty's repos (but compiling with the correct options to avoid the embedded window issue) so this version would be 'supported'.


But as you may or may not have missed, I just gave another option. Let people decide what's better for them without the need of anyone convincing them about what's best.

---

