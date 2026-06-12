---
title: "Setting screen resolution in preseed file."
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by Lluke77 on 2008-10-31
Hello,

I have made a preseed file for a kickstart installation of Ubuntu 8.04. The problem is that I cannot set the screenresolution in the preseed file. I know it's possible but i'm doing something wrong.

Let's see what I have;

> xserver-xorg xserver-xorg/config/monitor/selection-method \
       select medium
xserver-xorg xserver-xorg/config/monitor/mode-list select 1280x1024 @ 85 Hz

These are the settings that I want to use. But .. after installation the screen resolution is the max capable of the monitor, something like 1720x1354 don't know exactly. 

Anyone who knows how to solve problem? Thanks a lot.

---

