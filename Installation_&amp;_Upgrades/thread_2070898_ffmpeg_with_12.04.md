---
title: "ffmpeg with 12.04?"
date: 2012-10-14
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2012-10-14
Installed ffmpeg in 64 bit 12.04 and got this message in terminal:
> *** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.

What is best to do? I've only used ffmpeg in the past and am familiar with it.

Is avconv as easy to use as ffmpeg?
Should I remove ffmpeg and go with avconv?
Do you use similar code as ffmpeg, or is avconv code completely different?

---

### Post by FakeOutdoorsman on 2012-10-14
> **cybrsaylr said:**
> Installed ffmpeg in 64 bit 12.04 and got this message in terminal:
```

 *** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead. 

```
This is a confusing statement since it does not make a distinction between ffmpeg (the program: offered by both FFmpeg and libav for a some time) and FFmpeg (the project), and therefore many users imply that the statement means the FFmpeg (the project) is going away. FFmpeg is very active. For a better summary see: [Who can tell me the difference and relation between ffmpeg, libav, and avconv](http://stackoverflow.com/a/9477756/1109017).

> **cybrsaylr said:**
> What is best to do? I've only used ffmpeg in the past and am familiar with it.
The good thing is that you have a choice. I didn't want the whims of a package maintainer to choose for me, and prefer FFmpeg, so I compile it myself: [Compile FFmpeg on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide). [Static FFmpeg builds](http://ffmpeg.gusari.org/static/) are also available if you don't want to compile or deal with the package management system.

> **cybrsaylr said:**
> Do you use similar code as ffmpeg, or is avconv code completely different?
For the general user the syntax should be similar between ffmpeg (from FFmpeg) and avconv. I'm referring to current upstream. It isn't guaranteed to stay that way however.

---

### Post by cybrsaylr on 2012-10-14
Thanks FakeOutdoorsman, you and Ron helped me out with this a couple years ago in this thread. 
[http://ubuntuforums.org/showthread.php?t=1650995&highlight=converting+mp3+video+mp4+youtube]("http://ubuntuforums.org/showthread.php?t=1650995&highlight=converting+mp3+video+mp4+youtube")

You both basically helped me use command line with ffmpeg.

Glad to hear ffmpeg will be around because that message terminal gave out was a bit confusing.

Since I installed ffmpeg in 12.04 should I remove it and replace it with the latest version for 12.04?
Then I believe the libraries have to be added to make it work properly.

Do you happen to have the proper code needed to do this?

---

### Post by FakeOutdoorsman on 2012-10-15
> **cybrsaylr said:**
> Thanks FakeOutdoorsman, you and Ron helped me out with this a couple years ago in this thread. 
[http://ubuntuforums.org/showthread.php?t=1650995&highlight=converting+mp3+video+mp4+youtube]("http://ubuntuforums.org/showthread.php?t=1650995&highlight=converting+mp3+video+mp4+youtube")

I remember that thread now. Those pesky spaces as the first character will confuse just about anyone.

> **cybrsaylr said:**
> Since I installed ffmpeg in 12.04 should I remove it and replace it with the latest version for 12.04?
Are you trying to decide between using "ffmpeg"/avconv from the repository or using ffmpeg from FFmpeg? Only you can decide that. There are pros and cons to both the repository "ffmpeg"/avconv and using real ffmpeg:

Repository "ffmpeg"/avconv pros:
[list]
[*] It is easy to install
[*] It will work with other repository programs that depend on ffmpeg
[/list]

Cons:
[list]
[*] It's not FFmpeg (I'm biased)
[*] It is old (in terms of FFmpeg development)
[*] I do not use avconv so I don't provide help for it (if that's worth anything)
[*] It seems buggier than real ffmpeg
[/list]

FFmpeg pros (assuming you're compiling):
[list]
[*] Compiling lets you decide everything: what to support, etc
[*] Will always be newer than what the repo supplies and therefore will have more bugfixes and features
[*] Geek points for compiling
[/list]

Cons:
[list]
[*] Potential syntax changes
[*] Takes time to compile
[*] Will not always work with packages that depend on "ffmpeg"/avconv
[/list]

If you plan on using ffmpeg often then try compiling it. If you are simply encoding on rare occasions you may want to use whatever the repository offers for convenience.

That being said you can still use both at the same time. You can use the repo version to keep other packages happy, and then use the static build when you want to use ffmpeg directly.

---

### Post by cybrsaylr on 2012-10-15
> **FakeOutdoorsman said:**
>  If you are simply encoding on rare occasions you may want to use whatever the repository offers for convenience.

I just used ffmpeg occasionally to upload clips to Youtube so the Repository "ffmpeg" version should suffice.

To avoid those pesky spaces errors, I saved the required codes needed so all that was needed we to replace the new image and mp3 titles. Then I would simply 'copy & paste' the new adjusted code into terminal and it worked like a charm....lol

This would avoid having to manually type everything into terminal and have it fail due to a 1 space error or typing error....lol

---

