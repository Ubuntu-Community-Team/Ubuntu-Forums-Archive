---
title: "How to play (and convert) WMA files"
date: 2009-09-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Ganymedes on 2009-09-06
I am trying to play WMA-files on Ubuntu 9.10, 64-bit. They seem to be lossless (bitrate 1074 kb/s Audio 0x0163 according to ffmeg info).

When using Totem to play, it will fail to get the plug-in.

I have also tried to convert the files, my goal is to get rid of a Windows dependency as much as I can, and for that purpose tried the Sound Converter application, the audio converter script in Nautilus, tried pacpl and loaded all kinds of apps and codecs's as suggested. But they all fail. Nautilus script just does nothing and stops very quickly. pacpl gives the following error:

Converting:  [01Bloom.wma] -> [mp3] decode failed with exit status: 256

I would assume that this is all because the system just cannot play (decode) the file.

Is there any way this can be done in Ubuntu at the moment?

(Sorry, this post slipped into a slightly wrong category - this should be in general Multimedia - please move this as you see fit).

---

### Post by hal10000 on 2009-09-06
Did you enable the medibunu repositories?
If you enable them, then i think totem should find the necessary plugins

---

### Post by Ganymedes on 2009-09-06
Thanks! Did not know about that. However, it still does not find the plugins. Neither does SoundConverter find the plugin. I get the error message, as attached, about Windows Media Audio decoder.

---

### Post by mc4man on 2009-09-06
> I am trying to play WMA-files on Ubuntu 9.10, 64-bit. They seem to be lossless (bitrate 1074 kb/s Audio 0x0163 according to ffmeg info)

> is there any way this can be done in Ubuntu at the moment?


3 ways on a 64 bit install for wma lossless

Thru **gstreamer apps only **with purchase of fluendo windows media pack

Build and install a 32 bit player and w32codecs - mplayer is best choice - if a gui is wanted then additionally install smplayer (64 bit smplayer will work with the 32 bit mplayer

run a  32 bit windows mplayer thru wine

---

### Post by Ganymedes on 2009-09-06
Thanks for the reply! Yes, I really want to explore what is possible and what is not.

I tried MPlayer, after all this, but it says that cannot find codecs for audio format 0x163 - I guess that is very much consistent with NOT having the right codecs for lossless WMA.

But, what I really want to do is to CONVERT - to get rid of these Windows files - and thus I do not really need a player - not that I actually, understood completely how the player is created :) .


As for Wine, yeah, I already can use VMware workstation and run Windows there and convert WMA-files.

So, I have a solution, but not without Windows.

Thanks for the help anyway - proprietary formats are a bitch. I already told the user to stop using them, but he does not care.

---

### Post by mc4man on 2009-09-06
> But, what I really want to do is to CONVERT - to get rid of these Windows files

Well  if you wanted to convert the wma lossless in a 64 bit install same thing, you need to build and install a 32 bit mplayer and then use mplayer to convert

Other than that nothing to  be done in the 64 bit install 

If you had a decent amount of memory you could boot to a live cd (32 bit) and convert there fairly quickly

---

### Post by Ganymedes on 2009-09-06
OK, thanks, this explains the situation.

Yeah, I can easily use Live-CD, or better still, have a 32-bit environment in VMware and run there the conversion.

Thank you for the help :)

---

### Post by trulan on 2009-09-06
For converting files, check out WinFF (it's a gui front end for the ffmpeg library).  I'm not at my ubuntu machine right now, but I know it works on 64 bit Jaunty and I am pretty sure it can convert from a wma to mp3, ogg, wav, whatever (provided you install the unstripped codecs).  Works pretty slick for batch converting files.  I'll test it out on a few wma's as soon as I get a chance and report back.

On second thought, if they won't play they probably won't decode.  I'll check it out...

---

### Post by Ganymedes on 2009-09-06
> **trulan said:**
> 
...
On second thought, if they won't play they probably won't decode.  I'll check it out...

Thanks for the reply!

Yes, decoding is the problem - according to error messages as well. Some other WMAs do play - properties in Totem says "WMA version 8" for those which work.

I also just checked, those which do play they can also be converted. I tried Sound Converter. So it is pretty solid that decoding causes both problems: playing and converting.

---

### Post by scragar on 2009-09-06
Have your tried VLC? Using it's save/convert options in the media menu you can(with a little practice) convert almost any format to any other.

---

### Post by Ganymedes on 2009-09-06
> **scragar said:**
> Have your tried VLC? Using it's save/convert options in the media menu you can(with a little practice) convert almost any format to any other.

Yes, I did try to play. It says this:

"No suitable decoder module:
VLC does not support the audio or video format "wmal". Unfortunately there is no way for you to fix this."

---

### Post by mc4man on 2009-09-06
Just to clear up 

For wma **lossless**
The only available decoder (other than the pay for fluendo) is a dmo in w32codes

If you can't use w32codecs than decoding is impossible

If you can use w32codecs than it works fine ( playback and or converting, extracting

side note
wma2 and wma3 can be decoded by both dmo (w32codecs) and avcodec (ffmpeg libs)

So in **64 bit** if your mplayer is built right playback, ect. works fine
If your vlc and libavcodec are built right same thing

---

### Post by Stochastic on 2009-09-07
Moved to Karmic Koala forum section.

---

### Post by trulan on 2009-09-07
> **mc4man said:**
> Just to clear up 

For wma **lossless**
The only available decoder (other than the pay for fluendo) is a dmo in w32codes

If you can't use w32codecs than decoding is impossible

If you can use w32codecs than it works fine ( playback and or converting, extracting

side note
wma2 and wma3 can be decoded by both dmo (w32codecs) and avcodec (ffmpeg libs)

So in **64 bit** if your mplayer is built right playback, ect. works fine
If your vlc and libavcodec are built right same thing
That indeed clears things up.  Thank you very much.

---

