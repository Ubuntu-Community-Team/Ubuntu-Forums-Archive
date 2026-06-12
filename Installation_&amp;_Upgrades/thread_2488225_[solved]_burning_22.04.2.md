---
title: "[solved] burning 22.04.2"
date: 2023-06-27
forum: Installation &amp; Upgrades
---

### Post by mikealte2468 on 2023-06-27
I've been away from Ubuntu for a while and I'm trying get back to it.

I downloaded 22.04.2, verified the check sum and went burn only to find the the downloaded image is larger than a blank DVD.

How do I get around this?

Mike

---

### Post by tea for one on 2023-06-27
The usual way to install Ubuntu is via a USB stick.
[https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview)
There are links in the tutorial for both Windows and Mac users.

---

### Post by Rubi1200 on 2023-06-27
An 8GB USB stick is more than enough for most recent ISO images.

I use Rufus and have never had an issue.

---

### Post by aljames2 on 2023-06-27
Welcome back mikealte2468

There are also command line ways to prepare your USB. Just ask if you are interested.

I use a computer case that has a HP DVD r/w drive in it.  The DVD hasn't been connected for a long time.  I started to pull it out today
then  realized why I had left it there...I couldn't find the old faceplate to  put its place.  Oh well, at least it looks like its there for a purpose :)

---

### Post by MAFoElffen on 2023-06-28
Hmmm. You only mentioned CD, not DVD. Does the computer boot via USB? Or remember the Plop CD? 

If it doesn't boot directly from USB, you can boot from a Plop CD, then use that to boot a USB with the Live Installer.

What OS did you download the ISO to?

---

### Post by guiverc on 2023-06-29
You didn't specify what Ubuntu 22.04 LTS product, but  Ubuntu 22.04 LTS was the last release that was *intended* to be used for installing systems from *optical* media (DVD etc), later releases assume FLASH/USB media.

Changes started with *groovy *(20.10) that caused problems, especially on older equipment (*scan of media that is very slow on optical media, the timeouts that can occur being misinterpreted by some programs as other problems*) though it's still possible on newer/faster equipment.

Ubuntu Desktop now requires a *dual layer* DVD with larger capacity, 4.7GB per layerso single layer has only ~4.7GB but dual 8.5GB* (double less overhead*).

Some *flavors* easily fit on DVD; eg. all Lubuntu's will fit on a *single-layer* DVD as the largest ISO currently is *mantic* which is ~3GB in size; it's not alone in fitting though on single layer, but any ISOs that include (*optional*) 3rd party video drivers on the media (*instead of downloading them from the internet, ie. better for offline installs*) are noticeably larger.

DVD media can still be used for 22.04, 22.10 though... *though it may take more than a single install if using older equipment due to snap daemon & other potential consequences if the media check is slowed by older hardware.. for some like Ubuntu Server this can be more of a problem than others, but I was able to use hardware as old as from 2005 with multiple goes**, but it was faster/easier on newer hardware.*

I'd recommend just using *flash* media (USB thumb-drive etc) as others have already recommended.

---

### Post by mikealte2468 on 2023-07-03
Thanks Rubi1200 - Rufus-4.1.exe worked without a hitch, put it on a 64GB usb2 thumb drive. It took over 20 minutes to 'burn'. It boots very fast.

I'm not sure this is the right place to note this; There should be a note on the releases page [http://releases.ubuntu.com/](http://releases.ubuntu.com/) to use a 8 GB or larger drive or a dual layer DVD.

I tried balenaEtcher-Portable-1.18.8 but it cause frequent 'hiccups' from my firewall (Comodo free on win 10 pro).

---

