---
title: "Ubuntu dont like my PC"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by Mozz1965 on 2008-02-23
Computer:                                           Self Built
      Operating System                                  Microsoft Windows XP Professional
      OS Service Pack                                   Service Pack 2
      DirectX                                           4.09.00.0904 (DirectX 9.0c)
         

    Motherboard:
      CPU Type                                          AMD AM2 Athlon64 6000 Dual Core 3.0GHz
      Motherboard Name                                  Abit KN9 Ultra(NF-MCP55 series), 3000 MHz
      Motherboard Chipset                               NVidia nForce 570 Ultra
      System Memory                                     2048 MB
      BIOS Type                                         Award (08/21/06)

    Display:
      Video Adapter                                     NVIDIA GeForce 8800 GTS  (320 MB)
      Monitor                                           Samsung SyncMaster 190T/191T/195T/MagicSyncMaster CX195T (Digital)  [19" LCD]  (HJFW702015)

    Multimedia:
      Audio Adapter                                     Realtek HD Audio output

[SIZE="3"]:confused:[/SIZE]Hi, I've tried both the 64bit & 32bit versions of the live CD in my PC, but after the box comes up at first that says "loading the Kernel" wich I _CAN_ see, the screen just goes black and I can't realy tell wether anything else is happening. Becuase I can't see anything! My graphix card does have the latest driver from nvidia.
So if anyone else has come across this and managed to solve it, please help.
Thanx y'all.:KS

---

### Post by solidsteel144 on 2008-02-23
Try running the live cd under safe graphics mode.

---

### Post by zvacet on 2008-02-23
Try with safe grapfic mode.Second option is to download alternate CD.You have win drivers for your card and they don´t work in linux.

---

### Post by Mozz1965 on 2008-02-23
Thanx for the replys guys. JHow do i go into safe graphics mode. Also is there a driver for my card that will run both Ubuntu and XP.

---

### Post by dstew on 2008-02-23
> Also is there a driver for my card that will run both Ubuntu and XP.You might be confusing firmware, which is on the card itself, and the driver, which is part of the operating system. The linux driver will be different from the XP driver because the operating systems are different, and the same software will not work in different operating system environments. Hopefully, both the XP driver and the Ubuntu driver will work with the same firmware that is on your card. Usually that is the case. But that is really an issue to deal with once you have Ubuntu installed. Your video adapter should work fine in Ubuntu.

To get Ubuntu installed using the Live CD, you can try kernel parameters (press F6 at the first screen). Some to try are noapic nolapic acpi=off irqpoll. For the display, try vga=791 (that should give you a basic 1024x786 GUI during the installation) If none of these work, use the Alternate Install CD. It installs the same Ubuntu desktop system on your hard drive using a text-based installer that will be able to work with your system easily.

---

### Post by Officer Dibble on 2008-02-23
> **Mozz1965 said:**
> 
[SIZE="3"]:confused:[/SIZE]Hi, I've tried both the 64bit & 32bit versions of the live CD in my PC, but after the box comes up at first that says "loading the Kernel" wich I _CAN_ see, the screen just goes black and I can't realy tell wether anything else is happening. Becuase I can't see anything! My graphix card does have the latest driver from nvidia.
So if anyone else has come across this and managed to solve it, please help.
Thanx y'all.:KS

I've had this problem on two occasions. The first time I just reset the computer and let it boot into the installation again without a CD in the drive.

On another occasion it was just a matter of waiting for a short while and then pressing escape - try this option first.

Hope it works for you because once you are sorted out with Ubuntu it will become your main OS and XP/Vista, if you continue using them at all, will be for toying around with games and other none too essential matters. ;)

---

### Post by Bongo Fury on 2008-02-23
As Officer Dibble, mention hit (ESC)

I have a XFX GeForce 8600GT 256MB DDR3 card, in my system. After several attempts to install 7.10 g, my monitor went off-line every time, as a last ditch effort I went in to monkey mode started striking keys and when I hit the ESC key my monitor starting working. After the install this problem never happened again.

:lolflag:

---

### Post by ChronoSphere on 2008-02-26
I had a similar problem, which I solved by using a DVI adapter for the monitor.

---

