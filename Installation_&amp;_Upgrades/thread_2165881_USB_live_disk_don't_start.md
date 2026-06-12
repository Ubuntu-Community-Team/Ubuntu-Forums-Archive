---
title: "USB live disk don't start"
date: 2013-08-06
forum: Installation &amp; Upgrades
---

### Post by joaov-ferreira on 2013-08-06
I'm trying to install ubuntu 13.04 amd64, i downloaded the iso and used ubuntu's live disk creator to make a bootable usb flash drive, and when i try to start the installation via the usb drive, it show and error

"Unable to find a medium containing a live file system"

When i tried to install the x86 version from 12.04 LTS, everthing worked fine, but I need the x64 version 

I tried the same usb drive on another computer and it worked fine

my computer is :

AMD FX-8320
XFX Radeon HD 7750
Gigabyte ga-970a-UD3 rev 3.0

---

### Post by sudodus on 2013-08-08
Welcome to the Ubuntu Forums :-)

- Did you try the usb drive with ubuntu 13.04 amd64 in another computer and it worked fine?

In that case the problem is with the computer.

- Did you try another USB port?

- Are you running UEFI?

- Is Windows installed?

- Is it possible (in the BIOS menu) to change the settings of UEFI, fast boot and secure boot?

---

### Post by prookie on 2013-08-08
Hi Ferreira,

  I think that 13.04 is prepared very lousy. If you can stick with older 12.04 revision. It seems much stable and with much less bugs.

  Good luck,
  pRookie

---

### Post by johnnyelias on 2013-08-09
try using  [COLOR=#ff0000]unetbootin[/COLOR] to make your bootable usb flash drive
for all my cases unetbootin better than startup disk creator

---

### Post by joaov-ferreira on 2013-09-01
It was a issue with UEFI, after some tweaks on motherboard's configuration it worked =D
thanks for the help

---

### Post by sudodus on 2013-09-02
You are welcome :-)

---

