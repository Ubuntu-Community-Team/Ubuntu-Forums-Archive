---
title: "Help Installing DaVinci Resolve on Ubuntu Studio"
date: 2017-09-09
forum: Installation &amp; Upgrades
---

### Post by jsmccloud on 2017-09-09
I'm new to Linux and I'm running Ubuntu Studio in hopes of being able to run all the programs I use to run on Windows.  Right now I'm trying to setup DaVinci Resolve, which has a linux version.  I follow the steps from this link here:
[https://www.thefanclub.co.za/how-to/how-install-blackmagic-design-davinci-resolve-125-ubuntu-1604-lts](https://www.thefanclub.co.za/how-to/how-install-blackmagic-design-davinci-resolve-125-ubuntu-1604-lts)

After completing the steps, the icon shows up on the desktop, but when I double click to open it, nothing happens.

I'm not sure what else to do at this point.  Any help is appreciated.

Thank you!

---

### Post by warmango on 2017-09-09
to clerify, you want to run Windows apps, on Ubuntu, Correct? if so, you can directly run the EXE file using WINE, although not ALL apps will work, because some apps require specific binaries that ONLY COME WITH WINDOWS that wine cannot add to their program

[https://www.winehq.org/](https://www.winehq.org/)

---

### Post by wildmanne39 on 2017-09-09
You need to list the programs you want to run and someone can tell you if there is a linux alternative or if it will run it wine, in general windows programs do not run on linux.

---

### Post by jsmccloud on 2017-09-09
To clarify I am wanting to install and run the Linux version of the software, which you can download here: 
[https://www.blackmagicdesign.com/products/davinciresolve/#](https://www.blackmagicdesign.com/products/davinciresolve/#)

If is downloaded as a zip file.  I extract it and install it via the .sh file following the instructions from the previous link I mentioned.

It has appeared to install, however, when I double click the Davinci Resolve icon from the desktop, nothing happens.

Thanks.

---

### Post by gordintoronto on 2017-09-10
The installation instructions are quite complicated.

Coming from Windows, the most likely problem is that somewhere, you typed a letter in the wrong case.

In Linux, Downloads and downloads are completely different places.

---

### Post by heikki-repo on 2017-09-12
Follow these instructions:
[https://forum.blackmagicdesign.com/viewtopic.php?f=21&t=56878&start=500#p361701](https://forum.blackmagicdesign.com/viewtopic.php?f=21&t=56878&start=500#p361701)

Please note, that at the moment there is no audio support in Resolve Linux version, except through BMD hardware (for example, Decklink Mini monitor). Hopefully that'll change soon or someone from the open source community finds a way to bridge ALSA / PulseAudio and Resolve.

---

