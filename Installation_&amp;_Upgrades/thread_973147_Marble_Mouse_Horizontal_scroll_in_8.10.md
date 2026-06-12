---
title: "Marble Mouse Horizontal scroll in 8.10"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by dld on 2008-11-06
There was a nice thread in Intrepid Testing & ... concerned with using the Marble Mouse to scroll.  I did the *.fdi file bit, and do have scrolling --
vertically.  One article mentioned that horizontal scrolling was not working, and that is my situation also.  Has anyone found a fix that give both horizontal and vertical scrolling??

---

### Post by dld on 2008-11-20
SOLVED!  This is what I have as  scroll.fdi


<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">

<match key="info.product" string="Logitech USB Trackball">
 <merge key="input.x11_options.ButtonMapping" type="string">1 8 3 2 9</merge>
 <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelButton" type="string">9</merge>
 <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
 <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
</match>

</deviceinfo>

Adding the XAxisMapping and YAx... lines made the difference.  I don't
know why, or that the YAxis... line is necessary.

---

### Post by Galeo Deus on 2008-11-29
For me, adding/subtracting/modifying any .fdi file in the hal/fdi/policy folder does nothing.  I cannot get any kind of scrolling to work, let alone horizontal scroll.  Putting anything in any .fdi file does nothing.  I'm obviously doing something wrong.

What I'm trying to do (and have no idea how to do) is to get the left little button as middle click (to open new tab in firefox) as well as scroll when click-hold, then the right little button as "back".

---

### Post by fhansson on 2008-12-21
> **Galeo Deus said:**
> For me, adding/subtracting/modifying any .fdi file in the hal/fdi/policy folder does nothing.  I cannot get any kind of scrolling to work, let alone horizontal scroll.  Putting anything in any .fdi file does nothing.  I'm obviously doing something wrong.

What I'm trying to do (and have no idea how to do) is to get the left little button as middle click (to open new tab in firefox) as well as scroll when click-hold, then the right little button as "back".

I have the same problem. Adding .fdi files does nothing to my system, have tried reboot the computer as well. I did exactly as the tutorial and called the file MarbleMouse.fdi. It says nothing about the filename so I suppose it does not matter. Anyone else having the same problem?

---

### Post by tad on 2009-03-29
Check your permissions. Make sure your fdi file is world-readable:

```
sudo chmod go+r MarbleMouse.fdi
```

---

