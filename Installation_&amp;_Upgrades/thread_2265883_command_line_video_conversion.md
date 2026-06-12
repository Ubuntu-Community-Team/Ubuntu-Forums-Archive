---
title: "command line video conversion"
date: 2015-02-18
forum: Installation &amp; Upgrades
---

### Post by remmas-sido on 2015-02-18
Hi
I'd like to learn how to convert videos using terminal, is there like a step by step guide? or basics I should know about? or any tips or tricks?
Thank you

---

### Post by TheFu on 2015-02-18
There are 50 ways to do it.
What is the input and what is the output you want, exactly. Be as technical as possible - audio and video codecs, subtitles, languages, etc. ... 

Or you can just google for ffmpeg, avcon, mencoder and handbrakecli for the tools and options used for simple transcoding.

---

### Post by SeijiSensei on 2015-02-18
The [Ubuntu help page for **ffmpeg**]("https://help.ubuntu.com/community/FFmpeg") calls it "the premier video decoding and encoding system on Linux (and in computing in general)."  Nowadays Ubuntu ships a "fork" of ffmpeg called "avconv".  You can use the ffmpeg documentation replacing "ffmpeg" in the examples with "avconv." The basic conversion command
```
ffmpeg -i [input] [video options] [audio options] [output]
```
then becomes
```
avconv -i [input] [video options] [audio options] [output]
```

If you're like me and prefer to use ffmpeg itself you can install it from a PPA repository using the commands
```
sudo add-apt-repository ppa:jon-severinsson/ffmpeg
sudo apt-get update
sudo apt-get install ffmpeg
```

For a start, try converting a file from one "container" format, say MKV, to another like MP4. 
```
ffmpeg -i /path/to/input.mkv -codec copy /path/to/output.mp4
```
This command uses the "-codec" parameter to copy the video and audio streams from one file to the other without any re-encodings.  That works fine if the source has a single audio stream and no subtitles.  If not, you'll need to add additional parameters to the command to select the streams you want to preserve.

From here on, use Google to figure out which parameters you'll need for whatever conversions you want to perform.  I doubt there is anything you'll need to do that you can't accomplish with ffmpeg. (The command "ffmpeg -formats" will show you the full array of codecs and containers ffmpeg knows about.) The [Ubuntu wiki article]("https://help.ubuntu.com/community/FFmpeg") has a good array of examples.

Oh, and if you get tired of seeing the "banner" with the build options and such, use these commands to add the "-hide_banner" option by default:
```

cd
echo "alias ffmpeg='ffmpeg -hide_banner'" >> $HOME/.bash_aliases
source .bashrc

```

---

### Post by FakeOutdoorsman on 2015-02-19
See the [FFmpeg Wiki](https://trac.ffmpeg.org/wiki#CommunityContributedDocumentation) for a bunch of articles. I think it's the best place to start for beginners. It is meant to supplement the [documentation](http://ffmpeg.org/documentation.html). Note that it is written for ffmpeg from FFmpeg and not the avconv nonsense. You can simply [get a recent ffmpeg build](http://johnvansickle.com/ffmpeg/) (just download, extract, execute) or [compile](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu), or use [mc3man's PPA](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media). Or wait until 15.04 (if I recall correctly) for the real ffmpeg binary to return to Ubuntu.

Official help channels are the [ffmpeg-user mailing list](http://ffmpeg.org/contact.html) and #ffmpeg IRC channel, but there are many other places that provide sane answers.

---

