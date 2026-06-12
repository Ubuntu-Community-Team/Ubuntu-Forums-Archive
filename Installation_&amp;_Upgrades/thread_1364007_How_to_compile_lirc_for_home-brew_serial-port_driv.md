---
title: "How to compile lirc for home-brew serial-port driver Igor Cesko's variation"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by bruma on 2009-12-25
Since version [0.8.5-0ubuntu2]("http://changelogs.ubuntu.com/changelogs/pool/main/l/lirc/lirc_0.8.6-0ubuntu2/changelog") we don't have support for Home-brew serial-port driver Igor Cesko's variation in lirc deb package.

This how-to will show how to recompile (debian/ubuntu way) lirc package to get that support.
This example is for version 0.8.6, but it should work with other versions too.

Get the lirc sources:
> sudo apt-get -d source lirc
Install missing build dependencies:
> sudo apt-get build-dep lirc
Unpack and patch sources:
> tar xzvf lirc_0.8.6.orig.tar.gz
cd lirc-0.8.6/
zcat ../lirc_0.8.6-0ubuntu2.diff.gz | patch -p1


Apply modifications;
in file *debian/modules-source/lirc-modules-source.conf* set LIRC_SERIAL_CFLAGS to:
> LIRC_SERIAL_CFLAGS=" -DLIRC_SERIAL_SOFTCARRIER -DLIRC_SERIAL_IGOR"
at the top of the file *lirc-0.8.6/debian/changelog* insert something like this
> lirc (0.8.6-0ubuntu3) karmic; urgency=low

  * Added -DLIRC_SERIAL_IGOR to lirc_serial module

 -- Your Name <your@email>  Fir, 25 Jun 2009 10:42:45 -0500

This step is optional, but it will provide nicer upgrade of official package. **Note** that we increased package version (3 in 0.8.6-0ubuntu**3**), official latest version was lirc_0.8.6-0ubuntu2.

Build package
> sudo dpkg-buildpackage -rfakeroot -uc -us -sa -d

Install binary packages:
> sudo dpkg -i lirc_0.8.6-0ubuntu3_i386.deb liblircclient0_0.8.6-0ubuntu3_i386.deb
and new modules
> sudo dpkg -i lirc-modules-source_0.8.6-0ubuntu3_all.deb

New installed *lirc_serial* module supports Igor Cesko's variation, we just have to configure it, run:
> sudo dpkg-reconfigure lirc
and select *Home-brew (16x50 UART compatible serial port)*.


That's it! This method could be used for other drivers too.

---

### Post by prshah on 2009-12-25
> **bruma said:**
> Since version [0.8.5-0ubuntu2]("http://changelogs.ubuntu.com/changelogs/pool/main/l/lirc/lirc_0.8.6-0ubuntu2/changelog") we don't have support for Home-brew serial-port driver Igor Cesko's variation in lirc deb package.

Hey thanks for this info. I've been blowing my brains out trying to find out why LIRC doesn't work with the homebrew receiver i've made. 

Now I know.

[s]I'm off to try this[/s]. Maybe over the weekend...

---

### Post by Deusex25 on 2011-03-25
> **prshah said:**
> Hey thanks for this info. I've been blowing my brains out trying to find out why LIRC doesn't work with the homebrew receiver i've made. 

Now I know.

[s]I'm off to try this[/s]. Maybe over the weekend...

Yeah!!! Thanks, thanks, thanks!!!
Absolutely agree!!!
I've especially registered on this forum to say thanks to [U]Bruma!
I've spend one full day, trying to get it working. Now it works! Yahoooo!!!
[/U]

---

