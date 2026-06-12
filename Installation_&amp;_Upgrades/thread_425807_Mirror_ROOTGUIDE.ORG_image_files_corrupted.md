---
title: "Mirror ROOTGUIDE.ORG image files corrupted"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by totosplatz on 2007-04-27
Two image files on the miror <mirror.rootguide.org> are corrupted.

I had repeatable, duplicatable downloads with problems with incorrect md5sums as shown in this post:

<http://ubuntuforums.org/showthread.php?t=420058>

I can now confirm that the ISO images on [www.rootguide.com](www.rootguide.com), specifically:

<http://mirror.rootguide.org/ubuntu-releases/feisty/ubuntu-7.04-desktop-i386.iso>

... and ...

<http://mirror.rootguide.org/ubuntu-releases/feisty/ubuntu-7.04-desktop-amd64.iso>

... are corrupt.

It is possible, but not likely, that the files are OK but something about the way they are being served up is corrupt. However, these erroneous downloads were EXACTLY duplicated and frankly, they take too long to download for me to experiment further.

I downloaded these images from the mirror in Portland at Portland State University and got correct md5sum values. I did not download directly to China; I downloaded to my machine in Portland, and then used scp to get that file to China.

I used Firefox v1.5.0.6 on Linux 2.6.11 to do the downloads.

Linux yangtze.china-post.cn 2.6.17.11 #1 SMP PREEMPT Thu Sep 7 18:05:42 HKT 2006 x86_64 AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ unknown GNU/Linux

Thanks.

Jim Howe
Zhuhai, China and Portland, Oregon



..............

---

