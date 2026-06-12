---
title: "Lucid freezes during install"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by damnated on 2010-08-06
I'm trying to install Lucid to an older PC, but it constantly freezes during the setup. Most of the time I can't even select whether I want to install or to try the OS, but sometimes I get past that. Once I got to the point where the installation was copying the files to the hard drive, but it froze once again at 5%.

The PC's config is: 1,8 GHz AMD processor, 768 MB DDR1 memory, 200 GB HDD, ATI 9200 VGA and a DVD drive. According to the minimum reqs for lucid this should be more than enough, yet Lucid froze once while in Live CD mode.  

Should I try an older ubuntu version? Or could this be something more serious, ie hardware issue in which case you guys can't help..

PS: afaik the DVD is not corrupted.

---

### Post by utilitytrack on 2010-08-06
Hello, I can't say that your computer is old. Wich the motherboard you use? Anyway try unplug all USB devices, also turn off USB subsystem in BIOS. Sometimes it might help. What version of Ubuntu you installed?

---

### Post by kngsze on 2010-08-06
I had a very similar issue when trying to install on my fairly old laptop. The only way I could get either the live CD or install was to boot was with   &#8220;acpi=off i915.modeset=1 xforcevesa&#8221;    parameters.    
 

 Hit F6 at Live CD menu, if you've managed to get there,  then select acpi=off.  Hit Esc, then end to scroll to the end of the boot kernel (if thats the right name, sorry) and remove &#8220;quite splash&#8221;.  Seeing where the boot hangs may be of some help.    You may also find that any combination of the F6 options gets you in

---

### Post by utilitytrack on 2010-08-06
to **kngsze**

Yes, it's generally good advice, except "i915.modeset=1" boot parameter because **damnated** don't have Intel graphics.

---

### Post by damnated on 2010-08-06
> **utilitytrack said:**
> Hello, I can't say that your computer is old. Wich the motherboard you use? Anyway try unplug all USB devices, also turn off USB subsystem in BIOS. Sometimes it might help. What version of Ubuntu you installed?

It has Asus motherboard, I have no idea atm what model is it exactly, and it's definitely old to some extent because for instance I can't boot off a USB drive. 

At the time of install I had no USB devices plugged-in, but I will try with turning off the USB subsystem.

Also, I don't have any OS on that particular hard drive, and it's empty.

---

### Post by utilitytrack on 2010-08-06
to **damnated**

[I](aside)
[/I]For help us to understand and solve your technical problems you should give  aswers exactly. You say "Asus". It's not a answer.

---

### Post by damnated on 2010-08-06
```

--------[ AIDA32 (c) 1995-2004 Tamas Miklos ]--------------------------------------------------------------------------- 
 
    Version                                           AIDA32 v3.93 
    Author                                            tamas.miklos@aida32.hu 
    Homepage                                          http://www.aida32.hu 
    Report Type                                       Quick Report 
    Computer                                          BEA-66B2295DEDC (kicsigep) 
    Generator                                         Bea 
    Operating System                                  Microsoft Windows XP Professional 5.1.2600 (WinXP Retail) 
    Date                                              2010-08-06 
    Time                                              21:15 
 
 
--------[ Motherboard ]------------------------------------------------------------------------------------------------- 
 
    Motherboard Properties: 
      Motherboard ID                                    12/29/2003-VT8377/VT8235-A7V8X-X 
      Motherboard Name                                  Asus A7V8X 
 
    Front Side Bus Properties: 
      Bus Type                                          DEC Alpha EV6 
      Bus Width                                         64-bit 
      Real Clock                                        100 MHz (DDR) 
      Effective Clock                                   200 MHz 
      Bandwidth                                         1600 MB/s 
 
    Memory Bus Properties: 
      Bus Type                                          DDR SDRAM 
      Bus Width                                         64-bit 
      Real Clock                                        167 MHz (DDR) 
      Effective Clock                                   333 MHz 
      Bandwidth                                         2667 MB/s 
 
    Chipset Bus Properties: 
      Bus Type                                          VIA V-Link 
      Bus Width                                         8-bit 
      Real Clock                                        67 MHz (ODR) 
      Effective Clock                                   533 MHz 
      Bandwidth                                         533 MB/s 
 
    Motherboard Physical Info: 
      CPU Sockets/Slots                                 1 
      Expansion Slots                                   6 PCI, 1 AGP 
      RAM Slots                                         3 DIMM 
      Form Factor                                       ATX 
      Motherboard Size                                  240 mm x 300 mm 
      Motherboard Chipset                               KT400 
      Extra Features                                    Q-Fan, CPU Overheating Protection, JumperFree, Stepless Freq Selection 
 
    Motherboard Manufacturer: 
      Company Name                                      ASUSTeK Computer Inc. 
      Product Information                               http://www.asus.com/products/mb/mbindex.htm 
      BIOS Download                                     http://www.asus.com/support/download/download.aspx 
 

------------------------------------------------------------------------------------------------------------------------ 
 
The names of actual companies and products mentioned herein may be the trademarks of their respective owners.

```

---

