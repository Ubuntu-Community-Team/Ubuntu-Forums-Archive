---
title: "Taking OS image after installing"
date: 2023-10-05
forum: Installation &amp; Upgrades
---

### Post by kishore3 on 2023-10-05
After installing Ubuntu on a laptop or desktop is there a robust solution available to take an OS image of the same and deploy the same over a pxe server?

---

### Post by sudodus on 2023-10-05
What do you mean by robust solution? What do you want?

[HR][/HR]
In principle, if you have an installed system without proprietary drivers, it is likely to be portable between computers of the same architecture (typically between PC computers: desktops, laptops).

If you prepare it for [OEM](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview), it will be well suited as a master version for an image that can be cloned to other computers.

---

### Post by TheFu on 2023-10-05
[https://discourse.ubuntu.com/t/ubuntu-22-04-pxe-uefi-netboot-desktop-installation/27841](https://discourse.ubuntu.com/t/ubuntu-22-04-pxe-uefi-netboot-desktop-installation/27841) 
and
[https://www.youtube.com/watch?v=E_OlsA1hF4k](https://www.youtube.com/watch?v=E_OlsA1hF4k) 
is all I've seen.

---

### Post by tea for one on 2023-10-05
Not sure if this is exactly what you need but perhaps the info is useful.
> Multicast is supported in Clonezilla SE, which is suitable for massive clone. You can also remotely use it to save or restore a bunch of computers if PXE and Wake-on-LAN are supported in your clients. 
The text above found here [https://clonezilla.org/](https://clonezilla.org/)

---

### Post by MAFoElffen on 2023-10-06
PXE deployment just needs an ISO file of the source system.

These are the possibles that I know of, that are helpers above having to completely build your own ISO:
[Remastersys]("https://github.com/nerun/remastersys")
[Cubic]("https://github.com/PJ-Singh-001/Cubic")
[SystemBack 2]("https://systemback.alien-os.de/")
[penguins-eggs]("https://github.com/pieroproietti/penguins-eggs")
[linux-live]("https://github.com/Tomas-M/linux-live")

Many of these are forks of the originals. Many of the past/previous ones died off just before Ubuntu 18.04 when systemd, qt4, and Python3 came in. All these are active, though SystemBack's last update was a year ago. That and there was strange quark when I helped someone with that about a year ago... Where it was only working to install 14 machines, then would quit working... So I don't know if I would fully recommend that one. Though he was creating LiveUSB's.

---

### Post by kishore3 on 2023-10-08
Thank you all, let me check

---

