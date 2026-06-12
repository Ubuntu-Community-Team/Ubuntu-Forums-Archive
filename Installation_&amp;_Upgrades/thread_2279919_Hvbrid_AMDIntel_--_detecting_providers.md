---
title: "Hvbrid AMD/Intel -- detecting providers"
date: 2015-05-26
forum: Installation &amp; Upgrades
---

### Post by Ubugim on 2015-05-26
Hi,

I am having problems with fglrx drivers in ubuntu 14.04 (it says hardware unsupported although it is supported) and this worked well on ubuntu 12.04 on my laptop. I have tried everything and the only reason I may find is :

xrandr --listproviders
Providers: number : 1
Provider 0: id: 0x48 cap: 0x9, Source Output, Sink Offload crtcs: 4 outputs: 5 associated providers: 0 name:Intel

Only 1 provider is listed although 
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
[sudo] password for faisal: 
0: IGD:+:Pwr:0000:00:02.0
1: DIS: : DynOff:0000:01:00.0



lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7500M/7600M Series] (rev ff)

Why only one provider is listed and not two?

---

### Post by Ubugim on 2015-05-27
cat /sys/class/drm/card1/device/enable
0
cat /sys/class/drm/card0/device/enable
1
cat /sys/class/drm/card1/device/boot_vga
0
cat /sys/class/drm/card1/device/boot_vga
1

Are these parameters a problem? are there more parameters? How do I change these to become 1 ? a simple sudo editing returns Fsync failed

---

