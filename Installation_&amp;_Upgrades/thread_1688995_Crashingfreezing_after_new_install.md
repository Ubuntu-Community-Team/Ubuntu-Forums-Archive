---
title: "Crashing/freezing after new install"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by chrisbay90 on 2011-02-16
I have a fresh install of Maverick on a Toshiba r700 laptop  PT310A-05N011. I am experiencing constant freezing. The computer will  without warning completely freeze. Can not move the mouse or even drop to  a tty shell. After about 5 seconds the fan will spin up to full speed. I  then have to do a hard shutdown.

Every time this has happened i have been connected up to a wireless  network with firefox open while actively surfing the net. This issue did  not happen before I installed the wireless driver (Broadcomm proprietary,  downloaded through ubuntu Additional Drivers). I'm not sure how  relevant that is though as 90% of what i do on this laptop is surfing  and i installed the driver a few hours after install.

This freezing does not happen in windows 7 and I have left it running prime95 overnight once in both 7 and ubuntu without error.

Does anyone know what this may be, how i might resolve it or steps I can take to diagnose it, logs i can check?

---

### Post by chrisbay90 on 2011-02-19
Bump.

Even if no one has a solution, does anyone know how I can diagnose this further?

---

### Post by Dutch70 on 2011-02-19
> **chrisbay90 said:**
> Bump.

Even if no one has a solution, does anyone know how I can diagnose this further?

I know nothing about broadcom drivers, but what video card are you using? Also, what did you do for Internet before you installed it? or...how long did you use it with no freezes.

Run this in terminal and post the output in code tags by using the
 # symbol on the toolbar...
```
lspci
```

---

### Post by chrisbay90 on 2011-02-19
> **Dutch70 said:**
> I know nothing about broadcom drivers, but what video card are you using? Also, what did you do for Internet before you installed it? or...how long did you use it with no freezes.

Run this in terminal and post the output in code tags by using the
 # symbol on the toolbar...
```
lspci
```

Thanks for you're feedback.

I am using the integrated graphics controller (intel i3).

As for the internet, I plugged it into the lan and installed the wireless driver. I did very little browsing before then. I am starting to think the wireless/browser are unrelated. It has crashed a few times without a browser open and I have un-installed the wireless driver and it has crashed since, although far less frequently.

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LC Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
06:00.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

---

### Post by Dutch70 on 2011-02-19
a lot of ppl are having problems with Intel graphics cards, as I did.

Do you have compiz? if not, try going to system>preferences> appearance, select the visual effects tab & set it to none. 
see if that helps.

---

### Post by chrisbay90 on 2011-02-20
> **Dutch70 said:**
> a lot of ppl are having problems with Intel graphics cards, as I did.

Do you have compiz? if not, try going to system>preferences>  appearance, select the visual effects tab & set it to none. 
see if that helps.

Okay thanks for the information. Yes i do have compiz. I will turn it  off/down and see how that goes. Although it may be hard to gauge as the  crashes seem to have suddenly stopped in the last 2 days (was happening  at least twice an hour). Do you know if there will/is any fixes proposed  or on development?

Thank you.

---

### Post by Dutch70 on 2011-02-20
> **chrisbay90 said:**
> Okay thanks for the information. Yes i do have compiz. I will turn it  off/down and see how that goes. Although it may be hard to gauge as the  crashes seem to have suddenly stopped in the last 2 days (was happening  at least twice an hour). **Do you know if there will/is any fixes proposed  or on development?**

Thank you.

Give this a try Chris...post #22 on page 3 should do the trick. 
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1307001&page=3[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1307001&page=3")

Just be sure to write everything down before you go into a tty.
Hopefully that will work for you, I know it did for me.

If it works, save it & share it please. There are lots of us that have been or are where you're at.

Let us know if it works
Best regards

---

### Post by chrisbay90 on 2011-05-08
> **Dutch70 said:**
> Give this a try Chris...post #22 on page 3 should do the trick. 
[[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=1307001&page=3[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1307001&page=3")

Just be sure to write everything down before you go into a tty.
Hopefully that will work for you, I know it did for me.

If it works, save it & share it please. There are lots of us that have been or are where you're at.

Let us know if it works
Best regards

Thank you. I tried this advice and at first it seems to have worked. However after extended use, no it still crashes.

I can now say. **It crashes only when on battery power. Crashes are more frequent the lower the battery level. Never crashes when battery capacity is >80%. Does not crash in windows.**

---

