---
title: "For those who want to try installing ffmpeg on 16.04 without PPA or compiling. . ."
date: 2016-06-16
forum: Installation &amp; Upgrades
---

### Post by roler2 on 2016-06-16
. . .this may work. . .or may not. . .it installed fine for me. . .I just haven't tested ffmpeg. . .

I went to this Web Site:

[https://launchpad.net/ubuntu/+source/ffmpeg/7:3.0.2-1ubuntu1/+build/9719259](https://launchpad.net/ubuntu/+source/ffmpeg/7:3.0.2-1ubuntu1/+build/9719259)


Down near the end of the page on the left you will see the .deb files for all the dependencies/extras. I did not download the -dev files nor the debug files, only the 'regular' deb files.

I had to install one by one because they had to be installed in a particular order, as all of the files appeared to be dependent on one another.

QUESTION: Is there a way to automate this installation if all of the files are in one Folder?

The only file I could not install was libavcodec-extra57. It is dependent on libavcodec57. When I tried to install the -extra57, I got an error message stating that libavcodec57 could not be removed.

QUESTION: Is it safe to force install libavcodec-extra57 or should I leave well enough alone? What is the difference between the two files?

---

