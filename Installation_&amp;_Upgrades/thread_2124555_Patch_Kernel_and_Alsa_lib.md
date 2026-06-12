---
title: "Patch Kernel and Alsa lib"
date: 2013-03-11
forum: Installation &amp; Upgrades
---

### Post by sparklyballs on 2013-03-11
hi. still inside my first few days of making the transition from mac osx/bootcamped win 7 in the hopes of running a nice xbmc system and a myth tv backend. 

i've kind of reached my first set of goals by getting some of the hardware working (namely, ethernet and wireless, need to look at ir6 remote next in hardware) on a dual booting mac mini late 2012 i7 quad core 2.3 mhz machine. 

reading through various xbmc forums in regard to the intel hd4000 graphics in this machine and hd-audio passthrough not working (which it does with windows7)  it would appear that i have to patch the kernel and alsa lib with 3 files for the kernel and one for alsa. 

i have absolutely no idea how to achieve this whatsoever, i'm running 12.10 with 3.5.0.17.28 kernel at the moment. 

here is output of lspci -nnk | grep -iA3 vga 

00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Apple Inc. Device [106b:0101]
    Kernel driver in use: i915
    Kernel modules: i915


and here is the relevant link with the patches [http://forum.xbmc.org/showthread.php?tid=128298&page=45](http://forum.xbmc.org/showthread.php?tid=128298&page=45) 

comment 446 on that page 

and i don't know if this will help but here is a bug report about this issue with the relevant patches also. 

[https://bugs.freedesktop.org/show_bug.cgi?id=49055](https://bugs.freedesktop.org/show_bug.cgi?id=49055)

is anybody able to guide me on how to patch a kernel and alsa lib please ? 

i've tried googling it but there seems to be many different conflicting search results and i don't have the filter of a small amount of knowledge to sort the wheat from the chaff.

---

