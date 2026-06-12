---
title: "Keyboard/mouse stopped working after upgrading to 10.04"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by g003y on 2010-05-07
I use the Logitech diNovo Edge keyboard and after the upgrade it stopped working. I tried to boot into the recovery mode and then at least the keyboard part started working in the console. I tried to repair and update the installation. I also tried to reconfigure the keyboard settings and I changed to dinovo edge. After that not even the recover console worked anymore.
Then i tried to boot using the CD but the keyboard doesn't work on the CD either. This really sucks!

---

### Post by efflandt on 2010-05-07
Assuming you are trying to use the USB dongle that came with it and have a wired keyboard & mouse to use temporarily, edit /lib/udev/rules.d/70-hid2hci.rules. I found that the easiest thing to do was to simply comment out this section (put # at the beginning of the lines):

```
# Logitech devices
#KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
#  RUN+="hid2hci --method=logitech-hid --devpath=%p"
```Or as an alternative change "hiddev*" to "hidraw*" instead of commenting out those lines.

Then plug your Logitech dongle in (or unplug it and replug it), and it should work.  Either worked for my diNovo Edge.

Note that to edit system files use **gksu gedit** or **sudo nano**.

---

