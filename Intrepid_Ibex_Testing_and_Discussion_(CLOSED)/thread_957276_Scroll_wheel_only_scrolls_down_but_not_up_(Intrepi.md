---
title: "Scroll wheel only scrolls down but not up (Intrepid Ibex in VMWare)"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Stokes on 2008-10-24
Hi,

I have a very strange problem here. My scroll wheel works only in one direction. I can scroll down but not scroll up. It seems that if I use the wheel upwards the computer thinks that I scrolled down very fast.

System: Intrepid Ibex 64-bit in a VMWare server box running on WinXP.

I googled around for this issue but I only get hits on how to get the scroll wheel working if it is not working at all.

xev shows that the scroll wheel sends event "Button 5" on both directions.

Here is the section in xorg.conf

```

Section "InputDevice"
     Identifier "VMware Mouse"
     Driver "vmmouse"
     Option "Device" "/dev/input/mice"
     Option "Protocol" "ImPS/2"
     Option "ZAxisMapping" "4 5"
EndSection

```

Any ideas?
Thanks and regards,
Stokes

---

