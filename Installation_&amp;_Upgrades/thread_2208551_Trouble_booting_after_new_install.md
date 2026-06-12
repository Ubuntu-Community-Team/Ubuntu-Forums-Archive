---
title: "Trouble booting after new install"
date: 2014-02-28
forum: Installation &amp; Upgrades
---

### Post by scalyed on 2014-02-28
Hello,

New to Linux here,

I originally downloaded a copy of Ubuntu 12.04 LTS and used the pendrive application to create a bootable USB.

Installed 12.04 without any trouble and when it asked to reboot the machine i pulled the USB drive and booted.

The system attempt to boot ubuntu but quickly flips back to a text UI repeating several lines about "First FIS Failed, gave up waiting for Root Device"  it would wait for a few minutes then repeat the process.  

I did a little reading and went into the bios and changed the device settings for the hard drives to ahci and this did not help either.

Downloaded the 13.10 and reinstalled to see if there was a difference if i had the ahci on before the install.  When i got to the screen in the install UI with the map and the time zones, a window popped up asking me about GBT Table.  There were 2 choices in this window, neither were clickable, the window was drag able so i moved it out of the way and carried on with the install.  As i got to the next screen set of options the GBT Table warning was gone.  Install finished and asked me to reboot.  Same issue as first insall.

I grabbed a copy of fedora dropped it on usb drive installed and same issue there as well.

I have reinstalled windows on my machine but i would really like to know what im doing wrong or if i try again what information i need to better help resolve this.

Im getting the impression its a setting on my motherboard or a hardware issue.

Thanks in advance,

Loren

---

### Post by sudodus on 2014-03-01
Welcome to the Ubuntu Forums :-)

I think you are right about a hardware issue. ***Please describe the computer***, and we have a chance to give relevant advice! At least the following

- Computer brand and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Have you ***tried Ubuntu*** booting from the pendrive, only running it but not installing? What do you see? [COLOR=#696969]I think Ubuntu is running, which is different compared to when installed.[/COLOR]

---

### Post by scalyed on 2014-03-01
Thanks in advance for the help!

I have not tried to boot the Ubuntu distribution from the usb drive, but i did have linux mint for an evening when i was looking around at distributions.  It was running by default on my USB drive when i booted the it and i played with it for an evening and everything was working well.

I have had the computer for a few years i built it from new egg:

Board - Asus F1A75-V Evo - [Link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131784")
Chip - AMD A8-3870K - [Link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819106001")
Memory - G.SKill 2x 4gb DDR3 1866 - [Link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231455")
Graphics - Gigabyte Radeon HD 6950 - [Link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814125385")
Network - Using on-board motherboard wired port

Thanks,

Loren

---

### Post by sudodus on 2014-03-01
The computer has enough muscles to run any flavour (desktop environment) of Ubuntu. But there might be problems to find a driver that cooperates with the graphics card. You might need some boot option for example **nomodeset** See this link [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
> 
Installed 12.04 without any trouble and when it asked to reboot the machine i pulled the USB drive and booted. How did you install Ubuntu? Did you do it with the desktop installer (in graphics mode) or with the alternate installer (or mini.iso) in text mode?

---

### Post by oldfred on 2014-03-01
Also are you consistently installing in UEFI or BIOS boot modes. All systems should be the same boot mode.

If you have gpt partitioning you can install Ubuntu in BIOS or UEFI, but Windows only boots from gpt with UEFI.
Both Windows & Ubuntu only boot in BIOS mode from the 30+ year old MBR(msdos) partition scheme.

If interested in more info on gpt & UEFI see link in my signature.

---

