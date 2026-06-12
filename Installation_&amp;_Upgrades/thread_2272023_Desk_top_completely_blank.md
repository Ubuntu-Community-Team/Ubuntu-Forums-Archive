---
title: "Desk top completely blank"
date: 2015-04-03
forum: Installation &amp; Upgrades
---

### Post by alan57 on 2015-04-03
I am a recent convert to Ubuntu 14.04.1, having now loaded it successfully to two laptops and one desk top. All was proceeding perfectly fine for the last month until a few days ago when a fault developed on one of the laptops - a Toshiba Satellite C50D. The trouble began with the occasional loss of the mouse arrow at the password screen. The only means of recovery (known to me at least) was to switch off the laptop and crash the machine. This happened a few times and has probably corrupted a file somewhere.
The latest development is that on successfully passing the password screen, I am now presented with a completely blank desktop apart from one folder which contains a few photos as well as the bar at the top right hand corner which allows one to shut down. There is no launcher bar to the left. Strangely logging on as a guest brings me into a desktop that is fully in working order.
I have researched the problem in these forums to the point where my head is spinning but to no avail.
The installation is new so nothing much would be lost in re-installing. So, I tried to re- run Ubuntu 14.04.01 from the original USB and from a DVD having reset the BIOS. However, the corruption that I suspect having taken place prevents the BIOS from recognising the USB or the DVD. On start up before the BIOS runs a 'purple edged' screen runs for a few moments and then the BIOS starts and the outcome is always booting into Ubuntu. By pressing escape and getting in to the Linux recovery mode, I am unable to move the cursor to run any of the options to perhaps check the disk. I am also unable to provide any output as I cannot open a terminal.
I really would appreciate any help or suggestions.

---

### Post by grahammechanical on 2015-04-03
What do you mean "reset the BIOS?" What did you do? It is likely that boot priority is now given to the hard disk. To run an OS from a DVD disc or a USB memory stick we usually give the DVD drive boot priority over the hard drive and something similar is needed for the USB ports. On my machine the BIOS sees the USB stick as an external USB drive and I have to make the adjustment under the boot/hard drive section of the BIOS set up utility.

If resetting means going back to factory defaults then that is why the motherboard is still loading to Ubuntu.

Regards.

---

### Post by alan57 on 2015-04-03
Thanks you for the response. To be clear, all I meant was changing the sequence of the devices that the BIOS selected. In the first case I moved USB to the top of the list leaving the HDD second and the DVD third - there are only 3 options. For the second attempt I moved the DVD to the top followed by the USB.  I did not touch the reset to factory defaults.

---

### Post by mateojonsonguynn on 2015-04-03
I'm not really an expert, but I am pretty sure that the corruption of a hard drive does not affect BIOS, only grub. Just so you can rule out that as the problem.

---

### Post by alan57 on 2015-04-04
Thanks for the insight. I agree that the BIOS is highly likely not at fault.  I think the problem lies within a program running at shut down. On restart immediately after shutdown before the BIOS title screen appears, the screen starts with a thin purple border all around and after about 15 secs the BIOS title screen appears, the HDD drive seemingly takes over and the Ubuntu logo appears.  Even if I press f2 and go into the BIOS as soon as the BIOS title appears and change the boot order, the laptop ignores it and boots to Ubuntu.  So I reason that whatever activity is taking place at shutdown is over-riding the BIOS.
Also far from being at all expert in Linux, I will now research grub to see how that works as I can access a grub screen on start up. Thanks for the pointer.

---

