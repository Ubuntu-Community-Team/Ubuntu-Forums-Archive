---
title: "FFMPEG compile failure:  Unknown option &quot;--enable-libfaad&quot;."
date: 2016-06-16
forum: Installation &amp; Upgrades
---

### Post by Robert_Gaines on 2016-06-16
I'm following the instructions on "http://flashvideodownloader.org/ffmpeg/indexen.html" to install FFMPEG. Under "FFMPEG Installation" when I run "./configure --enable-gpl --enable-nonfree --enable-pthreads  --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora  --enable-libx264 --enable-libxvid --enable-x11grab", I get "Unknown option "--enable-libfaad".". On another topic, it says this: "Well, install 'libfaac' first. It seems there was an error doing so. Make sure 'apt-get install libfaac-dev' works.". Okay, I run "sudo apt-get install libfaac-dev" and I get this: "libfaac-dev is already the newest version.". I'm stumped. I'm running Ubuntu 15.10.

---

### Post by FakeOutdoorsman on 2016-06-17
That's an ancient and utterly outdated "guide" that appears to be yet another ripoff of the compile guide that used to be on these forums. It is was moved to the [FFmpeg Wiki](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu).

15.10 contains ffmpeg in the repository, so why are you attempting to compile it?

---

### Post by Robert_Gaines on 2016-06-17
The plug in to Firefox said it needed to be uninstalled then compiled to properly function. It downloads Youtube movies in 4k. I have YouTube Red. Is there a better way to download YouTube videos that are 1080 or above? I am aware that it is downloaded demuxed and played like that for some reason. I have MKV Merge and know how to use it, but I'm not certain how to access those files to mux them into mkv.

---

### Post by Robert_Gaines on 2016-06-17
YouTube video and audio downloader was the plugin that worked,

---

### Post by FakeOutdoorsman on 2016-06-18
libfaad support was removed from FFmpeg in 2010 due to the maturation of the native FFmpeg AAC decoder.

---

