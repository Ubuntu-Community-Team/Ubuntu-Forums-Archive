---
title: "The resolution is stuck at 640x480.Help needed"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by baradwaj on 2006-08-17
Hi guys,I have a problem with an installation of ubuntu on my friend
s computer.His resolution is stuck at 640x480x24bit.When I change the resolution by reconfiguring xserver-xorg using dpkg-reconfigure,I endup in 640x480 resolution unless I choose 8 bit color depth.I am able to run at 1024x768x8bit but not any higher color depth.However,it is to be noted that windows works fine at 1024x768x32bit mode.Can some one help me fix this problem?I have attached the xorg.conf and Xserver log file when i try to run the system at 1024x768x16 bit mode.All I could understand was that the system (as autodetected by ubuntu) tries to run the system at the highest possible resolution it can run at the given color depth among the enabled ones provided I give a color depth below 24.It is not able to run the system at 24 bit mode in any of the resolutions.It can run at all resolutions(1024x768,800x600,640x480) at anything 8 bit mode but it is able to run only 640x480 at above 8 bit.The problem seems to be with the video bios memory allocated but i am unsure of it(This i conclude from the fact that when I tried another monitor,the dpkg-reconfigure showed highresolutions like 1280x1024 however started X at 640x480 mode.)I would be really happy if this gets solved.


Thanks all

---

### Post by baradwaj on 2006-08-18
Someone please help!!!

---

