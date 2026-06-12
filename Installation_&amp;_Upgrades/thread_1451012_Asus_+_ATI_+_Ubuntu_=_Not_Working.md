---
title: "Asus + ATI + Ubuntu = Not Working"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by NetBoy_Pilot on 2010-04-09
I am having a very strange problem and wondering if anyone can give me some guidance.
 
Equipment:
Asus P4S8X-MX motherboard with 2.7GHz Celeron
VisionTek Xtasy 9100 128MB PCI video card (ATI Radeon 9100 vpu)
Ubuntu 9.1 32-bit
Xubuntu 9.1 32-bit
 
I have successfully installed Ubuntu on the Asus and its been running great, but the onboard video is slow. When I install the ATI video card, Ubuntu gets halted at the splash screen. The system is frozen and CTRL-ALT-F1 won't bring up a login prompt.
If I press C-A-F1 immediately after boot, sometimes I can get to a login prompt.
If I wait a longer period of time before pressing C-A-F1, the splash screen remains but gets garbage on it (like its writing to the wrong area of video card memory).
If I wait too long, nothing happens when I press C-A-F1. 
 
Alternatives I have tried:
1) Asus (w/ onboard video) + Ubuntu 9.1 -> SUCCESS
2) Asus (w/ onboard video) + Ubuntu 9.1 Live-CD -> SUCCESS
3) Asus + ATI + Ubuntu 9.1 -> fails at splash screen
4) Asus + ATI + Ubuntu 9.1 Live-CD -> fails at splash screen
5) Asus + ATI + Xubuntu 9.1 Live-CD -> SUCCESS
6) Different MB + ATI + Ubuntu 9.1 Live-CD -> SUCCESS
7) Asus + ATI + WinXP ->SUCCESS
 
Questions:
1) Since Xubuntu works, should I install that then install gnome after it? Or will the same issue appear when booting gnome?
2) Is there a better way to go from Xubuntu to Ubuntu?
3) Is there a good way to troubleshoot the boot process to find out what is actually failing?
4) Is there any command switches that may alleviate this issue?
 
Thanks for any help with this issue.
 
-Net-

---

