---
title: "forcing resolution with nvidia drivers"
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hcaleman on 2010-04-25
Did a clean install of 8.04 then upgraded to 10.04 this morning (mainly due to lack of blank cds around).  System is P4 with 2gb ram, 100gb HDD using ext3 with LVM setup (one lvm partion each for swap, root and home).  Nvidia FX5200 graphics card connected to a plasma flat panel for now, moving upstairs to my lcd flatpanel once all is sorted (both are 1366x768 native).  

Lucid originally booted fine, but then I decided to screw around with it and managed to kill my ability to start X.  After some troubleshooting I got the nvidia-173 package working, but when rebooting I get unsupported resolutions on my display.  

I added a 1360x768 modeline and that got me into the OS finally, but everything is offset.  The nvidia setting utility is not able to recognize my display properly or allow me to choose a usable resolution.  It seems though that I can get what I need with a modeline inserted to my xorg.conf.  

I never had this issue with Hardy, but is there any way I can determine what to enter to my modeline so that I can get the proper resolution and centering of my display?

edit: I attached the PC to my Sharp LCD via DVI-D and everything was fine.  I guess my plasma display's vga connection was hindering the system from properly communicating with the panel.

---

