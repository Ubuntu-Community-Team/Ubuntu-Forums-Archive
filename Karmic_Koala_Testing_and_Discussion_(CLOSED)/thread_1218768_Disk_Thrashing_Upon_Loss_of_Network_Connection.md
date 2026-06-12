---
title: "Disk Thrashing Upon Loss of Network Connection"
date: 2009-07-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by brianafischer on 2009-07-21
I am experiencing some scary disk thrashing if I don't have a network connection on my Dell D830.  I would like to make sure this is a valid bug before creating a report and would like some assistance on tracking down the issue.  I would appreciate any advice on what the next step should be.

```
Linux latitude-laptop 2.6.31-3-generic #19-Ubuntu SMP Tue Jul 14 16:04:41 UTC 2009 i686 GNU/Linux

lspci:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

Thanks!

---

### Post by lithorus on 2009-07-21
Perhaps you could explain the bug futher?

---

### Post by brianafischer on 2009-07-21
> **lithorus said:**
> Perhaps you could explain the bug futher?

Whenever a network connection is not present, my hard drive trashes.  Everything seems to be working, but the hard drive light is almost solid indicating heavy disk IO.  Upon establishment of a network connection, the hard drive goes idle and the light is no longer on indicating no disk IO.

---

### Post by taavikko on 2009-07-21
Examine IO with "iotop" to have some data.

---

### Post by brianafischer on 2009-07-21
Well, I have tracked down the problem.  It appears to be MythTV with the bug.  This only occurs when I have no network connection and my laptop is on battery power.  Attached are the results of lshw and iotop without network connection.

I will submit this bug to the MythTV trac.

---

