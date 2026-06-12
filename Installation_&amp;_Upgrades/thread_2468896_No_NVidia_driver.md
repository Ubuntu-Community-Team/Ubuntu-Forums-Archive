---
title: "No NVidia driver"
date: 2021-11-13
forum: Installation &amp; Upgrades
---

### Post by peyre on 2021-11-13
I've had to reinstall Xubuntu from scratch since something went wrong with my old installation on this desktop, and want to install the proprietary driver, since nouveau kept locking the system up or logging me off without warning.  lspci returns this for the card (it's an old one!):

VGA compatible controller: NVIDIA Corporation G94 [GeForce 9600 GT] (rev a1)

I had tried getting it through Additional Drivers, but it says there aren't any available.  What a tease.

[ATTACH=CONFIG]289464[/ATTACH]

I downloaded a driver from NVidia which supports this card (NVIDIA-Linux-x86_64-340.76.run), but when I drop out of X Window, it fails to install.  It tells me:
> An alternate method of installing the NVIDIA driver was detected. (This is usually a package provided by your distributor.) A driver installed via that method may integrate better with your system than a driver installed by nvidia-installer.

The NVIDIA driver provided by Ubuntu can be installed by launching the "Software & Updates" application, and by selecting the NVIDIA driver from the "Additional Drivers" tab.

Of course, that's the very window I tried to use in the first place.  So how can I get this card's drivers installed?

---

### Post by The Cog on 2021-11-13
What version of Ubuntu is it? (**lsb_release -a** will tell you).
Does **sudo apt update** work?

---

### Post by peyre on 2021-11-13
It's 21.10.

---

### Post by peyre on 2021-11-13
Odd, now following a reboot I can't seem to get the video to go out through the card.  I'm currently using the onboard video, so down to one monitor.  Boo.  I shut down and reseated the card, but it's still not outputting.  The card does still show in lspci.

Should I maybe reinstall from scratch again?  Maybe something went wrong during install?

---

### Post by mikewhatever on 2021-11-13
21.10 is too new for GeForce 9600 GT from 2008. You have to use 20.04 with the original 5.4 kernel.

---

### Post by peyre on 2021-11-13
Really!  That would explain it.  So wipe and install 20.04 from scratch then?  Or maybe get by on nouveau until the driver's ready?

Strange though.  I thought maybe something had gone wrong with the video card, so I swapped it out with a real old one I had in the garage.  (lspci shows it as VGA compatible controller: NVIDIA Corporation G72 [GeForce 7200 GS / 7300 SE] (rev a1).)  This old Dell's still insisting on outputting to onboard video.

---

### Post by peyre on 2021-11-13
Ok, I reinstalled with 20.04, and sure enough there's the driver.  Thanks Mike.

---

### Post by mikewhatever on 2021-11-13
Welcome, and thanks for the feedback. 
Those Geforce 9000 GPUs are supported by the legacy nvidia-390 driver. Nvidia dropped support at the end of 2019, and so 20.04 with the original kernel 5.4 is the last release that has the driver. It does not work with newer kernels, like, for example 5.11.

---

### Post by peyre on 2021-11-13
Oh, man!  It's been a real workhorse, this card.  So are you saying in a year I may have to replace it?

---

### Post by mikewhatever on 2021-11-14
Well..., it depends. While Xubuntu 20.04 is supported until 04.2023, the base system gets 5 years, and after that, there is also extended support. So, you don't have to replace it for a quite some time.

---

### Post by peyre on 2021-11-14
Oh, thanks.  Well I'm mostly back up and running, although...if I install the NVidia driver, on reboot the system refuses to output video through the card.  Weird.  So I'm still on nouveau, and it occasionally logs me off summarily.

---

