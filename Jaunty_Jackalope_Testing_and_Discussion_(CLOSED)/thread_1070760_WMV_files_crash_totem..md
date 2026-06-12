---
title: "WMV files crash totem."
date: 2009-02-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-02-15
Anyone else get this happening?

Tried disabling compiz with no effect.

---

### Post by ronacc on 2009-02-15
not having any trouble with totem+wmv here with compiz .

---

### Post by Nullack on 2009-02-15
can you host a sample so we can look? wmv's are not generic they contain many different things

---

### Post by Toe on 2009-02-15
I think I'm also affected by this or a very similar bug.
Several videos that used to work with Intrepid's totem now cause the program to crash.
I specifically observed this with a collection of 720p MKV files.

There's also a Nautilus crash that may be related. It happens upon right-clicking to bring up the file properties and then choosing the audio/video tab .

---

### Post by Nullack on 2009-02-15
Guys, saying WMV or MKV does very little to specifically diagnosing the problem. Those formats are just *containers*, and like physical containers like they can potentially contain many different things inside it.

How about inspecting the GTS properties with the gstreamer tools or hosting some samples.

---

### Post by philinux on 2009-02-16
Hi nullack,

[http://www.jhepple.com/support/sample_movies1.htm](http://www.jhepple.com/support/sample_movies1.htm)

Sample 15 crashes totem but sample 14 does not. I'm not an expert at debugging this stuff but I'll file a bug report.
```

 totem

(totem:26058): GStreamer-CRITICAL **: gst_pad_alloc_buffer_full: assertion `size >= 0' failed
** Message: Error: Internal GStreamer error: negotiation problem.  Please file a bug at http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer.
gstffmpegdec.c(1140): gst_ffmpegdec_negotiate (): /GstPlayBin:play/GstDecodeBin:decodebin0/ffdec_wmv3_vdpau:ffdec_wmv3_vdpau0:
could not find caps for codec (wmv3_vdpau), unknown type

Segmentation fault (core dumped)
```

---

### Post by Nullack on 2009-02-17
Hi mate

Sample 15 "niceday.wmv" plays fine on mine. To confirm do you have:

Good plugins
Bad plugins
Ugly plugins
ffmpeg plugins

Installed on gstreamer and your using the gstreamer backend for Totem?

---

### Post by ronacc on 2009-02-17
both samples , #14 and #15 , play fine for me with totem-gstreamer .

---

### Post by philinux on 2009-02-17
I'm on 64 bit if that makes a difference. Got good, bad, ugly and ffmpeg plugins installed. VLC can play the sample.

---

### Post by Nullack on 2009-02-17
Are you using the gstreamer totem backend? Or Xine?

---

### Post by philinux on 2009-02-17
> **Nullack said:**
> Are you using the gstreamer totem backend? Or Xine?

Gstreamer I guess as it's a standard install.

---

### Post by taavikko on 2009-02-17
> **philinux said:**
> I'm on 64 bit if that makes a difference. Got good, bad, ugly and ffmpeg plugins installed. VLC can play the sample.

I'll suspect it needs gstreamer0.10-plugins-bad-multiverse
to play properly, but it isn't installable, due to unmet dependencies...

libmjpegtools0c2a (>= 1:1.8.0) but it is not installable
libx264-59 (>= 1:0.svn20080408) but it is not installable

---

### Post by Nullack on 2009-02-17
If thats so why can I play it no problems? Im on x64

---

### Post by taavikko on 2009-02-17
> **Nullack said:**
> If thats so why can I play it no problems? Im on x64

Beats me?? 
Just tested on my i686 installation and the file played with no problems.
Installations are quite identical...

Ain't using no ppa's or other experimental stuff... other than aplha os :)

---

### Post by ronacc on 2009-02-17
I'm 64bit here and I have  gstreamer0.10-plugins-bad 0.10.10-1 (regular  not multiverse ) and they play for me . I also have both gstreamer0.10-plugins-ugly 0.10.10-1 and gstreamer0.10-plugins-ugly-multiverse 0.10.7-2  installed .

---

### Post by philinux on 2009-02-17
> **taavikko said:**
> I'll suspect it needs gstreamer0.10-plugins-bad-multiverse
to play properly, but it isn't installable, due to unmet dependencies...

libmjpegtools0c2a (>= 1:1.8.0) but it is not installable
libx264-59 (>= 1:0.svn20080408) but it is not installable

That plugin is installed.

---

### Post by philinux on 2009-02-17
Just done todays updates and now no problem.

---

### Post by taavikko on 2009-02-17
> **philinux said:**
> Just done todays updates and now no problem.

testing...

i686 laptop fresh install when ext4 was available. works.
x86_64 desktop fresh install alpha4. doesn't work

both, all updates applied every day.

---

### Post by philinux on 2009-02-18
Back to bad ways again. :(

---

### Post by philinux on 2009-02-23
Works fine on jaunty upgrade from intrepid but crashes on jaunty clean install. Any way to debug this. I've raised a bug at launchpad.

---

### Post by Nullack on 2009-02-24
Please host a sample of the problem file.

You can use gst inspect to gather multimedia details but I suspect it wont reveal anything of much use.

---

### Post by philinux on 2009-02-24
Hi,

See post #6

---

### Post by Nullack on 2009-02-24
Sorry Phil I forgot you provided one. Using:

nullack@PPP:~$ sudo apt-cache policy totem
[sudo] password for nullack: 
totem:
  Installed: 2.25.91-0ubuntu1
  Candidate: 2.25.91-0ubuntu1
  Version table:
 *** 2.25.91-0ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
        100 /var/lib/dpkg/status

With the default gstreamer backend I have no problems with playback. I use the good, bad, bad multiverse, ugly and ugly multiverse plugins - but most impoprtantly I also have the ffmpeg plugin installed to get the benefit of libavcodec.

My mplayer svn compile with vdpau acceleration spits out:

nullack@PPP:~/Downloads$ mplayer -vo vdpau -vc ffwmv3vdpau -ao pulse niceday.wmv 
MPlayer SVN-r28715-4.3.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing niceday.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  320x240  24bpp  1000.000 fps  250.0 kbps (30.5 kbyte/s)
Clip info:
 name: 
 author: 
 copyright: 
 comments: 
==========================================================================
Forced video codec: ffwmv3vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[wmv3_vdpau @ 0xc9bbe0]Old WMV3 version detected, only I-frames will be decoded
Selected video codec: [ffwmv3vdpau] vfm: ffmpeg (FFmpeg WMV3/WMV9 (VDPAU))
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 65.6 kbit/4.65% (ratio: 8205->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
[pulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: WMV3 VDPAU acceleration)
VDec: using WMV3 VDPAU acceleration as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [vdpau] 320x240 => 320x240 WMV3 VDPAU acceleration 
[vdpau] Failed creating VDPAU decoder: An invalid/unsupported VdpDecoderProfile value was supplied.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
Error while decoding frame!57 ct:  0.000   1/  1 ??% ??% ??,?% 0 0 
Error while decoding frame!49 ct:  0.005   2/  2 ??% ??% ??,?% 0 0 
Error while decoding frame!44 ct:  0.009   3/  3 ??% ??% ??,?% 0 0 

So you can see this file isnt all that clean, but nonetheless gstreamer is ok with it. Same with mplayer. FFMPEG with libavcodec is highly resilient to stream errors :)

---

### Post by philinux on 2009-02-24
Thanks Nullack,

Updated and the bugs gone away again. :lolflag:

i only get a still pic every 5 seconds or so. No smooth video.

---

### Post by tgpraveen on 2009-02-24
these are really odd i dont have problems with wmv files but cant play mkv or check their properties as nautilius crashes.

---

### Post by taavikko on 2009-02-25
For me totem-mozilla just stands, and wmv files crash totem...
[https://bugs.launchpad.net/ubuntu/+source/ffmpeg-debian/+bug/330165](https://bugs.launchpad.net/ubuntu/+source/ffmpeg-debian/+bug/330165)

---

### Post by Nullack on 2009-02-25
Bizzare, I cant reproduce the crash with libavcodec.

---

### Post by philinux on 2009-02-25
> **Nullack said:**
> Bizzare, I cant reproduce the crash with libavcodec.

Indeed. Doesn't crash but no sound in jaunty now.....

---

### Post by anders_c_ on 2009-02-25
> **philinux said:**
> Indeed. Doesn't crash but no sound in jaunty now.....

just add your user to group "audio", theres another thread about it...

---

