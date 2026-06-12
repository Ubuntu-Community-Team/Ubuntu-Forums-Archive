---
title: "TV-Out doesn't work after upgrade to 8.10"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by utkjamie on 2008-11-02
TV-out no longer works for me after upgrading to 8.10. Definitely frustrating considering that it took me weeks to get it working properly in the first place and less than an hour for the upgrade to undo it all. I really don't want to have to go back to using a WinXP dual-boot to use tv-out.

I'm using an ATI Radeon 9000 RV250 card and have been using a bash script with the following commands to "activate" TV-out:

```

xrandr --addmode S-video 800x600
xrandr --output LVDS --mode 800x600 
xrandr --output S-video --mode 800x600
xvattr -a XV_CRTC -v 1

```Xrandr now seems to lock up the OS and I am forced to kill the power to do a reboot.

---

### Post by utkjamie on 2008-11-05
Anyone else having problems with TV-Out/S-video after upgrading?

---

### Post by lungdoc on 2009-01-04
Hi. Absolutely new to linux and ubuntu, but enjoying it over windows so far - I used my acer travelmate 290Lci (intel 855gm) to play movies via an s-video out. That function seems to have fallen out after switching to ubuntu. The screen on my laptop shows a broken snowy image and locks up the system as well. I have to use ctrl-alt-del to get out.

Any thoughts on how to fix it?

---

