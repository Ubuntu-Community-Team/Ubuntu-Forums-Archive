---
title: "Nouveau issues after upgrade - able to login but nothing else"
date: 2019-05-01
forum: Installation &amp; Upgrades
---

### Post by moodog on 2019-05-01
I upgraded my desktop (which is reasonably old) to 19.04, which went fine. When it booted up again I was able to get to the login screen, select my user, type my password and login. I saw the desktop with the dock down the side. the Mouse moves on screen, but nothing else will work.

the graphics card in the box is NVIDIA Corporation G94 [GeForce 9600 GT] (rev a1)

I can ssh ok to the desktop from my laptop. When I first checked dmesg I saw 3 errors similar to:

nouveau 0000:02:00.0: vp: unable to load firmware nouveau/nv84_xuc00f

Note that these errors don't appear on boot up – i.e. when the login is displayed. They're only logged after logging in.

Google didn't give me much, however I found some discussion about firmware missing here:

[https://nouveau.freedesktop.org/wiki/VideoAcceleration/](https://nouveau.freedesktop.org/wiki/VideoAcceleration/)

I then followed the instructions under the section with header:

"If your distribution isn't in the list, you can run the following commands to install the firmware:"

The errors listed via dmesg then disappeared, however the symptoms are still the same. Clicking on icons, typing keyboard etc. does nothing, after initial login.

Any tips? :)

---

### Post by kc1di on 2019-05-01
Have you tried puting nomodeset in the grub boot line?

---

### Post by rsteinmetz70112 on 2019-05-01
Were you using the proprietary Nvidia drivers prior to the upgrade?
If so make sure they were removed. That has caused me problems with some recent upgrades.
Also the desktop and desktop manager may be causing problems. I've had that happen as well.

If that doesn't work please post information on you video drivers,

---

### Post by moodog on 2019-05-05
I tried nomodeset but it didn't change anything.

I thought I was running the nvidia driver before update, but checking for it now I can't find any nvidia packages installed.

When you say "post information on your video drivers" what specifically do you suggest?

lshw -c video shows the following

  *-display UNCLAIMED       
       description: VGA compatible controller
       product: G94 [GeForce 9600 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:fa000000-faffffff memory:c0000000-dfffffff memory:f8000000-f9ffffff ioport:bc00(size=128) memory:c0000-dffff



lspci -nnk | grep -i vga -A3

returns

02:00.0 VGA compatible controller [0300]: NVIDIA Corporation G94 [GeForce 9600 GT] [10de:0622] (rev a1)
	Subsystem: NVIDIA Corporation G94 [GeForce 9600 GT] [10de:070e]
	Kernel modules: nvidiafb, nouveau



63-2) ...
Setting up hwinfo (21.63-2) ...
Processing triggers for man-db (2.8.5-2) ...
Processing triggers for libc-bin (2.29-0ubuntu2) ...
farnsy@spankybigboylinux:~$ sudo hwinfo --gfxcard
14: PCI 200.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.386]
  Unique ID: B35A.ffBy_Wmqel7
  Parent ID: 3hqH.TGxeZMWt_E8
  SysFS ID: /devices/pci0000:00/0000:00:03.0/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: graphics card
  Model: "nVidia G94 [GeForce 9600 GT]"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0622 "G94 [GeForce 9600 GT]"
  SubVendor: pci 0x10de "nVidia Corporation"
  SubDevice: pci 0x070e 
  Revision: 0xa1
  Memory Range: 0xfa000000-0xfaffffff (rw,non-prefetchable)
  Memory Range: 0xc0000000-0xdfffffff (ro,non-prefetchable)
  Memory Range: 0xf8000000-0xf9ffffff (rw,non-prefetchable)
  I/O Ports: 0xbc00-0xbc7f (rw)
  Memory Range: 0x000c0000-0x000dffff (rw,non-prefetchable,disabled)
  IRQ: 15 (no events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v000010DEd00000622sv000010DEsd0000070Ebc03sc00i00"
  Driver Info #0:
    Driver Status: nvidiafb is not active
    Driver Activation Cmd: "modprobe nvidiafb"
  Driver Info #1:
    Driver Status: nouveau is active
    Driver Activation Cmd: "modprobe nouveau"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #38 (PCI bridge)

---

### Post by jglen4902 on 2019-05-05
The > ubuntu-drivers command line utility will help install the recommended driver for your Nvidia card.  Yes, you could also use apt to install something very specific, but it seems like you just need to get your Nvidia environment running first.

---

### Post by moodog on 2019-05-12
So this is still a little weird, and I'm not sure it's related to video now... or not entirely.  the following is now displayed in dmesg:

[   21.326352] WARNING: kernel stack frame pointer at 00000000d4fbb38d in Xorg:2363 has bad value 000000008700762a
[   21.326354] unwind stack type:0 next_sp:          (null) mask:0x2 graph_idx:0

followed by stacks of lines with hex values. 

However the display is all appearing fine and if (eg.) I plug in an external device the device notification is displayed. The time is updating, other notifications update regularly. I can move the mouse, but no click appears to register. Also keyboard doesn't appear to be working within x - I can Ctrl-Alt-F<x> and get to a terminal. sometimes a key press will register, although it may take a long time - i.e. I hit the Win key a while ago, and the search box has just appeared. Remoting in and looking at cpu usage, there is nothing running too hard. I haven't found any other obvious errors.

I'm going to boot of a live USB shortly and see what happens - if all's good, I may reinstall, however would prefer not to have to...

---

