---
title: "automatic installation with kickstart and syslinux.cfg   10.10"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by AdmiralNotorious on 2011-01-17
Hello.

I am so close to the answer i think. My goal is to fully automate an entire Ubuntu installation off a usb flashdrive from start to finish. So, i did as this   

[https://help.ubuntu.com/8.04/installation-guide/i386/automatic-install.html](https://help.ubuntu.com/8.04/installation-guide/i386/automatic-install.html)    

guide said and i made a kickstart ks.cfg file that is used to automate an installation, as i'm sure many of u know.

The next step has infinitely confused me. To make the ks.cfg file boot automatically and startup an installation to my specifications.

from this link 
[http://old-releases.ubuntu.com/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/apcs01.html](http://old-releases.ubuntu.com/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/apcs01.html)

I have found that editing the syslinux.cfg file in the syslinux directory on the usb can be used to load preseed file, which to my understanding serves the same purpose as a kickstart file.

How should i edit syslinux.cfg to achieve my ends? or am i totally off base here?

---

