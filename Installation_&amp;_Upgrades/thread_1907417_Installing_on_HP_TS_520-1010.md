---
title: "Installing on HP TS 520-1010"
date: 2012-01-11
forum: Installation &amp; Upgrades
---

### Post by malkuth123 on 2012-01-11
I am trying to install on a brand new HP touchscreen all in one.

I tried to load directly off of the CD, to no avail. I then attempted wubi install. The Linux system boots (using no acpi) and goes to start the graphical interface. It flashes the screen several times and I even get the old vga x in the center of the screen. The video modes that it tries do not work. (I get scrambled garbage on the top of the screen.) Then it reboots.

What can I try?

---

### Post by 2F4U on 2012-01-11
Try the X troubleshooting guide

[https://wiki.ubuntu.com/X/Troubleshooting](https://wiki.ubuntu.com/X/Troubleshooting)

---

### Post by malkuth123 on 2012-01-11
I looked at the documentation you mentioned above. However, that does not apply well when you cannot bring the system up to look at anything.

I was able to bring the system up enough to bring up a tty screen (ctlr/alt/f1). This was accomplished by booting the "live CD" with the options noapic and nomodeset. The following is information that I have gathered from the machine....

I executed vbetool vbemode get and it returned a value of 3.

lspci reports VGA compatable nVidia Corp GF106 (GeForce GT 555M)
lsmod is reporting drm -> nouveau and video -> noveau.

dmesg reports Console colour VGA 80x25
init: lightdm process terminated with status 1.

xorg.log.0 reports:
Failed to load mondul nVidia
drm failed to open device
segfault in libXi.so.6.1.0

There does not seem to be an Xorg.conf file anywhere on this machine at this point. (Find cannot find one, anyway)

I cannot even get to a console screen when using wubi. I also do not know how to make permanent changes on my live CD (it is installed on a USB memory stick), if I could somehow come up with a method of getting the system to boot properly.

Assistance would be appreciated.

---

### Post by malkuth123 on 2012-01-14
Still waiting on a response.

---

