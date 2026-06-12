---
title: "Issues with upgrade 12.04 to 14.04 (battery drain, freezes…)"
date: 2015-08-15
forum: Installation &amp; Upgrades
---

### Post by ariel6 on 2015-08-15
I've been using ubuntu 12.04 for over a year without any issues with  my laptop (MSI GT70.) It has an integrated intel graphics card and an  nvidia GTX 870M. Therefore, I have been using the bumblebee project and  it's been working great. When runing 'optirun' command with the  applications I got the power led switch from white to orange to show  that it was indeed using the nvidia gpu and after closing the app it  switched back to white. So far so go. Plus the battery was lasting over 2  and a half hours with full charge, playing some videos in full screen  for example.
  A few weeks ago I upgraded from 12.04 to 14.04. I installed the  bumblebee project as well but now the battery lasts at least 40 minutes.  That's the first issue.
  I thought it may help to do a clean start formatting the root  partition (on an ssd) as well as the home partition (on an hdd) with gparted from a liveUSB. But  when I boot from it, after it starts the complete systems, it freezes  and I cannot even shut it down (ctrl+alt f2,3,....). Could this be related to the dual  graphic cards?. BTW, I'm using ubuntu-14.04.3-desktop-amd64.iso.
  Here is what I get with powertop (tunables tab) with the power cable unconnected in case it helps:

```

   Bad           Wireless Power Saving for interface wlan0                                                              
   Bad           NMI watchdog should be turned off
   Bad           VM writeback timeout
   Bad           Enable SATA link power Managmenet for host0
   Bad           Enable SATA link power Managmenet for host1
   Bad           Enable SATA link power Managmenet for host2
   Bad           Enable SATA link power Managmenet for host3
   Bad           Enable SATA link power Managmenet for host4
   Bad           Enable SATA link power Managmenet for host5
   Bad           Autosuspend for USB device USB-PS/2 Optical Mouse [Logitech]
   Bad           Autosuspend for USB device MSI EPF USB [MSI EPF USB]
   Bad           Runtime PM for PCI Device Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller
   Bad           Runtime PM for PCI Device Intel Corporation 4th Gen Core Processor Integrated Graphics Controller
   Bad           Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1
   Bad           Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2
   Bad           Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1
   Bad           Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3
   Bad           Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5
   Bad           Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1
   Bad           Runtime PM for PCI Device Intel Corporation HM87 Express LPC Controller
   Bad           Runtime PM for PCI Device Intel Corporation 82801 Mobile SATA Controller [RAID mode]
   Bad           Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller
   Bad           Runtime PM for PCI Device NVIDIA Corporation GK104M [GeForce GTX 870M]
   Bad           Runtime PM for PCI Device Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader
   Bad           Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI
   Bad           Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4
   Good          Enable Audio codec power management
   Good          Bluetooth device interface status
   Good          Autosuspend for USB device xHCI Host Controller [usb4]
   Good          Autosuspend for unknown USB device 3-11 (0cf3:3004)
   Good          Autosuspend for USB device xHCI Host Controller [usb3]
   Good          Autosuspend for unknown USB device 2-1 (8087:8000)
   Good          Autosuspend for USB device EHCI Host Controller [usb1]
   Good          Autosuspend for USB device EHCI Host Controller [usb2]
   Good          Autosuspend for unknown USB device 1-1 (8087:8008)
   Good          Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller
   Good          Runtime PM for PCI Device Qualcomm Atheros AR9462 Wireless Network Adapter
   Good          Runtime PM for PCI Device Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller
   Good          Runtime PM for PCI Device Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller
   Good          Wake-on-lan status for device wlan0
   Good          Wake-on-lan status for device eth0
   Good          Using 'ondemand' cpufreq governor
```

Any kind of help will be much appreciated. Thanks in advance.

---

### Post by dino99 on 2015-08-15
try to select the discrete graphic chip from the bios/uefi
if that works, then you will be safe to glance at logs to find the culprit
or boot in recovery mode

---

### Post by ariel6 on 2015-08-15
> **dino99 said:**
> try to select the discrete graphic chip from the bios/uefi
I don't have that option. And it freezes when I boot from the liveUSB. 

I installed 12.04 and then upgraded it to 14.04 rather than directly installing 14.04 from the liveUSB

---

### Post by ariel6 on 2015-08-16
I ran tlp-stat and I got this:

```
+++ Battery Status
/sys/class/power_supply/BAT1/manufacturer                   = MSI
/sys/class/power_supply/BAT1/model_name                     = BTY-M6D
/sys/class/power_supply/BAT1/cycle_count                    = (not supported)
/sys/class/power_supply/BAT1/charge_full_design             =   7800 [mAh]
/sys/class/power_supply/BAT1/charge_full                    =   2466 [mAh]
/sys/class/power_supply/BAT1/charge_now                     =   2387 [mAh]
```

So it means that the battery is not fully charged even though it says  96%. It also says charged rather than keep charging it until it reaches  100%. Why is charge_full not equal to charge_full_design?


  Is there any way to solve this issue? Or it might be really a  hardware issue with the battery rather than a software issue with the  upgrade?

  Thank you.

---

