---
title: "Upgrade or install impossible"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by best_friend_fr on 2006-10-27
Hi

I tried to ugrade from 6.06 to 6.10, and the upgrade worked fine. I rebooted, fine. But I couldn't shutdown anymore. When gdm quit, the computer freeze with a green screen.

The problem occurs when :
- I leave gdm (even if I hadn't started gnome yet)
- I try to switch to a text mode screen (ctrl+alt+1).

I tries to change my video driver (from fglrx to ati or vesa), and with ati or vesa, gdm don't even work.

If I try dpkg-reconfigure xserver-xorg, it crashes when detecting the screen. 
dpkg-reconfigure xserver-xorg (manual screen configuration) + dpkg-reconfigure gdm doesn't have any effect.

When the computer is frozen, even alt+ctrl+syst+b doesn't work.

I thought it was an upgrade error, and I downloaded edgy CD.

When I try to boot on the CD, it crashes at the end of the ubuntu splash screen. 

Do you have any idea?

Thank you

P.S Sorry for my poor English.

Configuration :
FSC Amilo 1437G
Pentium Centrino 1.73
Disk SATA
Video Card ATI X700

---

