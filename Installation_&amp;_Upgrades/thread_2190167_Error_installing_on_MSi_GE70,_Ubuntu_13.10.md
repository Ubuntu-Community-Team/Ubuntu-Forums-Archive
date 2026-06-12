---
title: "Error installing on MSi GE70, Ubuntu 13.10"
date: 2013-11-26
forum: Installation &amp; Upgrades
---

### Post by Hansje on 2013-11-26
Hi,

I just got my new laptop for work. I need a linux distro to do my job (I need couchdb, it's really buggy on windows). On my previous laptop i was running debian, but i want to try ubuntu once again.
I downloaded the 64bit image of ubuntu and tried to boot from it with a dvd, no luck, I get an error saying: 'you should load the kernel first' (I guess this has something to do with UEFI?).
I tried making a live USB stick to boot from, this seems to work a little better, idd, a little.
I tried booting from the USB stick with both UEFI and Legacy mode (and UEFI with CSM), In all 3 cases I tried booting without installing or installing directly. All come to the same error before I can do anything else, so I don't think this has something to do with UEFI.

I want to install Ubuntu as a dualboot with windows 8.1 (for some tasks i need windows...), turning to Legacy mode seems to break my windows install (if it is possible i want to avoid a re-install), so I want Ubuntu to boot with UEFI.

The error contains to many text to retype, so I took a picture of it. The strange thing for me is that some words are in French. As far as I can read this error it has something to do with the graphics, but I can't find any information...
[http://artexanis.be/ubuntuInstallError.jpg]("http://artexanis.be/ubuntuInstallError.jpg")
Help is greatly appreciated!

---

### Post by Hansje on 2013-11-26
I was searching for the wrong keywords, I figured it out, 'nomodeset' did the trick.
Thanks anyway :-)

---

