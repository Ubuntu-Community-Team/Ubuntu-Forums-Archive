---
title: "New Video Card"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by goldenatom on 2006-11-19
Whats the procedure for installing a new video card? I've got a ti4200 in my machine right now and I want to move up to something like an nvidia 7900 GS. I have the beta driver installed currently. Can I just pull the card and swap in the new one? Something tells me that's going to kill X. Little help?

---

### Post by dbott67 on 2006-11-19
Depending on the driver it uses, it can kill X.
[B][U]
The Easy Way:[/U][/B]

```
sudo dpkg-reconfigure xserver-xorg
``` and follow the reconfiguration of X windows.

**_The Harder Way_**

[I]Note: the problem with doing it this way is that if the settings and capabilities of the card are radically different, it can get messy.  The easiest way is **sudo dpkg-reconfigure xserver-xorg**.
[/I]
If you have a little bit of experience editing your xorg.conf file, you could do it before you start.  Suppose your wanted to go from an nVidia to ATI generic to fglrx.  Before you replace the card, you could do the following:

1. Backup your existing xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.ti4200
```

2. Edit your xorg.conf file to reflect the new generic driver (in red)(for ATI cards it's 'ati'; for nVidia cards it's 'nv').  You would also need to modify the file to reflect the **identifier** & **screen device** in the appropriate sections to reflect your new hardware.
```

Section "Device"
        **[COLOR="Blue"]Identifier      "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"[/COLOR]**
        **[COLOR="Red"]Driver          "nv"[/COLOR]**
        BusID           "PCI:1:0:0"
EndSection

```
Change the 'nv' driver to 'ati':
```
Section "Device"
        **[COLOR="Blue"]Identifier      "ATI Radeon AIW Pro"[/COLOR]**
        **[COLOR="Red"]Driver          "ati"[/COLOR]**
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
EndSection

```
Shutdown the computer, replace the card and then re-boot.  Next, download the fglrx drivers from the repositories and modify your xorg.conf to reflect the ATI 3D drivers:
```
Section "Device"
        **[COLOR="Blue"]Identifier      "ATI Radeon AIW Pro"[/COLOR]**
        **[COLOR="Red"]Driver          "fglrx"[/COLOR]**
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
EndSection

```

Reboot and your should be running the new fglrx drivers.

Hope this helps.

-Dave

---

### Post by goldenatom on 2006-11-19
Thanks a bunch.

---

### Post by dbott67 on 2006-11-19
No problem.  Let us know how you make out.

-Dave

---

