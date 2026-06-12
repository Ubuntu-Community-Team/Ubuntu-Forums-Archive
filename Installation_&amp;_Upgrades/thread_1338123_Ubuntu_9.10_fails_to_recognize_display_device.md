---
title: "Ubuntu 9.10 fails to recognize display device"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by sujan01 on 2009-11-26
Losing faith in UBUNTU!!! I just started learning Linux by installing dual boot Ubuntu 9.10 Desktop with Windows 7 on a brand new HP Pavilion Slimline 64 bit processor with 4GB memory and 640 GB hard drive.  However, I retained my old and faithful 18" Sony 420GS monitor.  I almost lost faith in Ubuntu as my first attempt to install Ubuntu 9.04 Desktop from a CD miserably failed since the boot loader set the screen resolution erratically at a very high resolution beyond the capacity of my monitor.  All I could see was a vertical line at the leftmost edge of the monitor screen.  So I downloaded and installed Ubuntu 9.10 Desktop.  The result was a little better that I could see the initial screen at 600x400 resolution and I could change it to a maximum of 800x600 resolution.  The terminal device was being shown as unknown device.  Even this pleasant experience was short lived.  During the next boot, all I could see was the vertical line at the left edge of the display screen.  I repeated the boot sequence a few times with erratic results during next couple of days and during one of the attempts, I found a choice to use the failsafe mode.  This time Ubuntu identified my display unit as a 18" Sony monitor.  Then I could set the resolution to 1024x768 or even higher.  I had my confidence back and used Linux as my main system for about a week.  Today, I rebooted Ubuntu and again it did not recognize my display device.  I could not set the resolution higher than 800x600.  Now, out of desperation, I tried a new trick.  I powered off the display unit and powered it back on.  Ubuntu got shaken up and correctly identified my display unit as a 18" Sony monitor.  It is a long story, but what I am trying to point out is that Ubuntu appears to be very unstable to me.  It must be having the right display driver but it is not getting activated during the boot sequence.  I have seen many postings for similar problem of not being able to display more than 800x600 resolution with Ubuntu 9.10.  I hope that my observations will lead to proper diagnosis and resolution of this nagging problem that is causing frustration to so many users. For more details, see my system configurations below:

lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
02:00.0 Communication controller: Agere Systems Device 0630 (rev 01)

---

