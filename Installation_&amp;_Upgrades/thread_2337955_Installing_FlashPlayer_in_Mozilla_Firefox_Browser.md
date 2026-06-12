---
title: "Installing FlashPlayer in Mozilla Firefox Browser"
date: 2016-09-23
forum: Installation &amp; Upgrades
---

### Post by prashant.usict on 2016-09-23
Hello guys,
I am new to Ubuntu so please help me by solving one problem.
I was installing flash downloader in mozilla brower and when I followed their instruction of running this command

sudo apt-get install build-essential subversion git-core checkinstall yasm texi2html libfaac-dev libfaad-dev libmp3lame-dev libsdl1.2-dev libtheora-dev libx11-dev libxvidcore4-dev zlib1g-dev

I am getting error of
 E: Unable to locate package libxvidcore4-dev
Please help! 
Thanks.
[ATTACH=CONFIG]271318[/ATTACH]

---

### Post by howefield on 2016-09-23
Hello and welcome to the forums.

It is better to copy and paste the output from the terminal between code tags to help others better help you.

The error is telling you what the problem is, there is no package called libxvidcore4-dev, try using libxvidcore-dev instead.

PS. What is flash downloader ?

---

