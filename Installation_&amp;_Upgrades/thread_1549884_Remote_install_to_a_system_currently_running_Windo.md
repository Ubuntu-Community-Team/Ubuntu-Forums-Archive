---
title: "Remote install to a system currently running Windows... anyone fancy a challenge?"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by danbishop on 2010-08-10
Does anyone know of any way (preferably fully documented/tutorialed, but even theoretical would be great) to remotely install Ubuntu to a machine currently running Windows...

We have 8 machines powering a digital signage system. The machines are not physically accessible (without extreme difficulty) and are currently running windows XP with a VNC server for control.

I want them to run Ubuntu instead. Is there any way anyone can think of that I can do this? My only thought so far is WUBI...but once it boots into Ubuntu ssh isn't installed by default and vnc isn't enabled by default so I wouldn't be able to control it.

Also I'd really like to completely wipe out Windows and use only Ubuntu.

I know this is a long shot... but anyone? :D

---

### Post by stlsaint on 2010-08-10
For starters you are wanting to do a netinstall. You will need a server hosting the boot image of the OS. Then setup DHCP boot or pxe boot from the client to boot from the server. 
This should at least get your wheels moving.
[https://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](https://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install)

---

