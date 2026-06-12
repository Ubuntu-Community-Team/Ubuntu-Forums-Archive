---
title: "FFmpeg 0.5 in Jaunty?"
date: 2009-03-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by olskar on 2009-03-10
Will FFmpeg 0.5 be in Jaunty?

With FFmpeg 0.5 there is a plethora of new audio/video file decoders and encoders, a new meta-data API, cleaner code, ffserver fixes, new muxers / demuxers, and various other features. Among the new decoders are for RealVideo RV30/40, MLP/TrueHD, Flash Screen Video, Monkey's Audio, and many other formats. There is also NVIDIA VDPAU support in FFmpeg.

---

### Post by JohnJackson on 2009-03-10
There is a bug filed about it [here]("https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/340303")

---

### Post by raggari on 2009-03-10
> **olskar said:**
> Will FFmpeg 0.5 be in Jaunty?

With FFmpeg 0.5 there is a plethora of new audio/video file decoders and encoders, a new meta-data API, cleaner code, ffserver fixes, new muxers / demuxers, and various other features. Among the new decoders are for RealVideo RV30/40, MLP/TrueHD, Flash Screen Video, Monkey's Audio, and many other formats. There is also NVIDIA VDPAU support in FFmpeg.

Current version is snapshot form one month ago:
[http://packages.ubuntu.com/jaunty/ffmpeg](http://packages.ubuntu.com/jaunty/ffmpeg)

Most of 0.5 listed stuff is already there.

---

### Post by asimon on 2009-03-10
A release of ffmpeg? What comes next, Duke Nukem Forever?

---

### Post by eyelessfade on 2009-03-10
...or mplayer 1.0?

---

### Post by Nullack on 2009-03-10
> **raggari said:**
> Current version is snapshot form one month ago:
[http://packages.ubuntu.com/jaunty/ffmpeg](http://packages.ubuntu.com/jaunty/ffmpeg)

Most of 0.5 listed stuff is already there.


The CVS commit mail list for ffmpeg has quite a few changes since though.

---

### Post by ronacc on 2009-03-10
ffmpeg 0.5 release builds fine in Jaunty , get it here  [http://ffmpeg.org/download.html](http://ffmpeg.org/download.html)

---

### Post by plun on 2009-03-11
a good interview/article from Phoronix

[http://www.phoronix.com/scan.php?page=article&item=ffmpeg_05_interview&num=1](http://www.phoronix.com/scan.php?page=article&item=ffmpeg_05_interview&num=1)

3 pages...

> In the past six months there have been 42 people that made at least one commit to their SVN server while 31 of those made ten or more commits. Of the 42 developers, about a dozen of those are extremely active within the FFmpeg community making 50 or more commits during the same period. There are also other open-source enthusiasts involved with providing support through IRC, maintaining the mailing list, running FFmpeg tests, and related activities.


;)

---

### Post by Yashiro on 2009-03-12
> ffmpeg 0.5 release builds fine in Jaunty , get it here [http://ffmpeg.org/download.html](http://ffmpeg.org/download.html)This is not the same as being available as a package is it.

---

### Post by olskar on 2009-03-19
Now it's in! :)

---

### Post by phenest on 2009-03-21
The man pages are old though. Does anyone know how to use the new -metadata option? I can add a title with:
```
-metadata "title=This is the title"
```
... but I can't add an album, etc.

---

### Post by FakeOutdoorsman on 2009-03-21
It worked for me like this:
```
-metadata title=foo -metadata author=blah
```
An ugly way to do it.  I couldn't figure out how to set more than one string at a time.

---

### Post by phenest on 2009-03-21
Yeah, that works, and artist works too, but what about album and other tags? I can't seem to figure the others out.

---

