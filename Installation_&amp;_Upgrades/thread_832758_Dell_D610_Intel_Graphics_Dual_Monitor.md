---
title: "Dell D610 Intel Graphics Dual Monitor"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by ipvidiot on 2008-06-18
I have a Dell d610 with Intel Corporation Mobile 915GM/GMS/910GML graphics.  Using the dock I have DVI and VGA Out. I would like to have dual monitors with my desktop across both monitors.  lspci shows intel graphics on two different locations on the bus.

After reading much on this forum and trying many combinations, I have the DVI out working.  Using the i810 switch package the VGA can be turned on to clone the DVI.  Also I use 915resolution to get 1680x1050 for the two DELL E207WFP monitors.

**When using both outputs of the dock, and the lid of the laptop closed, should both of the video cards that show up with lspci be used?**

Most of the posts I have read are using the laptop screen and an external monitor.

Thanks

---

### Post by ipvidiot on 2008-06-18
Output of lspci

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

part of Xorg.log


(**) I810(0): Device Presence: enabled.
(II) I810(0): Display Presence: CRT: attached: TRUE, encoder: TRUE
(II) I810(0): Display Presence: TV: attached: FALSE, encoder: TRUE
(II) I810(0): Display Presence: DFP (digital flat panel): attached: TRUE, encoder: TRUE
(II) I810(0): Display Presence: LFP (local flat panel): attached: TRUE, encoder: TRUE
(II) I810(0): Display Presence: Second (second CRT): attached: FALSE, encoder: FALSE
(II) I810(0): Display Presence: TV2 (second TV): attached: FALSE, encoder: FALSE
(II) I810(0): Display Presence: DFP2 (second digital flat panel): attached: FALSE, encoder: FALSE
(II) I810(0): Display Presence: LFP2 (second local flat panel): attached: FALSE, encoder: FALSE
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
              If you encounter this problem please add 
                 Option "DisplayInfo" "FALSE"
              to the Device section of your XF86Config file.
(II) I810(0): Display Info: CRT: attached: TRUE, present: TRUE, size: (720,400)
(II) I810(0): Display Info: TV: attached: FALSE, present: TRUE, size: (1024,768)
(II) I810(0): Display Info: DFP (digital flat panel): attached: TRUE, present: TRUE, size: (1680,1050)
(II) I810(0): Display Info: LFP (local flat panel): attached: TRUE, present: TRUE, size: (1400,1050)
(II) I810(0): Display Info: Second (second CRT): attached: FALSE, present: FALSE, size: (0,3343)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,3343)
(II) I810(0): Display Info: DFP2 (second digital flat panel): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: LFP2 (second local flat panel): attached: FALSE, present: FALSE, size: (0,3343)
(II) I810(0): Size of device DFP (digital flat panel) is 1680 x 1050
(II) I810(0): Currently active displays on Pipe A:
(II) I810(0):   DFP (digital flat panel)
(II) I810(0): Lowest common panel size for pipe A is 1680 x 1050
(II) I810(0): No active displays on Pipe B.
(==) I810(0): Display is using Pipe A
(--) I810(0): Maximum frambuffer space: 65368 kByte
(II) Loading sub module "ddc"

---

### Post by ipvidiot on 2008-06-20
Is this in the wrong forum?

---

### Post by ipvidiot on 2008-06-21
Section "Device"
	Identifier  "intel"
	Driver      "i810"
	Screen 		0
	BusID       "PCI:0:2:0"
	Option      "VBERestore" "true"
	VideoRam    131072
	Option      "BackingStore" "true"
	Option      "BusType" "PCIE"
	Option      "NoAccel" "false"
	Option      "DRI" "true"
	Option "MonitorLayout" "CRT,LFP"
EndSection

Section "Device"
	Identifier  "Device1"
	Driver      "i810"
	Screen		1
	BusID       "PCI:0:2:0"
#	Option      "VBERestore" "true"
	VideoRam    131072
	Option      "BackingStore" "true"
	Option      "BusType" "PCIE"
	Option      "NoAccel" "false"
	Option      "DRI" "true"
	Option "MonitorLayout" "CRT,LFP"
EndSection


This almost worked.  The mouse pointer appeared and I was able to move it from one monitor to another.  Then X crashed...........  

I did change CRT,LFT to CRT,DFP. Also changed the identifiers to match.

This is from: [http://www.linux-on-laptops.com/forum/showthread.php?t=1486&highlight=dual+monitor](http://www.linux-on-laptops.com/forum/showthread.php?t=1486&highlight=dual+monitor)

---

### Post by ipvidiot on 2008-06-21
Hopefully I can get this to work using something from here:

[http://ubuntuforums.org/showthread.php?t=373959](http://ubuntuforums.org/showthread.php?t=373959)

---

### Post by ipvidiot on 2008-06-26
> **ipvidiot said:**
> Hopefully I can get this to work using something from here:

[http://ubuntuforums.org/showthread.php?t=373959](http://ubuntuforums.org/showthread.php?t=373959)

Using the dual monitor xorg config file from the above link it's almost working, except I can't get above 1280x1024 on the monitor 1.

---

### Post by ipvidiot on 2008-10-02
Bump

---

