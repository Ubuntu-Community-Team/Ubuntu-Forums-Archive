---
title: "GeForce 2 MX + Ubuntu 9.10 Installation Instructions"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by seierson on 2010-01-16
Hi Gang,

I spent about 3 to 5 hours getting my Nvidia GeForce 2 MX working in Ubuntu 9.10.  Oh I could get it to work right away just not at anything higher than 640x480 which without panning is completely useless by the way. I tried xrandr, cvt, gtf, and manually editing my xorg.conf, using pico or gedit but to no avail.  

In the hopes that future users won't have such a horrible time of it please do the following:
1.  Click System --> Administration --> Hardware Drivers
2.  Install v96 or higher of Nvidia's proprietary driver
3.  Bring up a terminal (you may have to reboot before this works.  I haven't tested that part, but I don't think it's required)
4.  sudo nvidia-xconfig
5.  gksudo nvidia-settings
6.  On the left hand menu tree select "X Server Display Configuration"
7.  Select the desired Resolution, Refresh Rate, and Color Depth
8.  Click [Save to X Configuration File]
9.  Click [Save]
10. Click [Quit]
11. Click [Ok]

If these instructions work in a different distribution of GNOME, I'm also interested in hearing about that.  

Happy Installing,
Christian Blackburn
Thank you's are strongly encouraged :)

---

### Post by mörgæs on 2010-01-20
Thanks, but it did not work for me. 

When applying the Nvidia 96 driver as described, the screen is more or less a mess, and soon the machine will crash. This is the case both with Ubuntu 8.10, 9.04 and 9.10. 

I can get the machine into a higher resolution, but it is highly unstable.


Does anybody have an idea of what can be done?

---

### Post by mörgæs on 2010-01-21
Here is a screenshot and the results from **hwinfo --gfxcard**

```
23: PCI 200.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_1a0
  Unique ID: B35A.Q_T+JOxebUF
  Parent ID: 6NW+.iwKsjRIDKL6
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: graphics card
  Model: "nVidia GeForce2 Integrated GPU"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x01a0 "GeForce2 Integrated GPU"
  SubVendor: pci 0x10de "nVidia Corporation"
  SubDevice: pci 0x0c11 
  Revision: 0xb1
  Driver: "nvidia"
  Driver Modules: "nvidia"
  Memory Range: 0xec000000-0xecffffff (rw,non-prefetchable)
  Memory Range: 0xf0000000-0xf7ffffff (rw,prefetchable)
  Memory Range: 0xefff0000-0xefffffff (ro,prefetchable,disabled)
  IRQ: 19 (41125 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v000010DEd000001A0sv000010DEsd00000C11bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: nv
  Driver Info #1:
    XFree86 v4 Server Module: nvidia
    3D Support: yes
    Color Depths: 16
    Extensions: 
    Options: 
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #21 (PCI bridge)

Primary display adapter: #23

```

---

### Post by Grenage on 2010-01-23
Hi, mörgæs.

How does your display look when using the "nv" driver in xorg.conf?  I know it lacks acceleration, but it's a good start for testing.  Have tried it on any other OS, or the live CD?  How did it look then?

---

### Post by mörgæs on 2010-01-23
Hi Grenage, thanks for your answer.

I have not tried an nv-driver. How do I install that, please? I can live with the driver being slow if only I can get a better resolution than 800*600.

Puppy Linux runs in higher resolution, and in the bad old days the machine ran Windows 2000 also in high resolution. Yes, I know it is old hardware...

---

