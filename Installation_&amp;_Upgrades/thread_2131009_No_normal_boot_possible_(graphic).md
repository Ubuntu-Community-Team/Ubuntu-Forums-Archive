---
title: "No normal boot possible (graphic)"
date: 2013-03-31
forum: Installation &amp; Upgrades
---

### Post by anonymus302 on 2013-03-31
Hi guys,
i have a problem. Installed Xubuntu 12.04 to my parents desktop. Worked fine. 
Restarted when it was finished.
Choose right kernel:
Black screen (ca. 15 s). Then nothing.
Reboot
Choosing kernel with recovery console, there i started the normal way.
Works fine. Here i am.
Tried to install the nvidia drivers (Gforce 4000).
Now i could boot directly to the kernel.
But i only had 640x480 and 320x240 as options for the resolution.
Here i am back with noveau drivers and dont know what to do. 
sudo lshw -C display
```

  *-display UNGEFORDERT   
       Beschreibung: VGA compatible controller
       Produkt: NV18 [GeForce4 MX 4000]
       Hersteller: NVIDIA Corporation
       Physische ID: 0
       Bus-Informationen: pci@0000:01:00.0
       Version: c1
       Breite: 32 bits
       Takt: 66MHz
       Fähigkeiten: pm agp agp-3.0 vga_controller bus_master cap_list
       Konfiguration: latency=32 maxlatency=1 mingnt=5
       Ressourcen: memory:e0000000-e0ffffff memory:d8000000-dfffffff memory:e1000000-e101ffff

```

lspci -nn | grep -i vga
```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV18 [GeForce4 MX 4000] [10de:0185] (rev c1)

```

cat /etc/X11/xorg.conf
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
 DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


```

Attachement:[ATTACH]240779[/ATTACH] Xorg.0.log.old

Anyone got a good idea?
Thanks 
Ano

---

### Post by dino99 on 2013-03-31
on top of this forum, you can find a sticky thread about that issue; so you might read it i think :guitar:

---

### Post by bogan on 2013-04-01
Hi!, **Anonymus30**2,

The GeForce4 MX 4000 requires the nvidia driver version 100.14.11 dated back to 20007, and long since outdated. It certainly will not run with the Xserver of 12.10, & I doubt it will support the one of 12.04.

**Edit:** I see that v96.43.23 was updated by nvidia, as recently as 14:09:2012; so that is more likely to serve your purpose.

v100.14.11 is only available from Nvidia.com downloads, if you want to try that route. But I think you are probably stuck with the default Nouveau driver, unless the nvidia-96 ubuntu packaged driver is available to you. Check in Synaptic Package manager.

You could try installing the gnome-session-fallback and loging in to Gnome Classic or Gnome Classic (No Effects) which will give you UNITY 2D.

For full instructions to install the nvidia,com driver see the Blank Screen Sticky in this Forum.
[http://ubuntuforums.org/showthread.php?t=1743535&page=6](http://ubuntuforums.org/showthread.php?t=1743535&page=6) - Post #1126

Do not hesitate to ask if you need more detailed instructions.

Be sure to remove --purge any driver you have installed, before installing another; and check the new one is not blacklisted in /etc/modprobe.d.

Chao!, **bogan.**

---

### Post by gordintoronto on 2013-04-01
My rule of thumb is that PC hardware is good for seven years. If you can get a 9-year-old device working at all, it's a bonus.

---

### Post by helmingstay on 2013-06-11
> **anonymus302 said:**
> Hi guys,
i have a problem. Installed Xubuntu 12.04 to my parents desktop. Worked fine. 
Restarted when it was finished.
Choose right kernel:
Black screen (ca. 15 s). Then nothing.
Reboot
Choosing kernel with recovery console, there i started the normal way.
Works fine. Here i am.
Tried to install the nvidia drivers (Gforce 4000).
Now i could boot directly to the kernel.


I have an nforce2 box that I've been trying to configure as a headless fileserver box, and I ran into the same issues. This is a server, so I need it to reboot without user intervention.

The key that I found to automatically boot without the black screen is add "text nomodeset" to grub.  The nomodeset prevents graphics drivers from being loaded at boot time.


sudo edit  /etc/default/grub:
GRUB_CMDLINE_LINUX_DEFAULT="text nomodeset"
sudo update-grub

---

