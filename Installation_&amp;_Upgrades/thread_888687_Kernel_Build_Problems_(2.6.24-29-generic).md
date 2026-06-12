---
title: "Kernel Build Problems (2.6.24-29-generic)"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by tdz on 2008-08-13
Please excuse me if this question has been answered before.  (If it has, please let me know so I can chase down the old posts.)  I am new to Ubuntu and to Linux, so I suspect that someone has already fought and won this battle before.

I am attempting to build a kernel to support a driver that I am developing here at work. The kernel is based on 2.6.24-19-generic.

I've run into two problems.

First I configured using the default (make defconfig) configuration. That kernel booted, but did not have a network connection and had several undefined symbols when I built and loaded my driver module. (We have a wired LAN which the configuration prior to my config is able to get to with no problem). I suspect that I left something out of the .config which caused the network problem, though I don't know what. I tried forcing the inclusion of the files which define my undefined functions by manually editing the .config. When I ran make to build the kernel, somehow my edits were changed to not include these files and the undefined symbols problem was still there.

Next I tried a build using make xconfig. Although I tried to exclude drivers for devices that I know I don't have and things that I know would conflict with other items on my system, it looks like this pulled in almost everything. (Something similar happened with make menuconfig.) This kernel fails to boot, but instead, after a long wait (several minutes) goes to BusyBox.

"BusyBox v1.1.3 (Debian 1:1.1.3-5Ubuntu12) Built-in shell (ash)"

I suspect that both of these problems are config errors of some sort on my part, though I don't know what I did wrong. These are my first two attempts at kernel builds, so I don't seem to have the formula down yet.

What should I try next? I didn't see anything in the HOWTO or README documentation which seemed applicable, although I may have missed something important there.

Thanks in advance.

---

