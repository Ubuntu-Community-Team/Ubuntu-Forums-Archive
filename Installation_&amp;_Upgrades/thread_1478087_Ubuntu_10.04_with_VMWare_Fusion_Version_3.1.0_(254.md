---
title: "Ubuntu 10.04 with VMWare Fusion Version 3.1.0 (254806) Compiz"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by Andreab67 on 2010-05-09
Hi All,
interesting issue I am experiencing on my MacBook Pro.
I have a VM running Ubuntu 10.04.
It is a fresh install.
I installed the latest VmWare tools and everything looks good with the exception of Compiz.

I cannot enable Visual Effects 
*** soon as I try Ubuntu starts looking for Hardware drivers, flash the screen multiple times and then spits the message Desktop Effects Could not be enabled.

If I run compiz-check I get:


andreab@ubuntu:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         VMware SVGA II Adapter
 Driver in use:         vmware
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 


I have been looking on what it means and how to possibly resolve.

My guts feeling is that it has to do with the Monitor Configuration.

The monitor is not detected correctly, do you know how to manually create one instead of letting the system create one?

Monitor is reported Unknown

Any ideas on how to get Compiz working?

3D Support is already enabled in the VM Settings

Thanks

Andrea

---

### Post by georgeMandis on 2010-05-16
Although VMWare Fusion 3.1 support OpenGL, I'm under the impression it is only supported for virtual machines running Windows. 

[http://blogs.vmware.com/teamfusion/2010/03/vmware-fusion-31-beta-now-available.html](http://blogs.vmware.com/teamfusion/2010/03/vmware-fusion-31-beta-now-available.html)

"...support for Windows Vista and Windows 7."

So Ubuntu is giving you this error because it doesn't think your virtualized hardware supports 3D acceleration.

VirtualBox supports OpenGL 3D acceleration for virtualized Linux machines, I think.

---

### Post by rmcellig on 2010-08-14
I am having the same issue. Is there a solution to this problem?

---

### Post by moschops on 2010-09-14
Ditto... this doesn't seem to be well document and is a real shame as otherwise Fusion runs Ubuntu pretty well except for sluggish graphics.

I would probably got to Parallels (or back to VirtualBox) except that Parallels wont migrate my now virtual work machine.

---

### Post by SoulTechnologist on 2011-08-02
Experiencing the same issue with the latest vmware and MBP 8,1. Will try virtualbox and let you know pretty soon.

---

