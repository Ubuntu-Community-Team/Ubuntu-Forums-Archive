---
title: "Is it possible to start an USB-live v12.04 with an ATI video card ?"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by ValeryBruniaux on 2012-04-29
Hello,

The ubuntu-12.04-desktop.iso on an USB-live can't start the X server with my **ATI HD 5770**. I try severals boot options and differents drivers but startx everytime crashes.

I use the same USB-live to install on my netbook and it's done perfectly so, **the ISO is ok**.

My wife uses the **same computer but with a Nvidia GT440** and it **works**.

So, I think there's a **problem with ATI drivers in the 12.04** because the 11.10 works perfectly.

Is there any solution for ATI HD 57xx cards ?

Thank you very much.

---

### Post by oldfred on 2012-04-30
Welcome to the forums.

I have nVidia and have had to use nomodeset to boot for the last few versions until I get the nVidia driver installed.

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

About halfway down are some suggestions for ATI. Have you tried nomodeset?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If booting from USB it just may be easier to edit syslinux with whatever boot parameters you need like this:
Ubuntu 12.04 has been officially released and, with minor adjustments, the intel gma500 video card is working out of the box.
[http://blog.bodhizazen.net/](http://blog.bodhizazen.net/)
simply edit “syslinux.cfg”

---

