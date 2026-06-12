---
title: "VDPAU on Gstreamer / Totem"
date: 2008-12-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-12-23
Do I understand correctly that VDPAU wont work on gstreamer/totem?

Thanks

---

### Post by RAOF on 2008-12-24
Certainly there are no GStreamer elements that support it right at this moment.  It's not impossible to write them, though.  IIRC mplayer has applied a patch to add support, so that works, and nothing else does.

Given that VDAPU only works on new nVidia cards, and there are at least 2 other new HW video decoding APIs available, maybe it just makes more sense to do what gst-plugins-gl is doing and write decoders in GLSL? :)

---

### Post by TomaszD on 2008-12-24
Isn't GStreamer just wrapping around FFmpeg? As soon as FFmpeg gets VDPAU support, so will GStreamer. Am I right? 

So Xine, mplayer and VLC have or will have VPDAU support in the near future. Now it's FFmpeg's turn.

---

### Post by gnomeuser on 2008-12-24
> **TomaszD said:**
> Isn't GStreamer just wrapping around FFmpeg? As soon as FFmpeg gets VDPAU support, so will GStreamer. Am I right? 


No, it wraps ffmpeg for some codec support but most codecs have seperate elements.

---

### Post by vhaarr on 2008-12-24
> **Nullack said:**
> Do I understand correctly that VDPAU wont work on gstreamer/totem?

Not until someone implements it.
[http://bugzilla.gnome.org/show_bug.cgi?id=561225](http://bugzilla.gnome.org/show_bug.cgi?id=561225)

---

### Post by vhaarr on 2008-12-24
> **TomaszD said:**
> So Xine, mplayer and VLC have or will have VPDAU support in the near future. Now it's FFmpeg's turn.

ffmpeg is a mplayer project and has already been patched by nvidia to support vdpau video out, you can get the sources on the nvnews.net forums.

---

### Post by RAOF on 2008-12-24
> **gnomeuser said:**
> No, it wraps ffmpeg for some codec support but most codecs have seperate elements.

And even when the ffmpeg snapshot gst-ffmpeg is based on is updated to a version of ffmpeg that supports VPDAU, gst-ffmpeg still won't support VPDAU without extra modifications.  VPDAU would need to be implemented in GStreamer as a separate sink.

---

### Post by Nullack on 2008-12-24
Yes a generic solution would be better overall, if such a solution could be just as fast as a HW specific library like VDPAU.

---

### Post by zekopeko on 2008-12-25
why don't they/we/devs just wait for AMD,Intel and Nvidia to implement OpenCL in their drivers and then they have only one interface to work with?

---

### Post by plun on 2008-12-25
> **zekopeko said:**
> why don't they/we/devs just wait for AMD,Intel and Nvidia to implement OpenCL in their drivers and then they have only one interface to work with?

Well... the world is a market place and not a monopoly.

VDPAU is about playing Video files with often software patents involved.

It also uses a special GPU function.


Everything about it:
[http://www.phoronix.com/scan.php?page=article&item=nvidia_180_vdpau&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_180_vdpau&num=1)

> **So what's VDPAU?** The Video Decode and Presentation API for Unix. It is currently able to accelerate the decoding of MPEG-1, MPEG-2, H.264, and VC-1 bitstreams. It also provides an API for post-processing of decoded video (to apply such operations as temporal and spatial deinterlacing and noise reduction), timestamp-based presentation of final video frames, and compositing of sub-picture elements. NVIDIA's developer documentation describes it as:


And the largest "abusing" player today is Intel...
[http://europa.eu/rapid/pressReleasesAction.do?reference=MEMO/08/517&format=HTML&aged=0&language=EN&guiLanguage=en](http://europa.eu/rapid/pressReleasesAction.do?reference=MEMO/08/517&format=HTML&aged=0&language=EN&guiLanguage=en)

Hopefully AMD/ATI comes up with a alternate solution but software patents will for sure be involved...

---

### Post by RAOF on 2008-12-25
> **plun said:**
> Well... the world is a market place and not a monopoly.


Except that it's annoying and mostly useless to have multiple competing standards to do exactly the same thing.

> **plun said:**
> 
VDPAU is about playing Video files with often software patents involved.


"Often" with software patents involved?  Heh.  It's quite easy to tell if the decoder for a video file requires the use of a patent: is it ogg theora or dirac?  If so, probably[1].  If not, definately.

> **plun said:**
> 
Hopefully AMD/ATI comes up with a alternate solution but software patents will for sure be involved...
You might notice that the article you linked mentioned the XvBA system already implemented in the fglrx drivers.  Yes, patents will be involved; these APIs are for hardware acceleration of patented codecs.

I don't see how the complaint about Intel is relevant.

[1] But there are no *known* patents required here.

---

### Post by plun on 2008-12-25
> **RAOF said:**
> Except that it's annoying and mostly useless to have multiple competing standards to do exactly the same thing.



"Often" with software patents involved?  Heh.  It's quite easy to tell if the decoder for a video file requires the use of a patent: is it ogg theora or dirac?  If so, probably[1].  If not, definately.


You might notice that the article you linked mentioned the XvBA system already implemented in the fglrx drivers.  Yes, patents will be involved; these APIs are for hardware acceleration of patented codecs.

I don't see how the complaint about Intel is relevant.

[1] But there are no *known* patents required here.

Well... the world isn't just Black or White.

The world is also blue, green, red, and so on.

There are tons with software patents involved for playing High Definition files... also probably within a ATI driver...  rv7XX and up...

There are also maybe more important issuses such as abusing market players...  despite of so called "open source".

The black & white scenario is just a terrible trap and keeps Linux around 1% usage...  IMHO..:(

---

### Post by gnomeuser on 2008-12-25
> **RAOF said:**
> Except that it's annoying and mostly useless to have multiple competing standards to do exactly the same thing.



"Often" with software patents involved?  Heh.  It's quite easy to tell if the decoder for a video file requires the use of a patent: is it ogg theora or dirac?  If so, probably[1].  If not, definately.


You might notice that the article you linked mentioned the XvBA system already implemented in the fglrx drivers.  Yes, patents will be involved; these APIs are for hardware acceleration of patented codecs.

I don't see how the complaint about Intel is relevant.

[1] But there are no *known* patents required here.

There was also a GoC project to implement a generic video acceleration framework with a reference software fallback and a partial implementation on the nouveau driver. I don't know how well this works nor if it really fits the bill but here we go for adding more references to the debate:

[http://www.bitblit.org/gsoc/g3dvl/](http://www.bitblit.org/gsoc/g3dvl/)

---

### Post by plun on 2008-12-25
Some more maybe important facts from Windows 7 to add to this black & white scenario

Maybe a new important color :confused:

[http://apcmag.com/windows_7_surprise_divx_built_in.htm](http://apcmag.com/windows_7_surprise_divx_built_in.htm)

> By bundling a wide variety of media formats into Windows 7, Microsoft has created an operating environment which negates the need for third-party codecs and should therefore run more stably and reliably. It also brings blanket support for the most popular online media formats, providing an environment in which users can start playing their favourite content immediately


Except Apples Itunes.....:-\"

---

### Post by Nullack on 2008-12-25
Plun MPEG4-ASP is on its last legs in comparison to VC1 and AVC. Im sure the patent pool owners for it sold a cheap licence.

---

### Post by RAOF on 2008-12-25
> **plun said:**
> ...
The black & white scenario is just a terrible trap and keeps Linux around 1% usage...  IMHO..:(

Yes.  We're terrorised by the rampant standardisation of APIs!  It's not particularly helpful to have 3 different APIs to do exactly the same thing.

> **gnomeuser said:**
> There was also a GoC project to implement a generic video acceleration framework with a reference software fallback and a partial implementation on the nouveau driver. I don't know how well this works nor if it really fits the bill but here we go for adding more references to the debate:

[http://www.bitblit.org/gsoc/g3dvl/](http://www.bitblit.org/gsoc/g3dvl/)

I did some testing for that; it works, as long as the video wasn't too big (720p worked, 1080p failed).  The biggest problem is that it (currently) only supports XvMC, which means that it only supports MPEG 1 or 2 decoding, which no-one cares about.

---

### Post by plun on 2008-12-26
> **RAOF said:**
> Yes.  We're terrorised by the rampant standardisation of APIs!  It's not particularly helpful to have 3 different APIs to do exactly the same thing.



Well.. I just dont want any monopoly and Intel is a "dominant player", for the moment its more important at least for me.

This also just came up:

[B]Intel insists Atom only for Intel chipsets, does not want to share Nvidia's Ion
[/B]

[http://www.digitimes.com/news/a20081223PD216.html](http://www.digitimes.com/news/a20081223PD216.html)

Most important is more users to Linux...but now it seems to be more important to build barriers and strange "killing me softly" doctrins... example Fedora 10,   just sad..:(

---

### Post by plun on 2008-12-26
> **Nullack said:**
> Plun MPEG4-ASP is on its last legs in comparison to VC1 and AVC. Im sure the patent pool owners for it sold a cheap licence.

Well...  I have not seem "the market" served that format or PirateBay..:twisted:

---

### Post by RAOF on 2008-12-26
> **plun said:**
> Well.. I just dont want any monopoly and Intel is a "dominant player", for the moment its more important at least for me.
...

It doesn't matter *who* the API is originally designed by, as long as
[list]
[*] It's open, and
[*] It's suitably abstract so that everyone can implement it performantly.
[/list]

As long as VDPAU satisfies both criteria, I'd be happy to see it become the standard.  Or VA-API.  Or XvBA.  Or whatever.  Just as long as we don't have to write, debug, and support 3 different video backends in all the multimedia systems.

---

