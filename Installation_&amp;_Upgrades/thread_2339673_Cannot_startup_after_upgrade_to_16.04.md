---
title: "Cannot startup after upgrade to 16.04"
date: 2016-10-11
forum: Installation &amp; Upgrades
---

### Post by leptonrover on 2016-10-11
I accepted the offered Ubuntu upgrade from 14.04 to 16.04 last week. 
Since then suspension or hibernate has caused problems getting longer and longer to overcome until now I cannot restart. Whilst I can hear the fan in the PC my screen remains black and I cannot progress at all.
Stopping by a long press of the power button and then restarting does not do anything.
Help please!

---

### Post by ajgreeny on 2016-10-11
Much more information is needed before we can offer any real help.

What hardware are you using?
CPU?
RAM?
Graphic card?
etc, etc.

---

### Post by leptonrover on 2016-10-12
That is difficult. I cannot start the PC to get the information - it appears to stuck in hibernation even though I have forced shutdown by a long press of the start button.

---

### Post by ajgreeny on 2016-10-12
You must have some idea, surely.

If you really have no idea at all, what is the brand-name of the machine; laptop, desktop, etc etc?

---

### Post by leptonrover on 2016-10-14
It seems like every thing goes wrong at once!
I eventually concluded that the monitor had gone faulty, replaced that and  that was followed by a non responsive keyboard which has also been replaced.
Now I am back to the original problem. My PC will not wake up after hibernation, I have to 'short press' the power button which then reboots the system - a very  slow process - and start again.

However I have run lshw -short with the following o/p:

 
 H/W path                 Device      Class       Description
 ============================================================
                                      system      SZ77 (To be filled by O.E.M.)
 /0                                   bus         FZ77
 /0/0                                 memory      64KiB BIOS
 /0/3d                                memory      1MiB L2 cache
 /0/3e                                memory      128KiB L1 cache
 /0/3f                                memory      8MiB L3 cache
 /0/40                                memory      16GiB System Memory
 /0/40/0                              memory      4GiB DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
 /0/40/1                              memory      4GiB DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
 /0/40/2                              memory      4GiB DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
 /0/40/3                              memory      4GiB DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
 /0/41                                processor   Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz
 /0/100                               bridge      Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller
 /0/100/1                             bridge      Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port
 /0/100/2                             display     Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
 /0/100/14                            bus         7 Series/C210 Series Chipset Family USB xHCI Host Controller
 /0/100/14/0              usb4        bus         xHCI Host Controller
 /0/100/14/1              usb3        bus         xHCI Host Controller
 /0/100/14/1/3                        input       USB Receiver
 /0/100/1a                            bus         7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
 /0/100/1a/1              usb1        bus         EHCI Host Controller
 /0/100/1a/1/1                        bus         Integrated Rate Matching Hub
 /0/100/1a/1/1/4          scsi6       printer     Photosmart 6510 series
 /0/100/1a/1/1/4/0.0.0    /dev/sdc    disk        Photosmart 6510
 /0/100/1a/1/1/4/0.0.0/0  /dev/sdc    disk         
 /0/100/1b                            multimedia  7 Series/C210 Series Chipset Family High Definition Audio Controller
 /0/100/1c                            bridge      7 Series/C210 Series Chipset Family PCI Express Root Port 1
 /0/100/1c.4                          bridge      7 Series/C210 Series Chipset Family PCI Express Root Port 5
 /0/100/1c.4/0            wlan0       network     RTL8188CE 802.11b/g/n WiFi Adapter
 /0/100/1c.5                          bridge      7 Series/C210 Series Chipset Family PCI Express Root Port 6
 /0/100/1c.6                          bridge      7 Series/C210 Series Chipset Family PCI Express Root Port 7
 /0/100/1c.6/0            p6p1        network     RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
 /0/100/1c.7                          bridge      7 Series/C210 Series Chipset Family PCI Express Root Port 8
 /0/100/1d                            bus         7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
 /0/100/1d/1              usb2        bus         EHCI Host Controller
 /0/100/1d/1/1                        bus         Integrated Rate Matching Hub
 /0/100/1d/1/1/6          scsi7       storage     Desktop
 /0/100/1d/1/1/6/0.0.0    /dev/sdd    disk        2199GB Desktop
 /0/100/1d/1/1/6/0.0.0/0  /dev/sdd    disk        2199GB  
 /0/100/1f                            bridge      Z77 Express Chipset LPC Controller
 /0/100/1f.2                          storage     7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode]
 /0/100/1f.3                          bus         7 Series/C210 Series Chipset Family SMBus Controller
 /0/1                     scsi0       storage      
 /0/1/0.0.0               /dev/sda    disk        2TB ST2000DM001-1CH1
 /0/1/0.0.0/1             /dev/sda1   volume      745GiB Linux raid autodetect partition
 /0/1/0.0.0/2             /dev/sda2   volume      7629MiB Linux swap volume
 /0/1/0.0.0/3             /dev/sda3   volume      1110GiB Linux raid autodetect partition
 /0/2                     scsi1       storage      
 /0/2/0.0.0               /dev/sdb    disk        2TB ST2000DM001-1CH1
 /0/2/0.0.0/1             /dev/sdb1   volume      745GiB Linux raid autodetect partition
 /0/2/0.0.0/2             /dev/sdb2   volume      7629MiB Linux swap volume
 /0/2/0.0.0/3             /dev/sdb3   volume      1110GiB Linux raid autodetect partition
 /1                                   power       To Be Filled By O.E.M.
 /2                       virbr0-nic  network     Ethernet interface


Perhaps this will help.
Roger

---

### Post by ajgreeny on 2016-10-15
It is always possible that your hardware is simply incapable of hibernating properly from Ubuntu, which is precisely why the hibernation option was removed from the *ubuntu family of OSs some time ago and has to be added back in manually by editing system files.

I used to use hibernation some years ago in much earlier versions of Ubuntu but have not done so for a long time now as it took as long to recover from hibernation as it did to cold boot so was of very little advantage to me.

---

### Post by leptonrover on 2016-10-16
Thank you.

I have, I think, now understood the difference between suspending the display and hibernation. I have set hibernate to 'never' and switch off display to '10mins' and that works for me.

That leaves the other problems:
- Why so long to boot up?
- Why do Libre Office and GIMP take so long to start up?
- Also GRAMPS included an updated version with 16.04 which is causing me problems. 
All these make me think I would have been better of sticking with 14.04 - I may even seek to roll back.

---

