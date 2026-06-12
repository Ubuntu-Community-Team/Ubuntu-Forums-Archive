---
title: "Asus Sabertooth 990FX Gen3 - Network and USB ports not recognized"
date: 2014-03-15
forum: Installation &amp; Upgrades
---

### Post by Warped Trekker on 2014-03-15
When I install Ubuntu 13.10, the network and most USB ports don't work. Only the two USB that the keyboard and mouse are plugged in. If I unplug the mouse to put in a thumb drive to load drivers, Ubuntu just locks up. So can't load any network or USB hub drivers. Anyone have any fixes for this 990FX board?

---

### Post by Warped Trekker on 2014-03-18
Any thoughts?

---

### Post by varunendra on 2014-03-19
Have you checked the BIOS to make sure everything is enabled? Things to check -

- Make sure Network adapter and USB (all ports) are enabled.
- If there is a USB 'Legacy' mode, enable it too, it may be turned off by default.
- If there is a feature called "IOMMU", enable it too (or try disabling if is already enabled).

For letting us see what your system 'sees' about these, please open a terminal (Ctrl-Alt-T) and post back the outputs of the following commands -
```
lspci -nnk | egrep -iA2 'net|usb'
lsusb
```
..preferably, with some USB devices plugged in that you want to work with.

Along with the outputs, please also mention how many and which USB devices were plugged while you ran the commands, so that we can match the description against the output.

---

