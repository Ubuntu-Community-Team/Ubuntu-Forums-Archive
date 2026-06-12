---
title: "How can I install the Creative Webcam PD1001 in 11.04"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by ChristosHDJ on 2011-06-09
Hi everyone,
   I was going through some old stuff I had in a drawer of mine and I found this old webcam (Creative Webcam PD1001) and I thought that it 'd be nice to use it. Unfortunatelly, I just can't get it to work. After some google-ling I found these set of instructions:

1. Download the source files that are included in epcam-src-ubuntu-0.7.1.tar.gz
2. Open a terminal
3. Go the directory where you download epcam-src-ubuntu-0.7.1.tar.gz
4. Copy-Paste in your terminal each of the following lines exactly as it is :
    
   tar xfvz epcam-src-ubuntu-0.7.1.tar.gz
   sudo apt-get install linux-headers-`uname -r` linux- restricted-modules-`uname -r`
   sudo make
   sudo make install
   sudo make clean

So I thought "Great problem solved". Unfortunately, when I tried to run the "sudo apt-get install linux-headers-`uname -r` linux- restricted-modules-`uname -r" command the following konsole msg appeared:

E: Unable to locate package linux-restricted-modules-2.6.38-10-generic
E: Couldn't find any package by regex 'linux-restricted-modules-2.6.38-10-generic'

After google-ling a bit more I realised that for my kernel version - 2.6.38-10-generic - this package is not out yet. So I thought that maybe I can find an older version of the package, for another version of kernel that may be compatible with mine. But that's as far as I went. I can't find anything and even if I do, how will I know that the package version will be compatible with my kernel version?

Any other suggestions will be really helpful.

Cheers,

Christos

---

### Post by fixitdude on 2011-06-13
one of the files is here:
[http://ubuntuforums.org/showpost.php?p=2626919&postcount=29](http://ubuntuforums.org/showpost.php?p=2626919&postcount=29)

The project's sourceforge.net
[http://sourceforge.net/projects/epcam/](http://sourceforge.net/projects/epcam/)

I don't know if it works on newer versions.

(Last Update shows 2011-03-12)

---

