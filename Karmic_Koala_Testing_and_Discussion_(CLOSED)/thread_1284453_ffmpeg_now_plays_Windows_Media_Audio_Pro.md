---
title: "ffmpeg now plays Windows Media Audio Pro"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by eyelessfade on 2009-10-06
As of September 23, ffmpeg which means that also mplayer plays Windows Media Audio Pro.

from ffmpeg.org
> One of the last entrenchments of proprietary multimedia has fallen: Windows Media Audio Pro support is finally available in FFmpeg. It decodes all known samples flawlessly and is considerably faster than the binary decoder from Microsoft. A big thank you goes out to all the reverse engineers and programmers who made this possible. It really was a herculean effort.

I hope this will be included in karmic, if not or for those who can't wait there is hope. [https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

---

### Post by andrew.46 on 2009-10-06
Hi eyelessfade,

> **eyelessfade said:**
> I hope this will be included in karmic, if not or for those who can't wait there is hope. [https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

It is indeed great news. Mind you, if you were referring to MPlayer it has been able to play these files for a while using an *exernal* codec but certainly the use of ffwmapro is a great step forward, in particular for 64bit versions which could not use this codec. As well as RVM's PPA there should be a guide to compiling your own current MPlayer under Karmic as well, an early version is [here]("http://ubuntuforums.org/showthread.php?t=1280543").

All the best,

Andrew

---

### Post by eyelessfade on 2009-10-06
Not for x86_64.

---

### Post by andrew.46 on 2009-10-06
Hi eyelessfade,

> **eyelessfade said:**
> Not for x86_64.

Very true, it is* excellent* news for 64bit users :). Here it is running:

```

andrew@skamandros~/Desktop$ mplayer newOrleans_192_mulitchannel.wma 
MPlayer SVN-r29748-4.3.3 (C) 2000-2009 MPlayer Team

Playing newOrleans_192_mulitchannel.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 title: 
 author: 
 copyright: 
 comments: 
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 6 ch, floatle, 192.0 kbit/2.08% (ratio: 24000->1152000)
**[COLOR="Red"]Selected audio codec: [ffwmapro] afm: ffmpeg (WMA Pro audio (FFmpeg))[/COLOR]**
==========================================================================
AO: [oss] 48000Hz 6ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  60.9 (01:00.8) of 61.0 (01:01.0)  1.4% 

Exiting... (End of file)

```

and the atrac3 playback as well (featured next to the wmapro news):

```

andrew@skamandros~/Desktop$ mplayer sample.ATRAC3.66kbps.44100Hz.Stereo.wav 
MPlayer SVN-r29748-4.3.3 (C) 2000-2009 MPlayer Team

Playing sample.ATRAC3.66kbps.44100Hz.Stereo.wav.
Audio only file format detected.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 66.1 kbit/4.69% (ratio: 8268->176400)
**[COLOR="Red"]Selected audio codec: [ffatrc] afm: ffmpeg (FFmpeg Atrac 3 audio)[/COLOR]**
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   4.1 (04.0) of 4.0 (04.0)  0.9% 

Exiting... (End of file)

```

It is a great time to be using MPlayer!!!

Andrew

---

### Post by mc4man on 2009-10-06
> I hope this will be included in karmic

It was said to me fairly clearly that the will be no update to ffmpeg in karmic, backports was mentioned but I doubt it will go that far. 

So a mplayer build or ppa like rvm's remains the best choice. 

For vlc ( which announced native wmapro decoding in 1.0.2) you would need to provide your own wmapro enabled ffmpeg shared libs. ( and from what I can tell not use a ffmpeg -r greater than r 19777
Ongoing vlc thread [here]("http://forum.videolan.org/viewtopic.php?f=13&t=66047") that got off on wrong foot but may be productive, may not

(mplayer by far has the most sane approach to  ffmpeg

---

### Post by Nullack on 2009-10-06
When is this in ffmpeg's gstreamer plugin?

I used to patch ffmpeg libraries in mplayer builds for this but its nice to know its finally been put into the main code.

---

### Post by mc4man on 2009-10-06
> When is this in ffmpeg's gstreamer plugin?
In all likelihood not until gstreamer decides to add it or use a more current ffmpeg source in the plug-in. (would probably also require a wmapro enabled libavcodecXX installed in system

When i moved my hardy install to a package install of current ffmpeg and shared libs I had to also rebuild some of the gst plugins to maintain install deps.

They don't acquire any of the new 'enables' from the -devs or the shared libs, though do maintain prior 'enables'

I believe I did look at both trying to replace and or use use an external ffmeg in build but that proved problematic though probably not impossible ( and is specifically warned against

 > WARNING: you have chosen to build gst-ffmpeg against a random
   external version of ffmpeg instead of building it against the tested
   internal ffmpeg snapshot that is included with gst-ffmpeg.
   
   This is a very bad idea.  So bad in fact that words cannot express
   just how bad it is.  Suffice to say that it is BAD.
   

I don't remember if I  tried to patch the included ffmpeg sources, though if at all possible then you'd need to match the included source version with the appropriate wmapro patch version ( and other adj. probably would need to be made

---

### Post by Nullack on 2009-10-06
According to the last ffmpeg release notes at:

[http://gstreamer.freedesktop.org/releases/gst-ffmpeg/0.10.9.html](http://gstreamer.freedesktop.org/releases/gst-ffmpeg/0.10.9.html)

Update FFmpeg snapshot to SVN 19580 on the 0.5 branch

So what SVN commit number was wmapro merged into the mainline trunk?

---

### Post by mc4man on 2009-10-06
Ironically the so called 0.5 release ( from 03/03) was the only one I could never patch

Remembering back to your post in the mplayer-jaunty how-to, the wmapro patch worked that day, then started failing. This was at first due to a failure to find bitstream.h, though grabing the file from the 0.5 source resolved that for a bit.

Then there were a series of name and slight code changes, (bitstream.h to get_bits.h, wma3dec to wmaprodec ect., ect. ( the last month or so before the inclusion only the line numbers of where to apply changed.


I may have mentioned an -r # in one of my posts after your initial one, or a link to a post where I did..

You'd be looking for a wmapro -r from around that #

if the actual 0.5 source can't be patched, maybe a substitution from an ffmpeg -r in the immediate neighbourhood...?

( I did manage to get gstreamer apps to play wma3 in hardy, but only 9.1, not 10 though I think it was thru dmo, not ffmpeg 

I've not atm been able to get wma3 playback in gstreamer at all in karmic

---

