---
title: "Install help (no cdrom, no floppy, and no usb)"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by bryancoe on 2006-09-17
Hi Folks,

I'm having some trouble getting Ubuntu installed on my laptop (Panasonic Toughbook CF-M34, PII 300MHz).  This machine has no cdrom, no floppy, and cannot boot from USB.  In short, I'm stuck with booting from the HD.  Currently I am running Gentoo on this machine as Gentoo's ultra low level boot-strapping made it relatively simple to get the base system installed onto the HD while it was installed in my desktop and then finish the installation in the M34.  This is not the case with Ubuntu as there seems to be much hardware detection and trimming of extraneous packages during the install.  Installing to the laptop HD and then transplanting results in immediate freezing of the system on boot.

I have been through the various install guides and have been trying to boot from HD-installed grub into a raw partition containing the Ubuntu ISO.  The system starts to boot, but the always hangs early on, somewhere in the mounting of the ISO (sheepishly, I do not recall the exact message).

I would be very thankful for any insight anyone has to offer concerning this installation.

-Bryan

---

### Post by bernied on 2006-09-17
You could try what is called (I think) a network debootstrap. This is a debian method that almost works well with Ubuntu. Wait a sec, I'll have a better look...

You could also buy a USB cd-rom, then use your gentoo grub to boot it, a bit like you tried with the ISO. But it's a big investment if you don't know that it will work.

back in a sec...

---

### Post by bernied on 2006-09-17
Right, there's a bit of a howto on this. Maybe you've already tried it?
[http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apcs03.html](http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apcs03.html)

---

### Post by bernied on 2006-09-17
I think you might still be able to do the install on desktop, then transfer to laptop thing. But you would need to build your own kernel for the machine - in fact just use the gentoo one that you're already running on the laptop.

Then you just need to fix the network interface and /etc/fstab (maybe a few other bits)

---

### Post by bernied on 2006-09-17
I think the 'few other things' include which modules to load on startup - this I don't understand in ubuntu - it's not the same as gentoo anyway.

---

### Post by bryancoe on 2006-09-17
Thanks for the input, bernied.  I had not seen the info on installing from an existing linux install.  With my current setup, that seems like the most viable.

-B

---

