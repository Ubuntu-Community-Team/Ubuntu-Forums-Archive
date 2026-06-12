---
title: "ATI Catalyst 10.3"
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by wbar2 on 2010-04-25
I'm running Lucid 64-bit, and I have an ATI Radeon HD 3200. I have installed the proprietary drivers using System - Administration - Hardware Drivers.

How do I know what version of the drivers is installed?

I was thinking of installing (probably newer) drivers directly from ATI:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

I just wanted to see if some things with compiz, etc. do a little better with it. If I did so, is there an "escape hatch" if things go wrong and I lose video?

---

### Post by andrewthomas on 2010-04-25
> **wbar2 said:**
> 

I was thinking of installing ** (probably newer) ** drivers directly from ATI:



Probably not. Most likely the same.

---

### Post by moviemaniac on 2010-04-25
> **wbar2 said:**
> 
I was thinking of installing (probably newer) drivers directly from ATI:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

The fglrx drivers for lucid are prerelease drivers from ATI meaning they are newer (in terms of hardware support) than the drivers ATI/AMD is offering on their website. You can't even install the "official" ATI drivers from their site as they don't support Xserver 1.7 / Xorg 7.5
If you want to user newer drivers you'll have to wait for the 10.4 or 10.5 package, depending on which one will support the newer Xserver /Xorg in lucid.

In short: Stick with what's installed for now, you don't have any other option (unless you use the open source radeon or radeonhd drivers)

---

### Post by wbar2 on 2010-04-27
> **moviemaniac said:**
> The fglrx drivers for lucid are prerelease drivers from ATI meaning they are newer (in terms of hardware support) than the drivers ATI/AMD is offering on their website. You can't even install the "official" ATI drivers from their site as they don't support Xserver 1.7 / Xorg 7.5
If you want to user newer drivers you'll have to wait for the 10.4 or 10.5 package, depending on which one will support the newer Xserver /Xorg in lucid.

In short: Stick with what's installed for now, you don't have any other option (unless you use the open source radeon or radeonhd drivers)

Okay, thanks for your explanation. That makes sense.

---

