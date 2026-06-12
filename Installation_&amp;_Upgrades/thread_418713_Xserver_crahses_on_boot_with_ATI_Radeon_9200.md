---
title: "Xserver crahses on boot with ATI Radeon 9200"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by foldor on 2007-04-22
I have just upgraded my old install of Edgy to Feisty and now when I boot into Ubuntu it will go to a terminal prompt instead of the regular login screen and will say that the Xserver has crashed. I use an ATI Radeon 9200 and I have tried reinstalling the fglrx drivers, only to find they are still correctly installed from the last install of Edgy. As a side note my laptop uses the same drivers on its ATI Mobility X1400, and it had no trouble booting Xserver but Feisty seems to have changed the driver to the one thats in the restricted repositories.

EDIT: The report from the crash says: 

(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) No devices detected.

Fatal server error:
no screens found

(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |  |-->Monitor "aticonfig-Monitor[0]"
(**) |-->Device "ati-config-Device[0]"
Then some things about mouse and keyboard
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
                 Entry deleted from font path.
Some stuff about fonts...
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "AIGLX" "off"
(**) Extension "Composite" is disabled


Any help is appreciated because I am lost right about now.

---

### Post by AzraelUK on 2007-05-22
Exactly the error I get. What you'll need to do to fix it is run `sudo dpkg-reconfigure xserver-xorg` from the console, and choose the radeon driver instead of whatever else. Unfortunately, you won't get any hardware acceleration under the radeon driver :(.

I've filied a bug at [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/116268]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/116268").

---

