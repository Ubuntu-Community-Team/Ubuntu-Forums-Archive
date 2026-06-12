---
title: "Need pointers how to edit graphics shutdown - I figured out the USB problem"
date: 2018-03-12
forum: Installation &amp; Upgrades
---

### Post by leemckusic on 2018-03-12
I am writing to ask if anybody can tell me a grub boot parameter to stop the graphics adapter from being turned off when the computer is not touched for a period of time. What I believe is happening is the Power Management timer in the Linux kernel is turning off the graphics display and additionally the same event is switching off the USB keyboard.

Thanks everybody. My eight or ten year old Wind PC has always run Ubuntu. Some kind of trick web page really screwed up my 64 bit Ubuntu LTS. For the past three weeks I have been trying to re-install Ubuntu and most importantly save my /home partition. The good news is I plugged in a 2 Terabyte $65 USB backup drive and I backed up /home. 

The bad news is my system is being plagued with USB keyboards that disappear and a graphics display that disappears together with disappearing the USB keyboard too. I have been forced several times to shut the computer off with the power switch, which in turn requires manually running fsck to repair the damage to the file system.

Here is my guess as to what is happening.The Linux Kernel has power management and it is intended that the kernel can be compiled with different levels of power control so that computers can extend battery life by shutting down peripherals.

[https://www.kernel.org/doc/html/latest/driver-api/usb/power-management.html]("https://www.kernel.org/doc/html/latest/driver-api/usb/power-management.html")

To prevent the kernel from shutting down USB devices, you can add usbcore.autosuspend=-1 to the kernel boot line. In the grub boot loader press "e" and scroll down to 
```
vmlinuz.....1b3df usbcore.autosuspend=-1 ro quiet etc
```

As long as I use the keyboard (and after running fsck to fix damaged disk partitions from the power switch shutdown) the computer is OK. If I leave the computer running over night, the display goes blank and the keyboard shuts down. 

The thing I think is going on is called in the Linux Kernel manual Power Management. What I can't find in the Linux Kernel documentation is an explanation of how to stop the Kernel from shutting down my display adapter because the display adapter code shuts down the USB keyboard also.Or: where is the Ubuntu control instructions located.

---

### Post by leemckusic on 2018-03-17
Well my Ubuntu 16.4.3 Ubuntu upgrade has now taken 44 days with only one fleeting day of use of the upgraded system. Here is the problem so far. 
Ubuntu 16.04.3 appears to have a Power Management system that is interacting badly with my 2008 vintage Logitech keyboard.and my 2008 vintage Wind PC with a relatively early low power Intel Atom cpu.

With the very latest Ubuntu LTS 16.04.3-desktop-amdd64.iso, I was able to do a "something different" install where I specified the / disk partition, /home and /boot partitions. My Grub boot screen has three or four Linux boot options. I have tried the "usbcore.autosuspend=-1 (minus one!) and gotten varying degrees of boot-up. 

Here is a big gotcha: For me the USB keyboard keeps getting shut down and I wind up using the power switch to bail out of the uncontrollable computer. If you do that you have to go back and run fsck /dev/sd.. to fix the disks that were damaged.  Make a paper list of your disk partitions and the last 4 digits of the UUID for each disk to stay sane when you are making trials and reading boot error messages.

i have not looked closely but I think the Ubuntu Install disk is using a Power Management Enabled Linux Kernel, and the kernel's misguided efforts to shut down the USB keyboard is part of the reason why sometimes the USB keyboard freezes. 

That is why this install is so hard. I don't know how to stop the Install CD Kernel from managing my 10 year old USB keyboard. Second, each power switch restart damages the disks. Third, the latest and most modern Kernel even with the usbcore.autosuspend=-1 fix still can't prevent a power saving graphics display shutdown that somehow switches off the USB keyboard even if the previous usbcore command was placed in the boot command.

So following all this out, I had a successful install, I fsck'd the partitions, rebooted and got a text character prompt. I guess I damaged the Xorg start up file. Whose name i do not know.

So that is where I am at... I read the video system is being changed, but I don't know the package names.I can't find in the Kernel.org any writing about how the display adapter shutdown can be controlled or modified. Anybody got any names for me to study?

---

