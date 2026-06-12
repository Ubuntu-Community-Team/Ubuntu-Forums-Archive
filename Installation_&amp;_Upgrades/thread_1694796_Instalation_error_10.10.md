---
title: "Instalation error 10.10"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by peepsann on 2011-02-24
[B]I installed 10.10 and when I rebooted to complete the install I got this error message
"No root file system is defined"
"Please correct this from the partitioning menu"

I am a user of Ubuntu and like it very much, but I have never had a problem such as this one. Partition issues are a little over my head right now and not my forte. Has anyone had the same problem and if so were you able to get passed it. I need to mention that no matter how I install,  whether Wubi or direct from the CD...I have no luck with the installation on this machine which runs Windows7. If I install from wubi I get the error mentioned above..If I install from the CD, I get no Ubuntu boot option[/B]s. **I have tried different CDs and versions of Ubuntu to include xbuntu...and for the first time my Ubuntu installation has failed....I have installed Ubuntu on at least 7 machines with no or few problems until now. Can anyone please help as I am putting this computer together for my grand daughter..it will be her first one and I want her to have the Ubuntu/Linux experience early in her life.** **Thank you in advance.**

***Note: I am fairly computer literate at least with windows....but this one has me stumped!***. ***I have tried to install Ubuntu as a dual boot to a second hard drive and I also tried to install in on the same one as windows7 with no luck so far!***

---

### Post by bcbc on 2011-02-24
Can you boot from an Ubuntu cd and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")?

Just a wild stab... but some computers come with software raid metadata (even if the raid has not been setup) and this can confuse Ubuntu. The bootinfoscript should provide more information.

Edit: this can also occur on computers with a mix of gpt and mbr partition tables. There is a long-standing bug (that is getting no attention) about this: [https://bugs.launchpad.net/bugs/259540](https://bugs.launchpad.net/bugs/259540)

---

