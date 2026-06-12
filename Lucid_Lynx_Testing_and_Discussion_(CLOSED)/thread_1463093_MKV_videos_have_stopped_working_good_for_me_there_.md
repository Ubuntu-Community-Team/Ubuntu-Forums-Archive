---
title: "MKV videos have stopped working good for me there not smooth"
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-26
MKV Movies and videos have stopped working good for me they freeze and there not smooth and my cpu is working at 100% something is very wrong with one of the recent updates possibly xorg driver or something like this.

---

### Post by gnomeuser on 2010-04-26
What are using to play the files?

---

### Post by bretzeltux on 2010-04-26
Hi there,

I am using (k)ubuntu 10.04 rc and I am really surprised to be able to play mkv 1080p video files very smoothly, no lags!

I just hope that you are not using the proprietary NVidia driver.
My installation is a vanilla nouveau 2d default ubuntu driver and I will not dare to install the NVidia. 

- I read that libvdpau1 is necessary to get back fluid mkv movies. 
but I 've not tried that yet.

I've done the update yesterday ( apr. 25 ) and I see no lags in a 1080p movie yet ...

Good luck

---

### Post by aviramof on 2010-04-26
i'v tried with smplayer vlc and totem and not long ago everything was fine and i am using the proprietary ati driver from jockey and i have libvdpau1 installed and it's not mplayer problem i'v verified it.

could it be caused by the vlc update today that updated libx264-83 to libx264-94 and some other updates?

Update:
you know what i'm going back to windows untill all this problems would be fixed watching 720p and 1080p movies is pretty much the only thing i do with my computer and now it's also not working so will see what up with ubuntu much later.

---

### Post by gnomeuser on 2010-04-26
vdpau is an nvidia technology as I recall, it wouldn't be needed for ATI.

I personally use a pretty stock Ubuntu install and I bought the Fluendo GStreamer plugins. On this Acer Aspire Revo r3610 (a dual core ATOM nettop box) I play back HD content fluidly using the builtin VDPAU acceleration in the codec pack.

It works very well and I get a licensed solution - not that I need one, no software patents in Denmark but someone has to test them and it's a one click solution that just works(tm) to getting accelerated playback on my machine in applications I like rather than messing about with mplayer or vlc settings.

---

### Post by Winter Skies on 2010-04-26
1. Vdpau will work only with nvidia card.

2. You probably installed vlc from ppa try vlc from lucid repositories.

3. There is no chance for smooth playback of 1080p without hardware 
acceleration.

---

### Post by aviramof on 2010-04-26
i have updated vlc from the ppa but now i don't know how to clean it up completely i'v installed ppa-purge package but sudo ppa-purge ppa:webupd8 don't work
Warning:  Could not find package list for PPA: ppa:webupd8 ppa:webupd8

could it be nautilus elementary i installed recently?

---

### Post by Winter Skies on 2010-04-26
1. Remove vlc via Synaptic Package Manager, remove libx264-83
   or libx264-94 whatever version you have.

2. Remove webupd8 ppa from Software Sources. 

3. Update, install vlc, install libx264-85.

---

### Post by Longinus00 on 2010-04-26
> **Winter Skies said:**
> 3. There is no chance for smooth playback of 1080p without hardware 
acceleration.

This is patently false. I have smooth 1080p playback on a 1.6ghz core duo so long as I use multithreaded mplayer. Even in windows I don't need to enable gpu offloading to get smooth playback.

---

### Post by Winter Skies on 2010-04-26
> **Longinus00 said:**
> This is patently false. I have smooth 1080p playback on a 1.6ghz core duo so long as I use multithreaded mplayer. Even in windows I don't need to enable gpu offloading to get smooth playback.

Interesting.

1080p throw to knees my e8400, 1080i is even worse.

And word (smooth) mean 60fps.

If you playing 1080p and 1080i at 60fps on 1.6ghz then I think 
your cpu is magic.

---

### Post by aviramof on 2010-04-26
I Have formated again for the hundred time i was amazed to discover that grub 2 again did not installed itself automatically and that is an RC version i have tried to add as minimum ppa as i can and so far everything is working fine let's hope it stays like this but i really didn't like the fact that it so easy to destroy this os i only reinstalled it three days ago and one stable not unstable ppa can ruin it i have not decided if it was vlc or nautilus elementary that caused the problem in the end.

---

### Post by psyke83 on 2010-04-26
> **Winter Skies said:**
> 
And word (smooth) mean 60fps.

Most video content is encoded at a lower FPS rating (usually ~24) - this is because "real" video contains motion blur, which helps our eyes perceive a more fluid motion.

Maybe it's necessary to have 60fps (or the rate of your monitor) if video playback needs to be vertically synchronized with compiz, I dunno.

---

### Post by aviramof on 2010-04-26
my problem was not caused by compiz or metacity although i can't run mkv videos 
good with compiz so i use metacity for that but in any case it has to be and update 
from one of ppa i added most likely vlc but who knows.

---

### Post by mc4man on 2010-04-26
> from one of ppa i added most likely vlc but who knows. 
A few things to consider there..
If you enable a ppa that's not app specific then you may update other packages then the one you added the ppa for.

As far as the vlc build you were getting - while it's now a 'pre', it's still a dev. version and still should be considered unstable.
What worked well previously may not today, may work even better a few days from now - a bit of an unknown day to day.

The ppa is only building once and a while (2 builds in 2 months), you really shouldn't have any expectation it will work perfectly for your particular use.

Any update to vlc and the addition of the libx264-94 package would have no impact on other players such as mplayer

---

### Post by splicerr on 2010-04-26
> **Winter Skies said:**
> Interesting.

1080p throw to knees my e8400, 1080i is even worse.

And word (smooth) mean 60fps.

If you playing 1080p and 1080i at 60fps on 1.6ghz then I think 
your cpu is magic.

Well, there's 1080p and there's 1080p ;). He is probably using low-bitrate files.

---

### Post by kerry_s on 2010-04-26
1080p is a pain on my atom 1.6 1gb ram, i had 1 last night i had to add several more settings to get it to play smooth using gnome-mplayer.

```

-nodouble -lavdopts skipframe=nonref:skiploopfilter=all:fast=1 -cache-min 75

```

those settings should make most anything run, with little cpu overhaead.

---

### Post by Longinus00 on 2010-04-26
> **Winter Skies said:**
> Interesting.

1080p throw to knees my e8400, 1080i is even worse.

And word (smooth) mean 60fps.

If you playing 1080p and 1080i at 60fps on 1.6ghz then I think 
your cpu is magic.

Smooth means full fps of the video.
```
$ grep -m 1 "model name" /proc/cpuinfo
model name	: Genuine Intel(R) CPU           T2300  @ 1.66GHz
$ mplayer -benchmark -vo null -nosound -lavdopts threads=2 trailers_fox_lightningthief-tlr1_h1080p.mov
MPlayer UNKNOWN-4.3.4 (C) 2000-2010 MPlayer Team

Playing trailers_fox_lightningthief-tlr1_h1080p.mov.
Cache fill:  0.00% (0 bytes)   
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [H264]  1920x800  24bpp  23.976 fps  10772.1 kbps (1314.9 kbyte/s)
Clip info:
 major_brand: qt  
 minor_version: 537199360
 compatible_brands: qt  
 comment: Encoded and delivered by apple.com/trailers/
 comment-eng: Encoded and delivered by apple.com/trailers/
 copyright: &#65533; 2009 20th Century Fox. All Rights Reserved
 copyright-eng: &#65533; 2009 20th Century Fox. All Rights Reserved
 title: Percy Jackson & The Olympians: Lightning Thief
 title-eng: Percy Jackson & The Olympians: Lightning Thief
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Audio: no sound
Starting playback...
Movie-Aspect is undefined - no prescaling applied.
VO: [null] 1920x800 => 1920x800 Planar YV12 
V:  92.0   0/  0 30%  0%  0.0% 0 0 0% 

BENCHMARKs: VC:  28.168s VO:   0.011s A:   0.000s Sys:   0.447s =   28.625s
BENCHMARK%: VC: 98.4029% VO:  0.0370% A:  0.0000% Sys:  1.5600% = 100.0000%

Exiting... (End of file)

```
```
$ grep -m 1 "model name" /proc/cpuinfo
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
$ mplayer -benchmark -vo null -nosound -lavdopts threads=2 trailers_fox_lightningthief-tlr1_h1080p.mov
MPlayer SVN-r31044-4.4.1 (C) 2000-2010 MPlayer Team

Playing trailers_fox_lightningthief-tlr1_h1080p.mov.
Cache fill:  0.00% (0 bytes)   
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [H264]  1920x800  24bpp  23.976 fps  10772.1 kbps (1314.9 kbyte/s)
Clip info:
 major_brand: qt  
 minor_version: 537199360
 compatible_brands: qt  
 comment: Encoded and delivered by apple.com/trailers/
 comment-eng: Encoded and delivered by apple.com/trailers/
 copyright: © 2009 20th Century Fox. All Rights Reserved
 copyright-eng: © 2009 20th Century Fox. All Rights Reserved
 title: Percy Jackson & The Olympians: Lightning Thief
 title-eng: Percy Jackson & The Olympians: Lightning Thief
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Audio: no sound
Starting playback...
Movie-Aspect is undefined - no prescaling applied.
VO: [null] 1920x800 => 1920x800 Planar YV12 
V:  92.0   0/  0 16%  0%  0.0% 0 0 0% 

BENCHMARKs: VC:  15.317s VO:   0.005s A:   0.000s Sys:   0.270s =   15.592s
BENCHMARK%: VC: 98.2349% VO:  0.0314% A:  0.0000% Sys:  1.7337% = 100.0000%

Exiting... (End of file)

```
Enabling the optimizations stated in the previous post almost halve these benchmark times.

---

### Post by kerry_s on 2010-04-27
the only thing i care about is that i can watch the movie with out stutter or slow mo. :lolflag:

---

### Post by kerry_s on 2010-04-27
looks like the extra threads don't hurt so i added it:
```

-nodouble -lavdopts skipframe=nonref:skiploopfilter=all:fast=1:threads=8 -cache-min 75

```

i put it to the max 8, but it will only do what your cpu can handle, in my case it only does 2 for my atom 230 1.6ghz cpu.

---

### Post by aviramof on 2010-04-27
> **mc4man said:**
> 
Any update to vlc and the addition of the libx264-94 package would have no impact on other players such as mplayer

as far i can remember there are only two option updates from web8upd ppa or nautilus elementary and gloobus preview might have caused this.

---

### Post by Winter Skies on 2010-04-27
> **Longinus00 said:**
> Smooth means full fps of the video.

Enabling the optimizations stated in the previous post almost halve these benchmark times.

1.
No smooth for me means 60fps not 30fps look at this video you will hopefully understand.
[http://www.trbarry.com/CrowdRun_1024x576_50p_vs_25p.avi](http://www.trbarry.com/CrowdRun_1024x576_50p_vs_25p.avi)

2.
Your 1080p file plays fine on my e8400 at ~25fps but its low bitrate and have strange resolution 1920x800.

3.
My files have bitrate usually 20000 to 40000 kb/s at 1920x1080
and half of them require deinterlacing, no software player
that i have can play them (smoothly).

4. 
On my vista pc all my files are hardware accelerated the frame
rate is doubled and they are smooth as butter.

---

### Post by aviramof on 2010-04-27
on my windows 7 everything is working fine because there i have official ati driver not the jockey one i have here who is not even officialy released yet. 

but i never tried 20000 to 40000 kb/s video bit rate the max i had was 16MKBS so who knows how it work would work on my computer.

and the movie is working fine for me now and so does all the 720P tv series i download accept maybe a jump here and there.

---

### Post by kerry_s on 2010-04-27
> 1.
No smooth for me means 60fps not 30fps look at this video you will hopefully understand.
[http://www.trbarry.com/CrowdRun_1024x576_50p_vs_25p.avi](http://www.trbarry.com/CrowdRun_1024x576_50p_vs_25p.avi)


plays fine for me.

i been messing around & this seems to work best for avi, mp4, mkv at the cost of higher cpu.

```
-lavdopts skiploopfilter=all:threads=8 -cache-min 75
```

some movies needs drop frames on, others don't.

---

