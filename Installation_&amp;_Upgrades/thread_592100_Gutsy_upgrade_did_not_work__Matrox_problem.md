---
title: "Gutsy upgrade did not work / Matrox problem?"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by az68 on 2007-10-26
Trying to upgrade my working 7.06 system to Gutsy did result in a freeze of the system in one place. After failing to do CD upgrades, I finally decided to make a clean install.

So far, so good. System was running, more or less.

I then tried to install the latest Matrox driver for a Millenium P650. This was no good idea. The first thing is, that X has a serious problem, even with the standard VESA driver. I just get a 800x600 resolution. Before the install I had my 1280x1024.

The other thing is, that I can not choose a right Matrox driver from the list. It just lists the old mga drivers, not the new mtx.

The third thing is, that though the new Matrox driver is listed in the proprietary drivers package, it is not used. Status Active, not used.

Any hints, before we can go over to the next problem (which is my Samsung printer)?

---

### Post by az68 on 2007-10-27
Did one thing, that improved the situation a little bit.

Manually edited the xorg.conf file, and changed the driver to mtx.

Now the Matrox display driver is used, and everything works fine.

Nevertheless...
 - Matrox proprietary driver has status not used.
 - mtx driver is not listed in the list of available video drivers.

---

### Post by Finlunch on 2007-12-17
> **az68 said:**
> Did one thing, that improved the situation a little bit.

Manually edited the xorg.conf file, and changed the driver to mtx.

Now the Matrox display driver is used, and everything works fine.

Nevertheless...
 - Matrox proprietary driver has status not used.
 - mtx driver is not listed in the list of available video drivers.

Thank's a lot for a hint :popcorn:
I finally got my Matrox Millennium P650 working.

btw, when mtx-driver was installed i could choose it by reconfiguring xorg with command below
> sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Efrain Valles on 2007-12-30
Hey there...

I own a matrox card... I get terrible video with the mga driver and I can't seem to find the mtx driver in the repositories. I have tried editing the xorg.conf maunally but it is obviouslly not listed in the available drivers. I tried the restricted drivers and It doesn't show anything extra needed. 

my lspci | grep VGA:

```
00:09.0 VGA compatible controller: Matrox Graphics, Inc. MGA 2164W [Millennium II]

```

any help would come in handy

---

