---
title: "FAAC Encoding Ability Won't Be Included In Lucid"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Akita on 2010-03-30
Apparently the "solution" to the "Libfaac not LGPL" debate amongst some developers is to not ship any FAAC encoding ability with Lucid in hopes that it will "annoy" enough users to get the problem fixed. It's a sad day when we've devolved from "it just works" to "the answer is to annoy enough users." :frown:

From Launchpad bug 374900:

> removing faac will annoy our users pretty badly, since it is the most
common way to create AAC audio. I hope that removing it will motivate
(more) people to contribute to ffaac, ffmpeg's internal AAC encoder,
which still lacks some features only libfaac has.

...

> 10.04 will ship ffmpeg 0.5, which does not include an aac encoder.

if libfaac is removed, ubuntu 10.04 will not contain any useable AAC
encoder.

---

### Post by mc4man on 2010-03-30
libfaac encoding was removed from ubuntu ffmpeg builds starting in karmic, lucid is just continuing that. (and using the same ffmpeg

For karmic medibuntu produced libfaac enabled builds of ffmpeg and libs, expect the same for lucid once it releases.

The odds of 10.10 using the 0.6 release are decent (if it releases), whether native aac encoding is as good as libfaac or neroAacEnc are questionable.

Those that wish can build their own ffmpeg and libfaac shared libs if desired. (plus other capabilities if they up the -r

---

### Post by forcecore on 2010-03-30
i use months ffmpeg aac and everything is fine so nuke the faac.

---

### Post by FakeOutdoorsman on 2010-03-31
Nothing has been decided yet, as far as I can tell.  However, the FFmpeg devs mention that the native AAC encoder is, "basically unusable in its current state and people shouldn't be using it for serious purposes".:

[[FFmpeg-devel] [FFmpeg-devel-irc] IRC log for 2010-03-27](http://lists.mplayerhq.hu/pipermail/ffmpeg-devel/2010-March/086214.html)

neroAacEnc is easy to use:
```
ffmpeg -i input.foo -f wav - | neroAacEnc -ignorelength -if - -of audio.aac
```
Now combine with FFmpeg:
```
ffmpeg -i video.mp4 -i audio.aac -vcodec copy -acodec copy muxed.mp4
```
or MP4Box (part of the **gpac** package):
```
MP4Box -add hdvideo.mp4 -add audio.aac muxed.mp4
```
or mkvmerge (part of the **mkvtoolnix** or **mkvtoolnix-gui** packages):
```
mkvmerge -o muxed.mkv video.mp4 audio.aac
```
or MEncoder (I think it can do this).

---

