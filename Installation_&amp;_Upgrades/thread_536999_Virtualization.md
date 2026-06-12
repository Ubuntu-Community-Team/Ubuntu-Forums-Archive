---
title: "Virtualization?"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by invertedpanda on 2007-08-28
New machine parts will be here tomorrow. AMD X2 4200+ Windsor processor, 2gb DDR800 ram, etc etc...

Anyway, I need to run Windows with direct access to the hardware - as a host OS, or through some other virtualization alternative (this is for my recording/audio work). However, I also want to run Linux (my preferred OS - Ubuntu, of course). I used to just run one or the other inside QEMU (way back when it was hyped up with the release of KQEMU), but I'm wondering if there is a better solution. I'd like to still have 3d accel. support while under Linux, but as far as I know, no full virtualization solutions (available free, of course) support 3d acceleration.

I prefer using Linux for my photography processing work, web development, programming, as well as casual computing (word processing, surfing the web, etc). Only reason I use Windows is for games & composing/recording.

Times have changed, so I am wondering if anybody here has any experience they can offer me regarding the current virtualization solutions available.

---

### Post by jeremyphares on 2007-08-30
Probably the easiest way these days is to use [Wubi]("http://wubi-installer.org/"). All you have to do is install windows and then you install Wubi and it installs Ubuntu inside a file that sits on your hard drive, not partitioning needed. Also it uses the windows boot loader. If for some reason you ever need or want to uninstall ubuntu you can do so just like you would uninstall any other program under windows. 
As far as virtualization, other than proprietary solutions such as VMware, QEMU is the only thing I've ever used.

---

### Post by grmmog on 2007-08-31
KVM is my favorite way for virtualization.  Your processor will need to support AMD-v or Intel-vt.  It uses modified Qemu so familiarity with that will help.

On the Windows side Virtual PC is pretty good.  Linux isn't officially supported but it'll work.

---

