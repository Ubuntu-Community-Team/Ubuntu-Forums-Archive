---
title: "Install CD Boot Issues"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by cprofitt on 2007-03-22
I am trying to install Ubuntu on a second machine and the install CD takes both LCD monitors and kills them.

One reports out of range while the other just has lines running through it.

The system is as follows:

Intel D865GRH
Pentium 4 3Ghz
Nvidia 6800 AGP
1 GB Ram
The primary LCD is off the DVI head and is a View Sonic VX910
The secondary LCD is off the VGA head and is a Rosewill

I am unsure of how to proceed.

---

### Post by twikletoes on 2007-03-23
when it comes to the first screen that gives all the install options tap F4 and choose a screen resolution that it might work on.

---

### Post by cprofitt on 2007-03-23
Actually I found that I had to do the following:

[PHP]
press F6 at the first menu screen

delete "quiet-splash" and replace it with break=bottom

start the CD

when I get to the prompt

chroot /root nano /etc/X11/xorg.conf

scroll down to the device section and replace "nv" with "vesa"

hit cntl+o

hit cntl+x

type exit at the prompt

it then let me load the software and kept the vesa driver.

I was then able to download the nvidia driver by using add/remove programs.
[/PHP]

---

