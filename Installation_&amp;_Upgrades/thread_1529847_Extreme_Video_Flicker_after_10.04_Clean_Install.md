---
title: "Extreme Video Flicker after 10.04 Clean Install"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by UtopiaTheory on 2010-07-12
Okay...so my friend purchased an Asus CG5275 Desktop PC that came with Windows 7.  It has an Intel i5 with integrated Intel HD Graphics.  He wanted to install Ubuntu Lucid as a dual boot so he asked me to help him.  I noticed during the installation that the entire screen looked like it was vibrating.  I brushed it off as a pre-install graphics driver issue that would likely be solved after the installation had completed.  It was very difficult to read anything during the installation, but I got through it.  After the install, rebooted and the problem remained.  Ran updates...new kernel...reboot.  Problem remains.

It's constant...not random...it never stops happening.  Another weird symptom is that it is much less noticeable on the left side of the screen...whereas text is completely unreadable towards the middle and right of the screen.

I have read many other posts regarding the integrated Intel graphics screen flicker and this does not seem to be the same problem.  For one, it's constant rather than randomly occurring.  Also, I tried all of the solutions presented to those issues (I think) and none of them worked.

The problem does not occur at all in Windows, so it must be software related and not hardware related.  I got a migraine looking at his screen for only 20 minutes.  It's unbearable and I'll probably have to install Karmic or Jaunty if I can't get Lucid to work.

Any help would be much appreciated!

Intel i5 with integrated Intel HD Graphics
LG W40 Series LCD

---

### Post by waynefoutz on 2010-07-12
Right click on our desktop, click on "change desktop background" then in the visual effects tab turn them to off. See if that helps.

---

### Post by UtopiaTheory on 2010-07-14
> **waynefoutz said:**
> Right click on our desktop, click on "change desktop background" then in the visual effects tab turn them to off. See if that helps.

That was the first thing I tried.  It didn't change anything.  I'm on the computer in question right now (in Win7) so I'll boot into Ubuntu and post an lspci.

---

### Post by UtopiaTheory on 2010-07-14
Here's the lspci:

```

desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

```

---

### Post by UtopiaTheory on 2010-07-14
I should point out that I'm a proficient Ubuntu user.  I've tackled many complex issues before.  This one has me worked though.  I wouldn't be surprised if it turns out to be something ridiculous.  Would it be possible that the monitor itself isn't playing well with Ubuntu?  It works great under Win7.  It's an LG Flatron W2340VG.

---

### Post by UtopiaTheory on 2010-07-14
Argh.  I just removed the VGA cable and connected the monitor with an HDMI and it looks beautiful.  I guess I'll have to get another HDMI cable for my TV.  Even though this doesn't solve the issue with the VGA port, I'm going to mark this as solved...reluctantly.  I still would love to know what went wrong!

---

