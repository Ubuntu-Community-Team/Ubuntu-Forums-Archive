---
title: "Dual Core Athlon64 and nvidia BUG/Problem"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by clpc on 2007-02-03
There appears to be a BUG/Problem with AMD Dual Core Athlon64 and nvidia drivers, if anyone know of a solution I will be forever grateful.

The Kit...
AMD Athlon64 dual core
foxconn NF4SK8AA motherboard
nvidia 7300GS graphics card

The Problem.
uname -r = 2.6.17-10-generic.
I install the nvidia drivers and linux-restricted-modules.
reboot
Once the splash is complete the system APPEARS to hang with a blank screen, actually if you are just patient and wait for 10 minutes the login window will appear.
Once logged in everything works fine and hardware acceleration is working excellent.
As long as I don't mind waiting 10 minutes on every boot up all is well.

Some Info...
dmesg shows me where the 10 minutes was wasted.
I have 3 entries at the points where minutes went by with no action, these enties say...
BUG: soft lockup detected on CPU#0!
BUG: soft lockup detected on CPU#1!
BUG: soft lockup detected on CPU#0!

If I change back to the default nv driver the problem vanishes, so I am assuming this has something to do with the nvidia drivers.

I have installed the standard, alternative and 64bit versions of Ubuntu and the results are identical in all.

---

### Post by clpc on 2007-02-06
I have solved this problem with information I found on the internet.

If anyone else runs into this problem here is the solution I found.

Create a file with this: sudo gedit /etc/modprobe.d/nvidia
Add this line to it:

options nvidia NVreg_DeviceFileUID=0 NVreg_DeviceFileGID=33 NVreg_DeviceFileMode=0666 NVreg_SoftEDIDs=0 NVreg_Mobile=1

The above line is a single line although it may be word wrapped in this forum.

Then add this line...

Option         "ConnectedMonitor" "DFP"

to the devices section of xorg.conf and then reboot and all should be okay

I hope this helps some one else.

---

### Post by davidrools on 2007-04-26
I get the same problem but I'm on a Core 2 duo with two ATi Radeon x1600pro's.  I'm still searching for a fix. I've tried the 64 bit and the alternative versions but all do the same.  I'll try following something similar to your fox for the AMD/nVidia setup and see how it goes.

---

