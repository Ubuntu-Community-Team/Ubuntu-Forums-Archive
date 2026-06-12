---
title: "ubuntu will not install because of windows crash"
date: 2014-06-24
forum: Installation &amp; Upgrades
---

### Post by Jason_K on 2014-06-24
My windows 8 crashed, and I do not have a recovery disk for it. I tried installing Ubuntu 13.04, but the installation will not complete because of windows not finding an OS already installed. Is there any way around this? I thought I could just install Ubuntu to replace windows. It says "Could not find the ISO /images/images/raring.iso" and says to reboot into windows and let it fully load, but i obviously cannot do this...

---

### Post by Mark Phelps on 2014-06-24
Sounds like you're trying to install directly from the ISO file -- which you can't do.  You have to boot from media from which the ISO file has been "installed", that is, expanded into its constituent folders and files.

---

### Post by coffeecat on 2014-06-24
Two things.

> **Jason_K said:**
> I tried installing Ubuntu 13.04,

Don't do that. 13.04 is past end of life and unsupported and 13.10 will soon be end of life. If you wish to install Ubuntu, go for the latest LTS (long term support) version which is 14.04 and is available here:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)


> **Jason_K said:**
> It says "Could not find the ISO /images/images/raring.iso" and says to reboot into windows and let it fully load, but i obviously cannot do this...

Where are you seeing that message? Are you running the wubi.exe installer in Windows? Although wubi is still available it is now unmaintained and is best avoided. Neither will it work in Windows 8. See here:

[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

You can burn the ISO to DVD or USB with the advice given in the links in the ubuntu.com page linked above. This gives you a bootable installer/live session from which you can install Ubuntu. Are you sure you want to replace Windows? You may want to ask for further advice about installing Ubuntu to its own partition(s) if you've never done this before.

---

### Post by hakuna_matata on 2014-06-24
> **coffeecat said:**
> 
Are you running the wubi.exe installer in Windows?
IMHO, it is not Wubi, because "/images/images/raring.iso" is not a typical Wubi path name.

---

