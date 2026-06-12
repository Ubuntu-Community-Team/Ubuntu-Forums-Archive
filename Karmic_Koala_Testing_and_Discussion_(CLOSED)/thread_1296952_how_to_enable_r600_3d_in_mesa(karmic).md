---
title: "how to enable r600 3d in mesa(karmic)?"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Gutsycat on 2009-10-21
I found that with karmic 3d for r600 will be disabled:

> mesa (7.6.0~git20090817.7c422387-0ubuntu5) karmic; urgency=low

  * debian/rules: Disable r600: Disable r600 as 3D support is still
    experimental and causes problems with the gnome session when
    compiz is enabled (LP: #419126).


Could anybody help me enable it in diff patch and help with some commands to recompile deb source.

---

### Post by Woody1987 on 2009-10-21
This is how i got my radeon 4550 (r700) working with 3d, thus compiz on karmic.

First you have to install a 2.6.32 series kernel, this is easy to do, go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc5/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") and download and install the kernel for your architecture, please note that the latest 2.6.32 kernel is rc5 and therefore isnt the most stable of kernels.

Next updated driver: add this ppa [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) and update then upgrade. Upon reboot you should have opensource 3d working for your card.

On my particular card there were a few screen corruption issues. Nothing major, but for example i couldnt write anything in gnome-terminal, everything i wrote would show up as garbled, the commands still worked, i just couldnt read what i was typing. Since you have a different card this might not affect you, although you may have entirely different problems.

---

### Post by OpenGuard on 2009-10-21
> **Woody1987 said:**
> This is how i got my radeon 4550 (r700) working with 3d, thus compiz on karmic.

First you have to install a 2.6.32 series kernel, this is easy to do, go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc5/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") and download and install the kernel for your architecture, please note that the latest 2.6.32 kernel is rc5 and therefore isnt the most stable of kernels.

Next updated driver: add this ppa [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") and update then upgrade. Upon reboot you should have opensource 3d working for your card.

On my particular card there were a few screen corruption issues. Nothing major, but for example i couldnt write anything in gnome-terminal, everything i wrote would show up as garbled, the commands still worked, i just couldnt read what i was typing. Since you have a different card this might not affect you, although you may have entirely different problems.

If it's not of the most stable ones, why not just to install 2.6.31 ?

---

### Post by Woody1987 on 2009-10-21
because the 2.6.31 and below kernels dont have the drm code for the r600 and r700 series cards.

---

### Post by screaminj3sus on 2009-10-21
I have an r630 (mobility hd2600) and am using 2.6.32 kernel with the xorg-edgers ppa. So far it is working better than fglrx ever has, compiz is way smoother, and if I play videos full screen with undredirect fullscreen windows checked in compizconfig I can actually watch videos without tearing while compiz is enabled for once.

I have had no stability issues at all so far, its been more stable than fglrx.

---

### Post by Gutsycat on 2009-10-22
> **Woody1987 said:**
>  Next updated driver: add this ppa [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") and update then upgrade. Upon reboot you should have opensource 3d working for your card.
Do I need mesa 7.7 git from here [https://launchpad.net/~sarvatt/+archive/xorg-testing](https://launchpad.net/~sarvatt/+archive/xorg-testing) ?

---

### Post by Woody1987 on 2009-10-22
> Do I need mesa 7.7 git from here [https://launchpad.net/~sarvatt/+archive/xorg-testing](https://launchpad.net/~sarvatt/+archive/xorg-testing) ?

Yes

---

### Post by uBeer on 2009-10-22
Cool, compiz works quite well (for about an hour that I tested it this afternoon). Alas that the 2.6.32 kernel gave some problems while recording a jam of my band...

And another problem is that both my wireless and ethernet don't work with 2.6.32.
But it's really nice to see that almost after a year that I bought my laptop it can draw glxgears with open source software! That's what I've been waiting for! Not that I use 3D applications all that much, but it is sure fun to see it starting to work :D

---

### Post by Longinus00 on 2009-10-22
> **Woody1987 said:**
> because the 2.6.31 and below kernels dont have the drm code for the r600 and r700 series cards.

Did fedora add then in manually because I was testing 3d in fc12 beta and it used kernel 2.6.31. All that was required was installing an experimental version of mesa.

---

