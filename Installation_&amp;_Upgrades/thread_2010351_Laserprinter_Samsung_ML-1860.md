---
title: "Laserprinter Samsung ML-1860"
date: 2012-06-25
forum: Installation &amp; Upgrades
---

### Post by matza55 on 2012-06-25
Then I made a new fresh install of 12.04 today, problems with my printer occure. The printer writes a testpage, it says: Internal error - please use proper driver.
It has usb-connection.
I have installed and uninstalled. Nothing works.

Now it works! ```
sudo apt-get install samsungmfp-configurator-qt4
``` did the thing!

---

### Post by Groszman on 2012-10-24
When I want to get the package ist say:

"samsungmfp-configurator-qt4 is not available, but ist referenced by another package. That means, the package is missing or replaced or only available from another source wird aber von einem anderen Paket."

When I still used the 10.04 karmic distribution i could fix the problem with the unified linux drive. Unfortunately I don't find the drive on the net anymore.

---

### Post by mastablasta on 2012-10-24
have you tried using this: [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)

---

### Post by matza55 on 2012-10-24
> **Groszman said:**
> When I want to get the package ist say:

"samsungmfp-configurator-qt4 is not available, but ist referenced by another package. That means, the package is missing or replaced or only available from another source wird aber von einem anderen Paket."

When I still used the 10.04 karmic distribution i could fix the problem with the unified linux drive. Unfortunately I don't find the drive on the net anymore.

Open "Software Sources" through Unity
    Selected the 'Other Software' tab, clicked 'Add...' then pasted in deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra
    Hit ctrl + alt + t for terminal then ran sudo wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | sudo apt-key add - (it asked me for my password for sudo, of course)
    Ran sudo apt-get update to load the new source into the computer
    Opened the Software Centre from unity, searched for samsung config and installed Samsung Unified Driver Configurator (QT4 interface), along with the driver.
    Searched for Samsung in unity and ran the configurator. I hit refresh, then followed the steps to add the printer.

Although the configurator application thinks that the printer is a 'Samsung ML-1860 series', it appears to work perfectly.

---

### Post by NMeyne on 2012-11-25
Great.  Seems to work fine for me.  Thanks!

---

