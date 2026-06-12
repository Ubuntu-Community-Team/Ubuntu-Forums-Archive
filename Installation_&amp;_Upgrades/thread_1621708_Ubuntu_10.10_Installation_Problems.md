---
title: "Ubuntu 10.10 Installation Problems"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by OcelotXIII on 2010-11-14
Hello. I'm hoping someone can help me out. Im trying to install Ubuntu 10.10 in my PC which already has windows 7 pro installed. When I try to install Ubuntu the setup gets stuck in the ubuntu logo with the white dots on the bottom at it just stays there and does nothing. I left it for hours and nothing. I have installed Ubuntu 10.10 before on my work PC dual boot with xp and everything went smoothly but I can't seem to get it installed in my home PC. These are my hardware specs just in case:

Summary
        Operating System
            MS Windows 7 32-bit
        CPU
            AMD Athlon II X3 425    30 °C
            Rana 45nm Technology
        RAM
            4.0GB Dual-Channel DDR3 @ 666MHz (9-9-9-24)
        Motherboard
            MICRO-STAR INTERNATIONAL CO.,LTD 785GM-E51 (MS-7596) (CPU1)
        Graphics
            LA1610W @ 1366x768
            ATI Radeon HD 4200
        Hard Drives
            244GB Hitachi Hitachi HDP725025GLA380 ATA Device (SATA)    47 °C
            117GB Seagate ST3120026AS ATA Device (Unknown Interface)    43 °C
            313GB Seagate ST3320620AS ATA Device (Unknown Interface)    55 °C
            78GB Western Digital WDC WD800JD-00JNA0 ATA Device (SATA)    42 °C
        Optical Drives
            MagicISO Virtual DVD-ROM0000
            SONY DVD RW AW-G170S ATA Device
        Audio
            Realtek High Definition Audio

I also tried the alternate install and same thing, it gets stuck. Any suggestions?

---

### Post by mörgæs on 2010-11-15
Hi, welcome to the forum.

It sounds like you need to add boot options:
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by OcelotXIII on 2010-11-15
> **mörgæs said:**
> Hi, welcome to the forum.

It sounds like you need to add boot options:
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

I tried different options F6 to see if I can past the ubuntu logo screen but no luck. I get this warning (process: 383): Glib-WARNING getpwuid_r( ):Failed due to unknown user id (0)

---

### Post by mörgæs on 2010-11-15
This is a complicated error (or group of errors) to deal with: 
[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)

There is no clear advice that works on all hardware. I would try 10.04.1 as a first step and post in the other thread, if that does not help.

---

