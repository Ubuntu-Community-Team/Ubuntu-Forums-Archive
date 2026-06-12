---
title: "Is FFmpeg working with 12.04?"
date: 2013-12-12
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2013-12-12
What is the latest? Did the ongoing dispute with avconv and FFmpeg get resloved?
Used FFmpeg in the past. It worked great. Tried using it last night and get the message:
> *** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.

Is there a simple way or fix now, to get FFmpeg working again?

---

### Post by ajgreeny on 2013-12-12
You can compile it yourself if you want to, to get the full working version as the repo one is a little less than full working version on some HD codecs, or you can install the repo version and it will still mostly work as you expect it to, but as avconv does just the same job with almost the same syntax (and I could never remember that when using ffmpeg, but had to look it up) I generally use avconv instead.  It is less hard work compiling and messing about.

---

### Post by cybrsaylr on 2013-12-12
Yeah tried Google and got lots of conflicting results, so didn't know what to do.
Most said FFmpeg still works better than avconv.

FFmpeg syntax was never a problem since I just copy & pasted it and the only changes needed were for the pic and mp3 code.
You just put that code in, hit enter and FFmpeg did its thing beautifully.

It just I never compiled it myself and was hoping someone had the proper code to make it work again.

---

### Post by FakeOutdoorsman on 2013-12-12
The "deprecated" message was made intentionally vague&#8211;the Debian/Ubuntu package maintainer is the Libav release maintainer&#8211;so general users often assume "ffmpeg" (the fake version in the repo from the fork) refers to FFmpeg (the project).

If you want the real ffmpeg from FFmpeg, which I recommend since the fake version (and avconv) is old and buggy, then you have two major choices:

[size=5]Use a static build[/size]

Simply download, extract, and run a pre-built [binary of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds) (note the **./** before ffmpeg):
```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date +"%F").tar.gz
tar xzvf ffmpeg.static.32bit.$(date +"%F").tar.gz
./ffmpeg -i input ... output
```

[size=5]Compile ffmpeg[/size]
Refer to a [step-by-step guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide).

Neither method will interfere with repository packages. The build is easier, but compiling will allow you to customize it anyway you want. There's no reason to let politics or a maintainer make choices for you.

---

### Post by cybrsaylr on 2013-12-12
> **FakeOutdoorsman said:**
>  The build is easier....

Am assuming you mean the static build here?

So all needed is put in static build code in terminal
> wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date +"%F").tar.gz
tar xzvf ffmpeg.static.32bit.$(date +"%F").tar.gz
./ffmpeg -i input ... output
and I should be good to go?

---

### Post by FakeOutdoorsman on 2013-12-12
> **cybrsaylr said:**
> Am assuming you mean the static build here?
Yeah.

> **cybrsaylr said:**
> So all needed is put in static build code in terminal and I should be good to go?
That's the plan, and I wanted it to be as easy as possible, but results may vary due to time zones (due to the date command) and if the server is available. The first command downloads the most recent archive, the second command extracts the archive, and the third is an incomplete example of using ffmpeg.

If it does not download for you then you can download via your browser at the [FFmpeg Download](http://ffmpeg.org/download.html#LinuxBuilds) page.

---

### Post by cybrsaylr on 2013-12-13
FakeOutdoorsman, Thanks will give it a try when time permits.

---

### Post by cybrsaylr on 2013-12-13
Well put in that static build code you suggested in post 4 and it doesn't work.
Get the same *** THIS PROGRAM IS DEPRECATED *** message.

I'm stumped......

---

### Post by ajgreeny on 2013-12-13
There is a ppa for ffmpeg which you can enable for the updated version of "proper" ffmpeg.
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)

---

### Post by cybrsaylr on 2013-12-13
> **ajgreeny said:**
> There is a ppa for ffmpeg which you can enable for the updated version of "proper" ffmpeg.
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)

OK think I did that.

FFmpeg still won't work.
Was the FFmpeg code changed?
Tried using it and get this in terminal and know not what it means:
> rr@rr-Studio-XPS-8000:~$ ffmpeg -loop_input -i ~/Desktop/k.png -i ~/Desktop/k.mp3 -shortest -b 1000k -acodec copy video.mp4
ffmpeg version 0.10.9-7:0.10.9-1~precise1 Copyright (c) 2000-2013 the FFmpeg developers
  built on Oct  4 2013 06:37:30 with gcc 4.6.3
  configuration: --arch=amd64 --disable-stripping --enable-pthreads --enable-runtime-cpudetect --extra-version='7:0.10.9-1~precise1' --libdir=/usr/lib/x86_64-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
  libavutil      51. 35.100 / 51. 35.100
  libavcodec     53. 61.100 / 53. 61.100
  libavformat    53. 32.100 / 53. 32.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 61.100 /  2. 61.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  6.100 /  0.  6.100
  libpostproc    52.  0.100 / 52.  0.100
[color=orange]-loop_input is deprecated, use -loop 1
Note, both loop options only work with -f image2[/color]
Input #0, image2, from '/home/rr/Desktop/k.png':
  Duration: 00:00:00.04, start: 0.000000, bitrate: N/A
    Stream #0:0: Video: png, rgb24, 703x548, 25 fps, 25 tbr, 25 tbn, 25 tbc
[color=orange]-loop_input is deprecated, use -loop 1
Note, both loop options only work with -f image2
[mp3 @ 0xfe6da0] max_analyze_duration 5000000 reached at 5015510
[mp3 @ 0xfe6da0] Estimating duration from bitrate, this may be inaccurate[/color]
Input #1, mp3, from '/home/rr/Desktop/k.mp3':
  Metadata:
    title           : Blow Your Own Pt. 2 [ft Kathrin DeBoer]
    artist          : Aaron Jerome
    album           : Time to Rearrange
    album_artist    : Aarron Jerome
    genre           : Jazz
    track           : 10
    disc            : 1
    date            : 2007
  Duration: 00:04:52.49, start: 0.000000, bitrate: 320 kb/s
    Stream #1:0: Audio: mp3, 44100 Hz, stereo, s16, 320 kb/s
[color=orange]Please use -b:a or -b:v, -b is ambiguous[/color]
File 'video.mp4' already exists. Overwrite ? [y/N] y
[color=orange]Incompatible pixel format 'rgb24' for codec 'libx264', auto-selecting format 'yuv420p'[/color]
[buffer @ 0xfdf780] w:703 h:548 pixfmt:rgb24 tb:1/1000000 sar:0/1 sws_param:
[buffersink @ 0xfe85a0] auto-inserting filter 'auto-inserted scale 0' between the filter 'src' and the filter 'out'
[scale @ 0xfde840] w:703 h:548 fmt:rgb24 -> w:703 h:548 fmt:yuv420p flags:0x4
[color=red][libx264 @ 0x1000280] width not divisible by 2 (703x548)[/color]
Output #0, mp4, to 'video.mp4':
    Stream #0:0: Video: h264, yuv420p, 703x548, q=-1--1, 1000 kb/s, 90k tbn, 25 tbc
    Stream #0:1: Audio: mp3, 44100 Hz, stereo, 320 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (png -> libx264)
  Stream #1:0 -> #0:1 (copy)
[color=red]Error while opening encoder for output stream #0:0 - maybe incorrect parameters such as bit_rate, rate, width or height[/color]

---

### Post by ajgreeny on 2013-12-14
Sorry, but I don't think I can help you further with this.

As I said, I use avconv and have only the "dummy" ffmpeg installed from the repos of 12.04.  I find avconv does all I need, so I haven't looked into which of the two packages is the better

---

### Post by cybrsaylr on 2013-12-14
Wasn't sure about avconv.
Maybe will give avconv a spin.

---

### Post by erind on 2013-12-14
> **cybrsaylr said:**
> OK think I did that.

FFmpeg still won't work.
Was the FFmpeg code changed?
Tried using it and get this in terminal and know not what it means:

You might need to remove some packages before installing the real ffmpeg. I usually go for the easy way by adding the *jon-severinsson*'s ppa and then doing a normal install. Paste the following commands in order:
```
sudo apt-get purge libav-tools
sudo add-apt-repository ppa:jon-severinsson/ffmpeg
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install ffmpeg
```

Taken from the 1st link below:
[http://askubuntu.com/questions/373322/how-to-replace-avconv-with-the-real-ffmpeg-and-have-it-work-right/373509#373509](http://askubuntu.com/questions/373322/how-to-replace-avconv-with-the-real-ffmpeg-and-have-it-work-right/373509#373509)
[URL="http://askubuntu.com/questions/313217/install-latest-ffmpeg-for-all-users-in-debina-ubuntu"]http://askubuntu.com/questions/313217/install-latest-ffmpeg-for-all-users-in-debina-ubuntu
[/URL]
Afterwards if you run ffmpeg from the terminal you'll get something like this:
```
$ ffmpeg
ffmpeg version 0.10.9-7:0.10.9-1~precise1 Copyright (c) **2000-2013** the FFmpeg developers
...
```

---

### Post by cybrsaylr on 2013-12-14
> **erind said:**
> .....Afterwards if you run ffmpeg from the terminal you'll get something like this:
```
$ ffmpeg
ffmpeg version 0.10.9-7:0.10.9-1~precise1 Copyright (c) 2000-2013 the FFmpeg developers
```
Interesting erind! That is exactly what I got when showing my terminal output in post #10 above.

code:
> ffmpeg version 0.10.9-7:0.10.9-1~precise1 Copyright (c) 2000-2013 the FFmpeg developers

Question is why doesn't my FFmpeg version run?

---

### Post by erind on 2013-12-15
> **cybrsaylr said:**
> [...]

Question is why doesn't my FFmpeg version run?

I thought you were having problems installing ffmpeg, didn't see completely your previous ffmpeg's output.
While I think you can ignore the deprecated error messages, I don't have an exact answer for the other ones. The recent ffmpeg's source code may have changed, but it's normally backwards compatible. Nonetheless everything is on the table.

For now I'd try the code using avconv, or using an older ffmpeg's version in a VM or old Live CD, so you get an idea of what's going on, or maybe you might get an answer right in this thread. Lastly you can always write to ffmpeg's mailing list at [http://ffmpeg.org/mailman/listinfo](http://ffmpeg.org/mailman/listinfo) .

---

### Post by cybrsaylr on 2013-12-16
Tried to install avconv and both Synaptic Package manager and Ubuntu Software Center say it is installed already as FFmpeg. 
Both call it: libav-tools - Multimedia player, server, encoder and transcoder (transitional package) 7:0.10.9-1~precise1 latest version

When I put the same code in terminal, I just keep getting the same ffmpeg output in terminal I posted above in Post #10!

---

### Post by ajgreeny on 2013-12-16
> **cybrsaylr said:**
> Tried to install avconv and both Synaptic Package manager and Ubuntu Software Center say it is installed already as FFmpeg. 
Both call it: libav-tools - Multimedia player, server, encoder and transcoder (transitional package) 7:0.10.9-1~precise1 latest version

When I put the same code in terminal, I just keep getting the same ffmpeg output in terminal I posted above in Post #10!
You're right, avconv is just a part of the libav-tools package.  The full range of executables in libav-tools is:-
/usr/bin/[COLOR=#ff0000]avconv[/COLOR]
/usr/bin/avplay
/usr/bin/avprobe
/usr/bin/avserver
/usr/bin/[COLOR=#ff0000]ffmpeg[/COLOR]
/usr/bin/ffplay
/usr/bin/ffprobe
/usr/bin/ffserver
/usr/bin/qt-faststart

---

### Post by FakeOutdoorsman on 2013-12-16
> **cybrsaylr said:**
> Well put in that static build code you suggested in post 4 and it doesn't work.
Get the same *** THIS PROGRAM IS DEPRECATED *** message.

I'm stumped......

You simply forgot the **./** before the **ffmpeg** (it's easy to miss). As in:

```
./ffmpeg -i input <options and junk> output.mkv
```

This will execute the binary your downloaded assuming you're in the same directory as the binary. Otherwise the fake, so-called "ffmpeg" will be used as you've shown.

> **ajgreeny said:**
> There is a ppa for ffmpeg which you can enable for the updated version of "proper" ffmpeg.
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)

This is old, unfortunately. For general usage the static build should be used. However, the PPA should work nicely with most repo programs since they will ignore the static build. If ffmpeg is compiled as shown in [How To Compile FFmpeg and x264 on Ubuntu](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide) then it should not interfere with repo stuff unless the package uses the user's PATH to access the ffmpeg binary (such as WinFF and Kdenlive maybe).

> **cybrsaylr said:**
> 
FFmpeg still won't work.
Was the FFmpeg code changed?
Tried using it and get this in terminal and know not what it means:

```
[libx264 @ 0x1000280] width not divisible by 2 (703x548)
Stream #0:0: Video: h264, yuv420p, 703x548, q=-1--1, 1000 kb/s, 90k tbn, 25 tbc
Error while opening encoder for output stream #0:0 - maybe incorrect parameters such as bit_rate, rate, width or height
```


Your output is the MP4 container. By default ffmpeg will use x264 to encode (if that is not available then it will use "mpeg4" which is not as good). x264 is picky with frame sizes: it requires a frame size that is divisible by 2. Your input is 703x548. 703/2 = 351.5 (bad). 548/2=274 (good). You can use the crop, pad, or scale filters to fix this:

crop:
```
ffmpeg -loop 1 -i input.png -i input.mp3 -vf "crop=702:548,format=yuv420p" -codec:v libx264 -crf 23 -preset medium -codec:a copy -shortest output.mp4
```
pad:
```
ffmpeg -loop 1 -i input.png -i input.mp3 -vf "pad=704:548,format=yuv420p" -codec:v libx264 -crf 23 -preset medium -codec:a copy -shortest output.mp4
```
scale:
```
ffmpeg -loop 1 -i input.png -i input.mp3 -vf "scale=704:548,format=yuv420p" -codec:v libx264 -crf 23 -preset medium -codec:a copy -shortest output.mp4
```

Depending on your ffmpeg version and with PNG as input, adding "format=yuv420p" will make sure the output will work with "dumb" players like QuickTime. If this is for YouTube you can omit "format=yuv420p".

-crf and -preset are explained in the x264 link below.

My commands are written for recent ffmpeg. I don't know if they will work with anything from the repo or PPA.

Also see:
[list]
[*][FFmpeg and x264 Encoding Guide](https://trac.ffmpeg.org/wiki/x264EncodingGuide)
[*][FFmpeg and AAC Encoding Guide](https://trac.ffmpeg.org/wiki/AACEncodingGuide)
[/list]

---

### Post by cybrsaylr on 2013-12-17
FakeOutdoorsman thanks, that is a lot for me to digest.

Have to admit I'm weak on command line, only learned some CL on the Ubuntu forums with help from a few members here. 

Will try going through it and yes this is mainly for YouTube.

---

### Post by FakeOutdoorsman on 2013-12-17
> **cybrsaylr said:**
> Have to admit I'm weak on command line, only learned some CL on the Ubuntu forums with help from a few members here. 
You'll get the hang if it.

> **cybrsaylr said:**
> Will try going through it and yes this is mainly for YouTube.

Since YouTube will re-encode anything you give it then the recommended method is to provide the highest quality that is practical for you to upload. So depending on your input you can even try a lossless output:
```
ffmpeg -loop 1 -r 2 -i input.png -i input.mp3 -c:v libx264 -crf 0 -preset veryslow -c:a copy -shortest output.mkv
```

If that's too big try:
```
ffmpeg -loop 1 -r 2 -i input.png -i input.mp3 -c:v libx264 -crf 18 -preset veryslow -c:a copy -shortest output.mkv
```

---

### Post by cybrsaylr on 2013-12-17
FakeOutdoorsman, 

Believe I will go with the **-crf 18** option.

Question is how do you enter that second line of code into FFmpeg and will it then work as it did before?



Oh, just remembered in post #18 you listed 3 lines of code for; crop, pad and scale.
Do they have to be entered in and how?

---

### Post by FakeOutdoorsman on 2013-12-17
I don't quite understand your questions, but if you wanted to crop using the commands from my previous post:

```
ffmpeg -loop 1 -r 2 -i input.png -i input.mp3 -vf "crop=702:548" -c:v libx264 -crf 18 -preset veryslow -c:a copy -shortest output.mkv
```

---

### Post by cybrsaylr on 2013-12-17
Success....kinda...lol
Bear with me, as I said am not that strong in command line.

This is the only code that worked, the code with **-crf 18**:
> Code:
ffmpeg -loop 1 -r 2 -i input.png -i input.mp3 -c:v libx264 -crf 18 -preset veryslow -c:a copy -shortest output.mkv
Code with **-crf 0** failed.

However the song audio cut out at 4:51 not playing to 5:34 and am not sure why. Will admit that 4:51 is the album song length but I found a longer 5:34 length version I liked better and that was the one I wanted to work with and post on YouTube. Here's link: [www.youtube.com/watch?v=mg0qOQ6g2zs](www.youtube.com/watch?v=mg0qOQ6g2zs)

Your 3 codes in post 18 for mp4:
crop:
pad:
scale:

looked like they were going to work, took much longer but failed. They went to the end of song length but the frame section on far left in terminal kept going on forever never stopping. The mp4 that was created would not play and said there were no sound streams on it to play. Haven't got a clue what happened.

---

### Post by FakeOutdoorsman on 2013-12-20
> **cybrsaylr said:**
> Code with **-crf 0** failed.
You should always show your ffmpeg command and the complete ffmpeg console output. Otherwise I can only make guesses.

> **cybrsaylr said:**
> Your 3 codes in post 18 for mp4:
crop:
pad:
scale:

looked like they were going to work, took much longer but failed. They went to the end of song length but the frame section on far left in terminal kept going on forever never stopping. The mp4 that was created would not play and said there were no sound streams on it to play. Haven't got a clue what happened.
That's because I forgot to add "-shortest" to those examples. Also your player (or YouTube?) may not like the low frame rate and/or the pixel format but I have no idea without more info (command, console output, the player used, etc).

---

### Post by cybrsaylr on 2013-12-20
> **FakeOutdoorsman said:**
> You should always show your ffmpeg command and the complete ffmpeg console output. Otherwise I can only make guesses.
OK this is the only code that worked for me:
> Code:
 ffmpeg -loop 1 -r 2 -i input.png -i input.mp3 -c:v libx264 -crf 18 -preset veryslow -c:a copy -shortest output.mkv
This failed:
> Code:
ffmpeg -loop 1 -r 2 -i input.png -i input.mp3 -c:v libx264 -crf 0 -preset veryslow -c:a copy -shortest output.mkv



> **FakeOutdoorsman said:**
> That's because I forgot to add "-shortest" to those examples. Also your player (or YouTube?) may not like the low frame rate and/or the pixel format but I have no idea without more info (command, console output, the player used, etc).
All 3 of these codes failed going into that endless cycle in frame section on far left in terminal kept that kept going on forever never stopping. The mp4 that was created would not play and players reported there were no playable streams on file created, to play with either Movie player, VLC or Audacious player:

> crop:
Code:
ffmpeg -loop 1 -i input.png -i input.mp3 -vf "crop=702:548,format=yuv420p" -codec:v libx264 -crf 23 -preset medium -codec:a copy -shortest output.mp4

pad:
Code:
ffmpeg -loop 1 -i input.png -i input.mp3 -vf "pad=704:548,format=yuv420p" -codec:v libx264 -crf 23 -preset medium -codec:a copy -shortest output.mp4

scale:
Code:
ffmpeg -loop 1 -i input.png -i input.mp3 -vf "scale=704:548,format=yuv420p" -codec:v libx264 -crf 23 -preset medium -codec:a copy -shortest output.mp4

---

