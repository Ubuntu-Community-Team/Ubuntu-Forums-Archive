---
title: "ubuntu dvd and poweroff"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by gala.martin on 2007-04-16
hello!
 I would like to ask one question and some help about an issue. First, the easy question:
-what is the difference between the liveCD and the DVD? I guess you can find lots of additional packages in the DVD... nothing more?

Then the hard issue. This was happening already in Dapper and Edgy. A few months ago I switched to the Feisty prelease, but the problem was not solved. I mainly use fluxbox and GNOME, eventually some other WM, and all of them give me the same trouble. When I try to log out, the system freezes, and I have to switch it off manually. I am the only user on my PC, so it is not very annoying, but sometimes it is. The same problem happens when I try to "poweroff" or "reboot", although these two commands work correctly with a good 50% chance. Also "shutdown" does not close properly X.

I think the issue is related to closing X. Generally I close all the windows and applications before logging out, but then the system just stops. All I get is a solid colour background (which is my default background), with the mouse pointer still working, but everything else completely unresponsive. Unfortunately I cannot run any command while in this state.

 Thank you
Regards

---

### Post by gala.martin on 2007-04-18
Bump

---

### Post by spd106 on 2007-04-18
The DVD gives you both the live environment and the .deb packages. Plus lots of other packages (Apache, PHP etc), though they are of more interest to developers and sys-admins than desktop users.

Your shutdown issue sounds interesting, what kind of video card are you using and which driver? Have you checked the logs in /var/log/ for any errors?

---

### Post by gala.martin on 2007-04-19
Thanks for your answer. I am using a Sis video card on a laptop. That gives me some troubles. I had also tried to change the drivers and recompile the kernel, but it did not improve much ](*,) (now I am running the standard feisty configuration).  More precisely, here what I get in /etc/X11/xorg.conf

> 
Section "Device"
	Identifier	"Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

and here what I get from lshw
> 
*-pci
          description: Host bridge
          product: 650/M650 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: ec000000
          bus info: pci@00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
          resources: iomemory:ec000000-efffffff
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: 65x/M650/740 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga cap_list
                configuration: latency=0
                resources: iomemory:f0000000-f7ffffff iomemory:eb800000-eb81ffff ioport:d800-d87f irq:9
        *-isa
             description: ISA bridge
             product: SiS962 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0


I did not find much in the logs. Some minor issues are in /var/lof/Xorg.0.log, but I do not really know what to look for. In any case, here some lines from this file

> 
(--) SIS(0): sisfb not found


> 
(II) SIS(0): WARNING: Using the Hotkey might freeze your machine, regardless
(II) SIS(0):          whether enabled or disabled. This is no driver bug.
(==) SIS(0): SiSCtrl utility interface is disabled


> 
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!


and there are also a lot of these
> 
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)


Thanks again :)

---

### Post by gala.martin on 2007-05-10
bump

---

