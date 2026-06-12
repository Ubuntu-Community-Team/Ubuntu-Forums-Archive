---
title: "graphic card drivers"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by jasper-two on 2007-11-18
Hi just loaded Ubuntu 7.10

Going great but my Graphic card is not working, After checking for the drivers I get a message ]RESTRICTED AVIDIA DRIVER how do I find this driver for a Geforce 8500 Gt
Driver ( Avidia-glx-new )
Can any body help?:confused:

---

### Post by rmemm on 2007-11-24
Generally NVidea video cards can be driven by a number of drivers.  These include:

[LIST]
[*]nv driver - the opensource driver
[*]nvidia - the "restricted" nvidia driver - free but binary only
[*]a number of generic non-accelerated drivers including vga, vesa, fbdev
[/LIST]

The restricted driver should be in synaptic -- just search for it -- you just need to install it.  Might need to configure it in xorg.conf -- don't know if it auto configures or not.  By search I mean just search for say "nvidia" in synaptic.

Rob

---

### Post by sirdilznik on 2007-11-24
You need to first enable the restricted repositories in Synaptic in order for the nvidia-glx-new driver to become available.

---

### Post by Pumalite on 2007-11-24
Or you can try this:
For 8600-8800 GT

When grub comes up select the second ubuntu option.

When its finished you should now have a terminal.

login

run sudo passwd

setup your 'root' password

now run

sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

sudo shutdown -r now

Then use the normal option to boot ubuntu.


Hopefully you'll have an xserver

---

