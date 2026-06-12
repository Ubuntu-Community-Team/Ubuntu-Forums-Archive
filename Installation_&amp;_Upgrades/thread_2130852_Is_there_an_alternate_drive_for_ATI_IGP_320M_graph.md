---
title: "Is there an alternate drive for ATI IGP 320/M graphics now using vesa"
date: 2013-03-30
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2013-03-30
I have a Compaq Presarion 2100 using  ATI IGP 320/M graphics (on the motherboard).  I run xubuntu 12.04.2.  The graphics is quite slow on xubuntu and seems to be faster on Windows XP.  In addition, I would like to use compiz for some things.  When I run compiz-check, I get the following:
```
ralph@pres:~$ ./compiz-check_0-4-6

Gathering information about your system...

 Distribution:          Ubuntu 12.04
 Desktop environment:   Xfce
 Graphics chip:         Advanced Micro Devices [AMD] nee ATI RS100 [Radeon IGP320M]
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y
ralph@pres:~$ 
(jockey-gtk:11527): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed
```
When I look at the AMD (ATI) web site [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) , select "Integrated Motherboard Graphics", Radeon ICP Series, Radeon IGP 320, I see that there are drivers available for Windows ME\98, and Windows 2000 Professional.

My questions are:
1.  Is there an alternate driver for the "vesa" drive that Xubuntu is using that is faster?
2.  Is there something like ndiswapper that would allow me to run the Windows 2000 driver?

---

### Post by ManamiVixen on 2013-03-30
Unfortunately support by ATI for your card has ended. Only the open source drivers work now.

---

### Post by Ralph L on 2013-04-03
I do have a working version of XP dual booted with xubuntu.  It must have the windows drivers in it.  Is it possible to extract them some way, and is there a wrapper of some sort that would allow the drivers to be used in xubuntu??????

---

