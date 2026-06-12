---
title: "Installing Ubuntu 10.04 on acer Aspire m3400 Desktop, No Hard Drive Found"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by joama on 2010-08-23
Hi,
  We bought a new acer Aspire m3400 Desktop and it comes with windows 7. We wanted to install Ubuntu 10.04 AMD 64 bit on it instead. We put the Live CD in and got it started, by the time it reached the partition section the window was empty, it didn't recognize the hard drive at all. So we had to just hit Quit and that took us to the Live CD session. After searching online for almost 7 hours I found this post here: [http://ubuntuforums.org/showthread.php?t=1310560&highlight=sata](http://ubuntuforums.org/showthread.php?t=1310560&highlight=sata)

Thanks to Ginsu543 suggestion it worked like a charm :D. Below is the same instructions but with replacing Ubuntu 9.10 with Ubuntu 10.04.

1) Run Ubuntu 10.04 using the Live CD
2) Once you are in the live session, open a terminal
3) Remove dmraid by typing "sudo apt-get remove dmraid" at the command line
4) Trying installing 10.04 again by double-clicking on the install icon
5) See if your hdds will show up

Thanks again

---

