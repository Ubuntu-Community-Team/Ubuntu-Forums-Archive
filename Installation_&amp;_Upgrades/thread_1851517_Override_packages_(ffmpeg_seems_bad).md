---
title: "Override packages (ffmpeg seems bad)"
date: 2011-09-28
forum: Installation &amp; Upgrades
---

### Post by plant pot on 2011-09-28
Put simply, Is there a standard/correct place to install tar.gz's so they don't interfere with ubuntus idea of what is installed?

What I *Really* want to know is: How/where does one install stuff when I want to override a broken or missing package?


ffmpeg is composed of a whole army of packages with names such as  'libavutil' and 'swscale'. The developer packages for ffmpeg seem to be inconsistent. They seem to have installed a bunch of header files that refer to other header files that do not exist; even within a single component package (libavutil headers refer to other libavutil headers that do not exist). I want to compile my own stuff against the ffmpeg libraries but am finding it impossible.

ffmpeg is also changing its API's fast, so I  cannot fault ubuntu 11.04 for having an inconsistent set of header files that I find impossible to use. 


I just want to know where I should build and install a fresh snapshot of ffmpeg so its header files and libraries take presidence-over / replace-those ubuntu splashed on.

---

### Post by azmyth on 2011-09-28
There's a great how to on these forums that explains how to compile ffmpeg. It'll give you a package that you can use to overide the ffmpeg installed by ubuntu. Just search on google ubuntu compile ffmpeg.

---

### Post by andrew.46 on 2011-09-28
Or go straight here:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by plant pot on 2011-09-29
I will give that a go just as soon as I fix the bootloader that I broke last night!

I am not sure it answers my question directly, but it does give me a good direction to attack. If I read it correctly, it won't override my existing ubuntu ffmpeg since  current ffmpeg (last week anyway!) installs to /usr/local/ by default. I think that this is later in the header and library include path than the ubuntu install. In which case the ubuntu version will be used, and the new version is the one that will be ignored.

I think I will therefore need to first uninstall all of the ubuntu ffmpeg parts. That will be a pain as ubuntu will then try to reinstall a bad ffmpeg (overriding mine) if I ever need a package that depends on ffmpeg in the future. I may need to remain ever-vigilant.


Am I correct in assuming that ubuntu people conventionally use "--prefix=/usr" in their configure scripts when compiling non-ubuntu libraries?

---

### Post by andrew.46 on 2011-09-29
> **plant pot said:**
> Am I correct in assuming that ubuntu people conventionally use "--prefix=/usr" in their configure scripts when compiling non-ubuntu libraries?

Actually you might find:

```
--prefix-/usr/local

```

a little more commonly, which is for the most part the *default* anyway.

---

