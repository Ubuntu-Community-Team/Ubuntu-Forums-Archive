---
title: "Problem with A7N266 &quot;drivers&quot; - Screen resolution issue - Lubuntu 14.04"
date: 2015-07-19
forum: Installation &amp; Upgrades
---

### Post by Fernando_Resqun on 2015-07-19
Dear All:

I 've just installed Lubuntu 14.04. I could perform an update with no
errors. 
I have a system with Asus A7N266 motherboard and Athlon XP 
processor. 

How do I know if the drivers for this motherboard are updated? 

In the case of the graphics adapter, I can't set screen resolution 
above 1024x768, and 4/3 aspect ratio. In windows I can set higher 
resolutions with 16/9. 

The rest of the hardware appears to be OK. I have INTERNET and 
sound. 

There is something like the  Device Manager of Windows, in Linux? 

As suggested by **Bucky Ball **I wrote this command in LXTerminal: 

[COLOR=#ff0000]**sudo lshw -C video **

[/COLOR]This was the answer:[COLOR=#ff0000]

PCI (sysfs)  


  *-display               
       descripción: VGA compatible controller
       producto: nForce 220/420 NV11 [GeForce2 MX]
       fabricante: NVIDIA Corporation
       id físico: 0
       información del bus: pci@0000:02:00.0
       versión: b1
       anchura: 32 bits
       reloj: 66MHz
       capacidades: pm agp agp-2.0 vga_controller bus_master cap_list rom
       configuración: driver=nouveau latency=32 maxlatency=1 mingnt=5
       recursos: irq:19 memoria:eb000000-ebffffff memoria:f0000000-f7ffffff memoria:efff0000-efffffff[/COLOR]


Maybe it can help.

Thank you.

Regards.

---

### Post by Bucky Ball on 2015-07-20
Well, the open source driver is installed and being used (nouveau). If it is working okay, great. That will do if you're happy.

As for the resolution, where are you looking to change it? I'm not currently using Lubuntu, but something like Settings>Display should get you there. You are not able to choose a different resolution for your monitor there?

I use arandr myself. That is sometimes more descriptive and flexible. If the above doesn't work, install arandr using Synaptics or a terminal, launch it and see if that offers the correct resolution for you to select. Good luck. :)

PS: After doing an update, can you check 'Additional Drivers'. Is there anything in there that relates to your graphics card?

---

### Post by Vladlenin5000 on 2015-07-21
```
        producto: nForce 220/420 NV11 [GeForce2 MX]
```

This is one of the few (in)famous integrated chips from Nvidia eons ago... If I remember correctly it worked with nvidia proprietary driver v. 173 (?) which is now legacy??

---

