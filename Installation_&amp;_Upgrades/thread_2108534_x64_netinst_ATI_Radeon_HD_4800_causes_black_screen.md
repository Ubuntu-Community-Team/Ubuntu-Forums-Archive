---
title: "x64 netinst ATI Radeon HD 4800 causes black screen"
date: 2013-01-24
forum: Installation &amp; Upgrades
---

### Post by Rz666 on 2013-01-24
Hey there,

Yesterday I tried to install Ubuntu on my other PC, due to the fact that I have no DVD's and not a proper USB flash drive I decided to download the netinst "mini" version of Ubuntu.

Source:
[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/)

However, each of these options:

[LIST]
[*]Install
[*]Command line install
[*]Recovery
[/LIST]
Each of these options will result in (Note: changed "quiet" to "noquiet"):

> Loading Linux.......
Loading initrd.gx...................Ready

*Blank screen*So after a reboot I tried to press TAB to edit the "Install" menu entry.
The default is:
```
linux vga=788 initrd=initrd.gz -- quiet
```The system on which I am trieing to install Ubuntu has an [COLOR=DarkRed]ATI Radeon HD4800[/COLOR] graphics card. And after some searches I see this is a common problem.
The things that are recommended, to change the line with the things:

[LIST]
[*]nomodeset
[*]radeon.modeset=0
[*]noacpi
[*]acpi=off
[*]acpi_osi=
[*]acpi_osi="Linux"
[*]acpi=ht
[*]noapic
[*]nolapic
[/LIST]
However I don't have any experience with the these boot parameters. How should my line look like when I add one (or more) of these parameters?
Would this problem also occur when I use a DVD with the full installation instead of the "mini" ISO?




Thanks in advance!

---

### Post by Mark Phelps on 2013-01-25
AMD dropped restricted driver support for their HX 2x/3x/4x cards last summer, so you need to ensure that you are NOT trying to use the AMD restricted drivers, otherwise, all you'll get is a black screen.,

---

### Post by Rz666 on 2013-01-26
> **Mark Phelps said:**
> AMD dropped restricted driver support for their HX 2x/3x/4x cards last summer, so you need to ensure that you are NOT trying to use the AMD restricted drivers, otherwise, all you'll get is a black screen.,

Thanks for your reply, how do I make sure that i'm not using these drivers? (Do I need to install other drivers?) I managed to install the Debian distro in the meanwhile but I prefer to use Ubuntu.

---

