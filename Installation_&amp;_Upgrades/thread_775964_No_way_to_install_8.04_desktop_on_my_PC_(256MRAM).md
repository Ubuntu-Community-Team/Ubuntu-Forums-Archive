---
title: "No way to install 8.04 desktop on my PC (256MRAM)"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by mathieubill on 2008-04-30
Hi there,


I wanted to install the latest 8.04 version of Ubuntu Desktop on a PC with 256 M RAM and a Celeron 900 Mhz.
This is not the first time that I try to install Ubuntu. I installed many times the desktop and server versions (from 5.0 to 7.10).
I am also used to install debian.

I first downloaded and burned the live CD.
I tried the live install and also the normal install but nothing worked.
The computer freezes when I select an install.
I was not surprised that the live install did not work because I read somewhere that RAM is needed.
But I was more surprised that the normal install did not work either.
Furthermore, there was no error message at all!


I then downloaded and burned the text-based install CD.
I launched the normal install.
I could go further into the install process but it cannot succeed because it says for many packages:
Warning file:///cdrom/ ..... .deb was corrupt

I then though that the disk images I download had problems.
I checked them with md5sum and everything was OK.

I then tried to configure the package manager system in order to fetch the corrupt packages from the network but it did not work either.


I then though that I could install a debian system and then Ubuntu from it.
I read that it is not that simple with Hardy.

At least, I managed to install the debian etch version with the netinst CD.

But I did not manage to install ubuntu 8.04 as I wanted first.
I am very disappointed because I like very much Ubuntu and this experience does not correspond to what is advertised everywhere about ubuntu ie it is very simple to install.

So here are my questions:

- do you know why I have the corrupt warnings and do you know how I could get rid of them?

- is there a netinst for ubuntu 8.04 or a way to tell the installer to go to fetch the packages on the net instead of the CD?

- is there a simple way to install ubuntu 8.04 over a debian etch?

Thank you for your help.

---

### Post by dstew on 2008-04-30
The corrupt warnings might indicate a bad CD. Even if the md5 sum of the .iso or the CD is normal, check the CD integrity with the menu item. If you have a Linux or Windows system already working on that computer, you can use the [unetbootin]("http://unetbootin.sourceforge.net/") utility to install 8.04 over the internet. You can use unetbootin from Debian etch, I believe.

---

