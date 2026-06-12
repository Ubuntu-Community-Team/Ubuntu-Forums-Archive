---
title: "Fixes for problems encountered with upgrade to Edgy"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by uranus65 on 2006-10-27
Here's a list of the fixes/workarounds that I have come across to fix the problems that I encountered with my upgrade to Edgy.  After spending the entire day messing with this, I can now open a Sam Adams Octoberfest and get to work/play.

1st problem:  No more Xserver

I have Radeon Xpress 200.

Did:
sudo aptitude install xserver-xorg-driver-radeon

(thanks) ner0tic.

then:
sudo dpkg-reconfigure xserver-xorg

2nd problem:  No splash screens

Did:
sudo gedit /boot/grub/menu.lst

added "# defoptions=quiet splash vga=791 "

(thanks) ZagiFlyer, mykemlez.

3rd Problem: No more Wacom Graphire tablet.

This was killing me as it was so small (PS/2 mouse worked fine) and so hard
to fix.

After looking at syslog, I turned off APIC in the BIOS. 

now everything works.

I hope this saves some time for some people.

---

