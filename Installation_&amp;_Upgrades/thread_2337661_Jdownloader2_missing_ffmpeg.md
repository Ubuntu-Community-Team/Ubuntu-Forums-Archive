---
title: "Jdownloader2 missing ffmpeg"
date: 2016-09-20
forum: Installation &amp; Upgrades
---

### Post by viitinsh-m on 2016-09-20
hello i have a problem with jdownloader. when i try to download from youtube it says skipped - ffmpeg missing, when i try to install it uodate window pops up and says everything is up to date. I have ubuntu 16.04 x64


screenshots are atached

---

### Post by ubontu1 on 2016-11-13
I had the same issue here, same system. It seems Jdownloader2 can't use the downloaded version. So here the solution:

1. install the "real ffmpeg"-package via: sudo apt-get install ffmpeg
2. Open jdownloader2 go to: Advanced-Settings
3. Search for the lines for ffmpeg-binary path and ffprobe-path and set accordingly. 

In my system the path is: /usr/bin/ffmpeg
and
/usr/bin/ffprobe

4. restart Jdownloader2 and et voila: you got it

PS: you can find the binary-path of the tools in the commandline via:
which ffmpeg
which ffprobe

I hope it helps! 
Have fun!

---

