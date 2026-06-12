---
title: "Boot Failure cannot locate boot record when trying to install ubuntu from CD"
date: 2013-10-30
forum: Installation &amp; Upgrades
---

### Post by philnlaura on 2013-10-30
[COLOR=#333333][FONT=UbuntuRegular]I've been using Ubuntu at my job now for several years & have felt comfortable enough with it to now begin replacing my PC's at home with it before the EOL for Windows XP.  I'm replacing my older WinXP machine with version 13.04 from a DVD burned from the iso image. I installed 13.04 on another system, that was newer, using a USB drive & I had no problem changing the BIOS to boot from the USB & was able to get the OS up & running with no problem.   When I change the settings on the older PC to boot from the CDROM, I get a DOS message saying "Searching for boot record...Not found" & asked to try again when I try to install the OS. Is there a reason why I can boot from a USB on a newer computer but can't boot using the CDROM from the older one?  The system on the older PC was built on 12/13/01 by American Megatrends & it uses an AMD processor.  Here's an image of the error I get on my attempts:

[/FONT][/COLOR][IMG]http://img.photobucket.com/albums/v633/boonevillephil/1029131748-00.jpg[/IMG]

---

### Post by oldfred on 2013-10-30
System from 2001?
How much RAM and what video chip/card?

 You may need a very lightweight system, 32 bit and may have PAE issues as old systems do not support PAE. Not sure with AMD.

 [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
PAE is provided by Intel Pentium Pro and above CPUs, including all later Pentium-series processors (except most 400 MHz-bus versions of the Pentium M)
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by philnlaura on 2013-10-31
I have looked but am not sure where to find the info about the video card (the system was hand built by a friend who gave it to us) but I know it has 752MB RAM & 995MHz.  The processor is an AMD Duron K7.  It's currently running WinXP Professional.

---

### Post by oldfred on 2013-10-31
That looks like a 32 bit processor, and it may not have PAE.
You should be able to run Lubuntu with that much RAM.

       Lubuntu is an Operating System that is using LXDE.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)
Lubuntu one stop thread - amjjawad
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)


 Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae

---

### Post by mörgæs on 2013-10-31
No, all AMD processors (less than about 15 years of age) support PAE. The 400 MHz Pentium M is the only series with the problem.

I would suggest Lubuntu 13.10. Remember to burn the CD with the slowest speed possible.

---

### Post by warp99 on 2013-10-31
> 13.04 from a DVD burned from the iso image

Do you have a DVD drive? All I see in the image is a CD-ROM drive.

---

### Post by philnlaura on 2013-10-31
I'm pretty sure the system has a DVD drive because I've watched DVDs from it.

---

