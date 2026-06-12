---
title: "Install Ubuntu 9.10 on a Toshiba Satellite  U500-ST6344"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by kackley on 2010-02-11
I've recently purchased a Toshiba U500-ST6344 to replace Dell laptops that had Ubuntu for a few years.  

Here's some of the specs:
I3-330M 2.13 GHZ 3MB L3 CACHE  	
Integrated Intel Graphics Media Accelerator HD
Synaptics TouchPad

I've booted from the Live CD and have a few questions:
1. The fan - From what I understand Toshiba laptops have a fan issue that various posts give slightly different answers.  I used boot option "acpi=off".  Is this the correct option to use for this issue?  Also what is the best way to monitor that the fan is operating normally.
2. Graphics - I had to use "Safe Graphics Mode" to be able to use the video card.
3. TouchPad - I'm unable to get a response from the TouchPad or a USB-connected mouse.  Is there a way to get this to work? 

Any help would be appreciated.

Ken

---

### Post by mörgæs on 2010-02-12
Here is some advice regarding the touchpad: 
[http://ubuntuforums.org/showthread.php?t=1401645](http://ubuntuforums.org/showthread.php?t=1401645)

---

### Post by kackley on 2010-02-15
Thanks.  TouchPad working fine but still working through updating configuration for graphics card.

---

### Post by mörgæs on 2010-02-16
Please post the result from ```
hwinfo --gfx
```Regarding overheating: I believe "acpi=off" is the best you can do, but I can not say for sure since I have not had any overheating problem myself (I am mainly using Ubuntu 8.10). Does it feel hot under the belly?

---

### Post by kackley on 2010-02-16
I've updated the xorg.conf to have this:

[INDENT][INDENT]Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
EndSection
[/INDENT][/INDENT]

which will fix the resolution issue and now allow for 1280x800.  However, if I try to do the visual effects option (System -> Preferences -> Appearance -> Visual Effects -> Normal) the laptop freezes.

Here's the output of hwinfo --gfx
[INDENT][INDENT]
08: PCI 02.0: 0300 VGA compatible controller (VGA)              
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_46
  Unique ID: _Znp.EmhdYHEbWf2
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel VGA compatible controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x0046 
  SubVendor: pci 0x1179 "Toshiba America Info Systems"
  SubDevice: pci 0xff40 
  Revision: 0x12
  Driver: "i915"
  Driver Modules: "drm"
  Memory Range: 0xf0000000-0xf03fffff (rw,non-prefetchable)
  Memory Range: 0xe0000000-0xefffffff (rw,prefetchable)
  I/O Ports: 0xe060-0xe067 (rw)
  IRQ: 35 (260 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00008086d00000046sv00001179sd0000FF40bc03sc00i00"
  Driver Info #0:
    Driver Status: i915 is active
    Driver Activation Cmd: "modprobe i915"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Primary display adapter: #8
[/INDENT][/INDENT] 

RE: overheating.  I haven't experienced it as of yet either.  Would be nice to have a monitor to follow the core temp.

---

### Post by mörgæs on 2010-02-16
I just realised that U500-ST6344 is a very new computer. Maybe the hardware detection is better in Ubuntu 10.04.

It is still an alpha, but surprisingly stable (at least on my machine)
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

