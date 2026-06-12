---
title: "Forced to use flash drive as boot drive."
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by smurfgod on 2011-06-11
Hello all.
   Back in Febuary, my wife bought a Toshiba Satilite from Wal-Mart and a few days ago the hard drive got toasted. So now I'm using an 8gig usb drive as the boot drive. I also have 2 other flash drives for downloads and such but overall I am very pleased.

I'm running 11.04 32 bit and was wandering if 64 bit made a difference. I've got 4 gigs of ddr3 and was wandering if that really helps in these situations?? It's slow to boot, but once it's running, it's faster then Windows 7. Very nice.

Is there anything I should chage, use, you can suggest, since I'm running it off a flash drive??

I have 3 seperat drives, 2 x 16 gigs and an 8 gig, and was wandering which one would be best for booting off of? What do I look for??

Thanks for the info.



Here's what I got:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

---

### Post by mp035 on 2011-06-11
Nice work!  I am assuming you are using a 'Live CD' install copied to a USB flash drive, rather than a full install on a flash drive.  If you are using a full install, it is generally recommended to disable any swap partitions to prevent thrashing of the flash memory.

IMHO, you will not see any advantage switching to 64 bit.  Unlike WinXP, the latest linux kernels can access all of your 4GB ram even on a 32 bit system.

---

### Post by kerry_s on 2011-06-11
all usb's are different, so you would want to use the 1 with fastest read & write times.

---

### Post by smurfgod on 2011-06-12
> **mp035 said:**
> Nice work!  I am assuming you are using a 'Live CD' install copied to a USB flash drive, rather than a full install on a flash drive.  If you are using a full install, it is generally recommended to disable any swap partitions to prevent thrashing of the flash memory.

IMHO, you will not see any advantage switching to 64 bit.  Unlike WinXP, the latest linux kernels can access all of your 4GB ram even on a 32 bit system.

I used the "desktop-i386" and used unetbooting. Should I redo it with just the live version?? In disk utility, it tells me I have 4 gigs of swap. Any way to get that back??

> **kerry_s said:**
> all usb's are different, so you would want to use the 1 with fastest read & write times.

Is there a way to test em in Ubuntu?? I did it in Windows, but wasen't sure about Linux.


Edit: Heres my laptop. [http://us.toshiba.com/computers/laptops/satellite/L670/L675D-S7015/](http://us.toshiba.com/computers/laptops/satellite/L670/L675D-S7015/)

Also, what would be best for 1080p video playback?

Thanks

Edit 2:

I went into GParted, and turn swap off on the 4 gig swap partition. I've read I need to do something in fstab, but am unsure. Heres a screenshot of both.

[IMG]http://i.imgur.com/3lxZA.png[/IMG]

---

### Post by Hedgehog1 on 2011-06-12
There is a line in /etc/fstab that will need to be commented out to turn off the swap partition.

```
gksudo gedit /etc/fstab
```

And put a '#' character in front of the 'swap partition' line:

```
# swap was on /dev/sdc5 during installation
**[COLOR="Red"]#[/COLOR]**UUID=cb0c7226-150e-45ca-ba5c-2e161dc10f6a none   swap  sw   0       0

```

***The Hedge***

:KS

---

### Post by smurfgod on 2011-06-12
> **Hedgehog1 said:**
> There is a line in /etc/fstab that will need to be commented out to turn off the swap partition.

```
gksudo gedit /etc/fstab
```

And put a '#' character in front of the 'swap partition' line:

```
# swap was on /dev/sdc5 during installation
**[COLOR="Red"]#[/COLOR]**UUID=cb0c7226-150e-45ca-ba5c-2e161dc10f6a none   swap  sw   0       0

```

***The Hedge***

:KS

Got it. Thanks.


How can I mierge the 2 now???

---

