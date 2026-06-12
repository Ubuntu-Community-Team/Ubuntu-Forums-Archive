---
title: "gstreamer testing request"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Stunts on 2010-03-29
Hi everyone!

For all you guys out there using 10.04 beta, can you test something for me please?
I've been having trouble playing "mod" music files using totem and rhythmbox. It's a gstreamer issue.
I've been having this problem in Arch Linux which uses the same gstreamer version as ubuntu 10.04. I've only got installs of 9.10, so I can't really test it myself.
Just try opening a mod file using totem or rhythmbox (or gstreamer directly using the command below)
```
gst-launch-0.10 -v playbin uri=file:///path/to/file.xm
```
If you can't play these files then it must be an upstream bug and I'll report it.
In case you are wondering what mod files are you can download some examples here:
[http://modarchive.org/](http://modarchive.org/)

Thank you for any feedback!

---

### Post by Stunts on 2010-03-30
It's been over 28 hours and no replies.
Maybe I just had bad timing when posting this.
It's no in page 9, so I'll just bump it and maybe I'll get lucky this time.
Thank you for your time.

---

### Post by taavikko on 2010-03-30
Downloaded one from link provided and the test ended up in 
```
:~$ gst-launch-0.10 -v playbin uri=file:///home/user/underthebridge.mod 
Setting pipeline to PAUSED ...
/GstPlayBin:playbin0/GstDecodeBin:decodebin0/GstTypeFindElement:typefind.GstPad:src: caps = audio/x-mod
/GstPlayBin:playbin0/GstStreamSelector:selector_audio_src0: active-pad = NULL
Pipeline is PREROLLING ...
/GstPlayBin:playbin0/GstDecodeBin:decodebin0/GstModPlug:modplug0.GstPad:sink: caps = audio/x-mod
/GstPlayBin:playbin0/GstDecodeBin:decodebin0.GstGhostPad:src0: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
/GstPlayBin:playbin0/GstDecodeBin:decodebin0/GstModPlug:modplug0.GstPad:src: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
*** glibc detected *** gst-launch-0.10: malloc(): memory corruption: 0x0000000001f74210 ***
======= Backtrace: =========
/lib/libc.so.6(+0x775b6)[0x7ff2622c35b6]
/lib/libc.so.6(+0x7b6d8)[0x7ff2622c76d8]
/lib/libc.so.6(__libc_malloc+0x6e)[0x7ff2622c858e]
/lib/libglib-2.0.so.0(g_realloc+0x2f)[0x7ff26283258f]
/lib/libglib-2.0.so.0(+0x18dcb)[0x7ff262803dcb]
/lib/libglib-2.0.so.0(g_array_sized_new+0xab)[0x7ff262803fab]
/usr/lib/libgstreamer-0.10.so.0(+0x76439)[0x7ff26318f439]
/usr/lib/libgstreamer-0.10.so.0(gst_structure_copy+0x2d)[0x7ff26318f48d]
/usr/lib/libgstreamer-0.10.so.0(gst_caps_copy+0x8f)[0x7ff26314ec6f]
/usr/lib/libgstreamer-0.10.so.0(gst_caps_subtract+0x82)[0x7ff26314ed12]
/usr/lib/libgstreamer-0.10.so.0(gst_caps_is_subset+0x51)[0x7ff26314ef51]
/usr/lib/libgstreamer-0.10.so.0(+0x52be7)[0x7ff26316bbe7]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_get_caps_reffed+0xca)[0x7ff26316f28a]
/usr/lib/libgstreamer-0.10.so.0(+0x46ebd)[0x7ff26315febd]
/usr/lib/libgstreamer-0.10.so.0(+0x52bac)[0x7ff26316bbac]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_get_caps_reffed+0xca)[0x7ff26316f28a]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_peer_get_caps_reffed+0xad)[0x7ff263171d0d]
/usr/lib/libgstbase-0.10.so.0(+0x2476b)[0x7ff26016b76b]
/usr/lib/libgstreamer-0.10.so.0(+0x52bac)[0x7ff26316bbac]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_get_caps_reffed+0xca)[0x7ff26316f28a]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_peer_get_caps_reffed+0xad)[0x7ff263171d0d]
/usr/lib/libgstbase-0.10.so.0(+0x2476b)[0x7ff26016b76b]
/usr/lib/libgstreamer-0.10.so.0(+0x52bac)[0x7ff26316bbac]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_get_caps_reffed+0xca)[0x7ff26316f28a]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_peer_get_caps_reffed+0xad)[0x7ff263171d0d]
/usr/lib/libgstbase-0.10.so.0(+0x2476b)[0x7ff26016b76b]
/usr/lib/libgstreamer-0.10.so.0(+0x52bac)[0x7ff26316bbac]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_get_caps_reffed+0xca)[0x7ff26316f28a]
/usr/lib/libgstreamer-0.10.so.0(+0x46ebd)[0x7ff26315febd]
/usr/lib/libgstreamer-0.10.so.0(+0x52bac)[0x7ff26316bbac]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_get_caps_reffed+0xca)[0x7ff26316f28a]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_get_caps+0x9)[0x7ff26316f3f9]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_peer_get_caps+0xad)[0x7ff263171e2d]
/usr/lib/gstreamer-0.10/libgstcoreelements.so(+0x16756)[0x7ff25ff28756]
/usr/lib/libgstreamer-0.10.so.0(+0x52bac)[0x7ff26316bbac]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_get_caps_reffed+0xca)[0x7ff26316f28a]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_get_caps+0x9)[0x7ff26316f3f9]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_peer_get_caps+0xad)[0x7ff263171e2d]
/usr/lib/gstreamer-0.10/libgstplaybin.so(+0x294a4)[0x7ff2609d54a4]
/usr/lib/libgstreamer-0.10.so.0(+0x52bac)[0x7ff26316bbac]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_get_caps_reffed+0xca)[0x7ff26316f28a]
/usr/lib/libgstreamer-0.10.so.0(+0x56311)[0x7ff26316f311]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_accept_caps+0x12c)[0x7ff26316f72c]
/usr/lib/libgstreamer-0.10.so.0(+0x46e54)[0x7ff26315fe54]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_accept_caps+0x12c)[0x7ff26316f72c]
/usr/lib/libgstreamer-0.10.so.0(+0x56829)[0x7ff26316f829]
/usr/lib/libgstreamer-0.10.so.0(+0x56b62)[0x7ff26316fb62]
/usr/lib/libgstreamer-0.10.so.0(+0x5733e)[0x7ff26317033e]
/usr/lib/gstreamer-0.10/libgstmodplug.so(+0x4a39)[0x7ff25f206a39]
/usr/lib/libgstreamer-0.10.so.0(+0x7f4e3)[0x7ff2631984e3]
/lib/libglib-2.0.so.0(+0x69a5f)[0x7ff262854a5f]
/lib/libglib-2.0.so.0(+0x67b84)[0x7ff262852b84]
/lib/libpthread.so.0(+0x69ca)[0x7ff2625d49ca]
/lib/libc.so.6(clone+0x6d)[0x7ff2623326dd]
======= Memory map: ========
00400000-00406000 r-xp 00000000 08:01 138744                             /usr/bin/gst-launch-0.10
00605000-00606000 r--p 00005000 08:01 138744                             /usr/bin/gst-launch-0.10
00606000-00607000 rw-p 00006000 08:01 138744                             /usr/bin/gst-launch-0.10
01c7e000-01f8f000 rw-p 00000000 00:00 0                                  [heap]
7ff250000000-7ff250021000 rw-p 00000000 00:00 0 
7ff250021000-7ff254000000 ---p 00000000 00:00 0 
7ff2555a0000-7ff2555a1000 ---p 00000000 00:00 0 
7ff2555a1000-7ff255da1000 rw-p 00000000 00:00 0 
7ff255da1000-7ff255da2000 ---p 00000000 00:00 0 
7ff255da2000-7ff2565a2000 rw-p 00000000 00:00 0 
7ff2565a2000-7ff25a5a3000 rw-s 00000000 00:10 117243                     /dev/shm/pulse-shm-2556350871
7ff25a5a3000-7ff25a5a4000 ---p 00000000 00:00 0 
7ff25a5a4000-7ff25ada4000 rw-p 00000000 00:00 0 
7ff25ada4000-7ff25adaa000 r-xp 00000000 08:01 135736                     /usr/lib/libogg.so.0.6.0
7ff25adaa000-7ff25afa9000 ---p 00006000 08:01 135736                     /usr/lib/libogg.so.0.6.0
7ff25afa9000-7ff25afaa000 r--p 00005000 08:01 135736                     /usr/lib/libogg.so.0.6.0
7ff25afaa000-7ff25afab000 rw-p 00006000 08:01 135736                     /usr/lib/libogg.so.0.6.0
7ff25afab000-7ff25afd7000 r-xp 00000000 08:01 135738                     /usr/lib/libvorbis.so.0.4.3
7ff25afd7000-7ff25b1d6000 ---p 0002c000 08:01 135738                     /usr/lib/libvorbis.so.0.4.3
7ff25b1d6000-7ff25b1d7000 r--p 0002b000 08:01 135738                     /usr/lib/libvorbis.so.0.4.3
7ff25b1d7000-7ff25b1d8000 rw-p 0002c000 08:01 135738                     /usr/lib/libvorbis.so.0.4.3
7ff25b1d8000-7ff25b39b000 r-xp 00000000 08:01 135967                     /usr/lib/libvorbisenc.so.2.0.6
7ff25b39b000-7ff25b59b000 ---p 001c3000 08:01 135967                     /usr/lib/libvorbisenc.so.2.0.6
7ff25b59b000-7ff25b5b2000 r--p 001c3000 08:01 135967                     /usr/lib/libvorbisenc.so.2.0.6
7ff25b5b2000-7ff25b5b3000 rw-p 001da000 08:01 135967                     /usr/lib/libvorbisenc.so.2.0.6
7ff25b5b3000-7ff25b5fc000 r-xp 00000000 08:01 135250                     /usr/lib/libFLAC.so.8.2.0
7ff25b5fc000-7ff25b7fc000 ---p 00049000 08:01 135250                     /usr/lib/libFLAC.so.8.2.0
7ff25b7fc000-7ff25b7fd000 r--p 00049000 08:01 135250                     /usr/lib/libFLAC.so.8.2.0
7ff25b7fd000-7ff25b7fe000 rw-p 0004a000 08:01 135250                     /usr/lib/libFLAC.so.8.2.0
7ff25b7fe000-7ff25b803000 r-xp 00000000 08:01 135028                     /usr/lib/libXdmcp.so.6.0.0
7ff25b803000-7ff25ba02000 ---p 00005000 08:01 135028                     /usr/lib/libXdmcp.so.6.0.0
7ff25ba02000-7ff25ba03000 r--p 00004000 08:01 135028                     /usr/lib/libXdmcp.so.6.0.0
7ff25ba03000-7ff25ba04000 rw-p 00005000 08:01 135028                     /usr/lib/libXdmcp.so.6.0.0
7ff25ba04000-7ff25ba06000 r-xp 00000000 08:01 135017                     /usr/lib/libXau.so.6.0.0
7ff25ba06000-7ff25bc06000 ---p 00002000 08:01 135017                     /usr/lib/libXau.so.6.0.0
7ff25bc06000-7ff25bc07000 r--p 00002000 08:01 135017                     /usr/lib/libXau.so.6.0.0
7ff25bc07000-7ff25bc08000 rw-p 00003000 08:01 135017                     /usr/lib/libXau.so.6.0.0
7ff25bc08000-7ff25bc45000 r-xp 00000000 08:01 389447                     /lib/libdbus-1.so.3.4.0
7ff25bc45000-7ff25be45000 ---p 0003d000 08:01 389447                     /lib/libdbus-1.so.3.4.0
7ff25be45000-7ff25be46000 r--p 0003d000 08:01 389447                     /lib/libdbus-1.so.3.4.0Aborted (core dumped)
```

---

### Post by plucky on 2010-03-30
This is what I get running Ubuntu 10.04 in Virtualbox after it downloaded and installed the gstreamer0.10-plugins-bad and 27 other files.

```
gst-launch-0.10 -v playbin uri=file:///home/peter/Downloads/analogic.xm
Setting pipeline to PAUSED ...
/GstPlayBin:playbin0/GstDecodeBin:decodebin0/GstTypeFindElement:typefind.GstPad:src: caps = audio/x-mod
/GstPlayBin:playbin0/GstStreamSelector:selector_audio_src0: active-pad = NULL
Pipeline is PREROLLING ...
/GstPlayBin:playbin0/GstDecodeBin:decodebin0/GstModPlug:modplug0.GstPad:sink: caps = audio/x-mod
/GstPlayBin:playbin0/GstDecodeBin:decodebin0.GstGhostPad:src0: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
/GstPlayBin:playbin0/GstDecodeBin:decodebin0/GstModPlug:modplug0.GstPad:src: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
/GstPlayBin:playbin0/GstStreamSelector:selector_audio_src0.GstPlaybinSelectorPad:sink0: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
/GstPlayBin:playbin0/GstDecodeBin:decodebin0.GstGhostPad:src0.GstProxyPad:proxypad1: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
/GstPlayBin:playbin0/GstStreamSelector:selector_audio_src0.GstPad:src: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
/GstPlayBin:playbin0/GstQueue:preroll_audio_src0.GstPad:sink: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
/GstPlayBin:playbin0/GstQueue:preroll_audio_src0.GstPad:src: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
/GstPlayBin:playbin0/GstBin:abin/GstAudioConvert:aconv.GstPad:src: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
/GstPlayBin:playbin0/GstBin:abin/GstAudioConvert:aconv.GstPad:sink: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
/GstPlayBin:playbin0/GstBin:abin.GstGhostPad:sink: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
/GstPlayBin:playbin0/GstBin:abin.GstGhostPad:sink.GstProxyPad:proxypad3: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
/GstPlayBin:playbin0/GstBin:abin/GstAudioResample:aresample.GstPad:src: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
/GstPlayBin:playbin0/GstBin:abin/GstAudioResample:aresample.GstPad:sink: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
/GstPlayBin:playbin0/GstBin:abin/GstVolume:volume.GstPad:src: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
/GstPlayBin:playbin0/GstBin:abin/GstVolume:volume.GstPad:sink: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
/GstPlayBin:playbin0/GstBin:abin/GstAutoAudioSink:audiosink/GstPulseSink:audiosink-actual-sink-pulse.GstPad:sink: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
/GstPlayBin:playbin0/GstBin:abin/GstAutoAudioSink:audiosink.GstGhostPad:sink: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
/GstPlayBin:playbin0/GstBin:abin/GstAutoAudioSink:audiosink.GstGhostPad:sink.GstProxyPad:proxypad2: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)32, depth=(int)32, rate=(int)44100, channels=(int)1
Pipeline is PREROLLED ...
Setting pipeline to PLAYING ...
New clock: GstPulseSinkClock
/GstPlayBin:playbin0/GstBin:abin/GstAutoAudioSink:audiosink/GstPulseSink:audiosink-actual-sink-pulse: volume = 1.000000
/GstPlayBin:playbin0/GstBin:abin/GstAutoAudioSink:audiosink/GstPulseSink:audiosink-actual-sink-pulse: mute = FALSE
Got EOS from element "playbin0".
Execution ended after 314090592609 ns.
Setting pipeline to PAUSED ...
Setting pipeline to READY ...
/GstPlayBin:playbin0/GstBin:abin/GstAutoAudioSink:audiosink/GstPulseSink:audiosink-actual-sink-pulse.GstPad:sink: caps = NULL
/GstPlayBin:playbin0/GstBin:abin/GstAutoAudioSink:audiosink.GstGhostPad:sink: caps = NULL
/GstPlayBin:playbin0/GstBin:abin/GstVolume:volume.GstPad:src: caps = NULL
/GstPlayBin:playbin0/GstBin:abin/GstVolume:volume.GstPad:sink: caps = NULL
/GstPlayBin:playbin0/GstBin:abin/GstAudioResample:aresample.GstPad:src: caps = NULL
/GstPlayBin:playbin0/GstBin:abin/GstAudioResample:aresample.GstPad:sink: caps = NULL
/GstPlayBin:playbin0/GstBin:abin/GstAudioConvert:aconv.GstPad:src: caps = NULL
/GstPlayBin:playbin0/GstBin:abin/GstAudioConvert:aconv.GstPad:sink: caps = NULL
/GstPlayBin:playbin0/GstBin:abin.GstGhostPad:sink: caps = NULL
/GstPlayBin:playbin0/GstQueue:preroll_audio_src0.GstPad:src: caps = NULL
/GstPlayBin:playbin0/GstQueue:preroll_audio_src0.GstPad:sink: caps = NULL
/GstPlayBin:playbin0/GstStreamSelector:selector_audio_src0.GstPlaybinSelectorPad:sink0: caps = NULL
/GstPlayBin:playbin0/GstStreamSelector:selector_audio_src0.GstPad:src: caps = NULL
/GstPlayBin:playbin0/GstDecodeBin:decodebin0.GstGhostPad:src0: caps = NULL
/GstPlayBin:playbin0/GstDecodeBin:decodebin0/GstModPlug:modplug0.GstPad:src: caps = NULL
/GstPlayBin:playbin0/GstDecodeBin:decodebin0/GstModPlug:modplug0.GstPad:sink: caps = NULL
/GstPlayBin:playbin0/GstDecodeBin:decodebin0/GstTypeFindElement:typefind.GstPad:src: caps = NULL
Setting pipeline to NULL ...
Freeing pipeline ...

```


and the music played.

Hope this helps.

---

### Post by Stunts on 2010-03-30
Thank you for your testing results!
The fact that someone else using ubuntu is also having issues suggests it might be an upstream bug.
However, someone else not having errors... well, I don't know, hence my next question:
Are you using 32 or 64 bits?
I'm having issues on 64 bits. Maybe the taaviko is also on 64 bits while plucky is on 32?
Thanks again for your feedback.

---

### Post by plucky on 2010-03-30
Yes mine is 32-bit Lucid Lynx.


Good Luck

---

### Post by taavikko on 2010-03-30
> **Stunts said:**
> 
I'm having issues on 64 bits. Maybe the taaviko is also on 64 bits...
Thanks again for your feedback.

Yep, x86_64 arch here.

Also tested with $.xm file and it ended up as the same.
"core aborted"

---

### Post by mc4man on 2010-03-30
Happen atm to be on a karmic laptop that has 32 and 64 bit installs - both with the latest gstreamer plugins (same as lucid's

mod's play fine in 32 bit, not in 64 bit

---

### Post by Stunts on 2010-03-30
Thank you guys!
That's all I needed to know!
It's definitely an upstream bug. I'll report it, link to it here and mark the thread solved.
Thank you all again!

---

### Post by Stunts on 2010-03-30
The bug was reported here:
[https://bugzilla.gnome.org/show_bug.cgi?id=614361](https://bugzilla.gnome.org/show_bug.cgi?id=614361)

Thank you all for your assistance. I'll post back here when it's solved. Could be a while though, and this forum section might get closed in the meantime.

---

### Post by Stunts on 2010-04-06
Just to let you know that the bug was fixed upstream.
It was a libmodplug bug and not on Gstreamer.
You can find the latest release here:

[http://sourceforge.net/projects/modplug-xmms/](http://sourceforge.net/projects/modplug-xmms/)

Although I don't think it will make it into Lucid... But it's a sure thing for Maverick Meerkat.

Thank you to all that helped me test this out. It would have taken me a lot longer if it weren't for your help.

---

