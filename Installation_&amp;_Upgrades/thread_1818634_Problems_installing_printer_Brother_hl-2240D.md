---
title: "Problems installing printer Brother hl-2240D"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by steseum on 2011-08-05
Hello,

I have followed [http://ubuntuforums.org/showthread.php?t=1627516](http://ubuntuforums.org/showthread.php?t=1627516) and tried to install the Brother printer driver for HL-2240D. It seems that driver has been installed and printer be recognized. However, I can't make it come up in the "system" "add printer" command.

Any tip? Stefan

Bus 002 Device 004: ID 04f9:0040 Brother Industries, Ltd 
Bus 002 Device 003: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0930:0214 Toshiba Corp. 
Bus 001 Device 004: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by tylerwagler on 2012-02-22
I have this printer plugged into an 11.10 server box, and it appears to have installed correctly through the cups web interface, and my desktop machine has added it, however nothing prints.  all the jobs say completed, but nothing comes out of the printer :(

---

### Post by tylerwagler on 2012-02-23
sudo apt-get -f install fixed my issue

---

