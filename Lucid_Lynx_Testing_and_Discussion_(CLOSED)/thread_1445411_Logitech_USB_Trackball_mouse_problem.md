---
title: "Logitech USB Trackball mouse problem"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by drucer on 2010-04-02
Ok, so device handling changed again and this time HAL was ditched with this latest 10.04 release and now devices are configured with something called udev.

I've spent the entire day searching for information on how to get my Logitech USB Trackball mouse to work, but no luck.

I want to enable horizontal and vertical scrolling when I press small left button and move the ball. This was easy to implement with HAL on 9.10 and some other way in previous releases, but 10.04 is a whole new ballgame and I don't know how to make it work.

I've read this entire thread describing similar problem to mine, but could not get it working with these hints:

[http://swiss.ubuntuforums.org/showthread.php?t=1434364](http://swiss.ubuntuforums.org/showthread.php?t=1434364)

I've also read the updated community wiki page regarding Ubuntu and Logitech Trackball mouses, but even though there is a new entry for 10.04 the configuration steps did not work for me.

[https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)

[https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)

---

### Post by ash86 on 2010-04-10
The udev rules were working perfectly for me until I updated to beta2 this morning. Now it seems like they aren't being loaded at all. Might be a bug in udev, but I want to look at my config bit more first.

To bring back scrolling for now, install the 'gpointing-device-settings' package, and use System > Preferences > Pointing Devices to set it up. The small button on the left is button 8 and middle click is emulated with buttons 1&2.

---

