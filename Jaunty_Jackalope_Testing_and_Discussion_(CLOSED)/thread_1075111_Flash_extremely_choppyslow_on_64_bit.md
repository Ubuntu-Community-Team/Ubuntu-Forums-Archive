---
title: "Flash extremely choppy/slow on 64 bit"
date: 2009-02-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by no1wantdthisname on 2009-02-19
Anyone else seeing extremely choppy playback for flash?
It's easy to see this on HD videos from gametrailers.

It's slow using Flash from the ubuntu repo and the native 64 bit version.
I tried using a fresh firefox profile and even removed pulseaudio and it was still slow.

Cpu: intel core2 duo 2.20ghz
Video card: Nvidia 8600m gt
/ is ext4.
/home is ext3.

I have intrepid on another partition, and it works fine.  Intrepid is using 180.29 too.

---

### Post by halfsane on 2009-02-20
I am seeing the same thing with flash,  it is choppy then actually freezes most of the time. 

I also noticed this with files on my hdd using movie player.  When I try VLC it last longer without choppiness then crashes.


is it related?  i have no idea.

---

### Post by Tich666 on 2009-02-20
Well, flash on linux sucks, period.
I'm running the 32 bit version and can't even play "HD" videos on youtube or regular ones when using fullscreen (not to mention the screwed up aspect ratio).

I can't wait for the HTML 5 implementation in FF 3.1 which will include audio and video elements. Here's hope for a better and FREE future for streaming media.
[https://developer.mozilla.org/En/Using_audio_and_video_in_Firefox](https://developer.mozilla.org/En/Using_audio_and_video_in_Firefox)

---

### Post by durand on 2009-02-20
> **Tich666 said:**
> Well, flash on linux sucks, period.
I'm running the 32 bit version and can't even play "HD" videos on youtube or regular ones when using fullscreen (not to mention the screwed up aspect ratio).

I can't wait for the HTML 5 implementation in FF 3.1 which will include audio and video elements. Here's hope for a better and FREE future for streaming media.
[https://developer.mozilla.org/En/Using_audio_and_video_in_Firefox](https://developer.mozilla.org/En/Using_audio_and_video_in_Firefox)

Strange, I've never really had a problem with flash on linux. HD videos work fine in vimeo, youtube and iplayer.

---

### Post by mano cazalet on 2009-02-20
here its choppy to
very choppy in firefox (both 3.06 and 3.1)
and not so choopy in opera 9.63 or 10 alpha

---

### Post by halfsane on 2009-02-20
again, not sure if my problem was related to the OP, but todays updates seems to have fixed my issues.

---

### Post by durand on 2009-02-21
> **mano cazalet said:**
> here its choppy to
very choppy in firefox (both 3.06 and 3.1)
and not so choopy in opera 9.63 or 10 alpha

Oh, I only use opera so I can't really say anything about FF.

---

### Post by Poleh on 2009-04-17
yup, I get extremely choppy playback with both the 64-bit pre-release and the 32-bit plugin. However, I only seem to see performance problems from within Opera, when I flick to FF it works fine.

Using 8.10 x64, Opera 9.64, Dell XPS M1530 Dual core, 4GB - Any other Opera users seeing something similar?

---

### Post by Peasantoid on 2009-04-17
Works great for me.

* CPU: Intel Core 2 Duo, 2.2 GHz
* RAM: 4 GB
* Graphics: Intel GMA X3100
* OS: Ubuntu Hardy Heron, 64-bit, all updates installed

---

### Post by durand on 2009-04-17
> **Poleh said:**
> yup, I get extremely choppy playback with both the 64-bit pre-release and the 32-bit plugin. However, I only seem to see performance problems from within Opera, when I flick to FF it works fine.

Using 8.10 x64, Opera 9.64, Dell XPS M1530 Dual core, 4GB - Any other Opera users seeing something similar?

As I said above, it's not choppy but there is some lag problem.
Ubuntu 9.04/Opera 10/etc

---

### Post by Peasantoid on 2009-04-17
> **durand said:**
> As I said above, it's not choppy but there is some lag problem.
Ubuntu 9.04/Opera 10/etc
What sort of lag? Do you mean the sound starts a while after you hit play and keeps going after you hit pause?

I get that too. Something to do with PulseAudio, I think. (?)

---

### Post by durand on 2009-04-17
> **Peasantoid said:**
> What sort of lag? Do you mean the sound starts a while after you hit play and keeps going after you hit pause?

I get that too. Something to do with PulseAudio, I think. (?)

Yeah, sometimes but it just seems more clunky than if I used firefox.

---

### Post by novafluxx on 2009-04-17
I've noticed some choppyness and sluggishness as well during flash games. Just remember the native 64-bit flash plugin from Adobe *IS* an alpha release. Also make sure you're using the latest alpha from February.

I hope the future of media on the internet is open and free as well...here's to the audio and video HTML in Firefox 3.5!

---

### Post by Reiger on 2009-04-17
> **Poleh said:**
> yup, I get extremely choppy playback with both the 64-bit pre-release and the 32-bit plugin. However, I only seem to see performance problems from within Opera, when I flick to FF it works fine.

Using 8.10 x64, Opera 9.64, Dell XPS M1530 Dual core, 4GB - Any other Opera users seeing something similar?

Atm, I don't get any video with Opera 10 on Jaunty 64bit using the 32bit plugin. I the get sound, though. :)

---

### Post by Reiger on 2009-04-18
Opera 10 with 64bit prerelease flash works fine, though.

---

