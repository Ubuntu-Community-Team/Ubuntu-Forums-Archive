---
title: "Newbie Q - Graphic mode problem"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by mike9682000 on 2008-01-05
Hello, all

I tried to test run ubuntu from its CD. The initial splash with the progress bar does show up, but then I see the initialization messages (text as well) then nothing. Switched to 640x480x16 with no effect.

I installed Ubuntu with the text only version CD. The desktop does not display at all - just some multicolored flashing text characters. It seems Ubuntu cannot get my card to switch from text to graphic mode.

Configuration

m'brd: Asus M2N-E SLI
AMD 64 FX62
Radeon X1950
2GB RAM
HDD SATA 1 Windows Vista (disconnected while installing Ubuntu) - 80 GB
HDD SATA 2 Ubuntu - never seen running - 80 GB

Any ideas would be much appreciated

Thx

---

### Post by taurus on 2008-01-05
Log in with your username and password.  Then, what happens if you run this command at the prompt?

```
startx
```
And if you need to reconfigure your X server, you can run

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by mike9682000 on 2008-01-05
I don't get a chance to log in.

I have no login window, no prompt nothing...

---

### Post by Partyboi2 on 2008-01-05
Are you able to get to a terminal?
Ctrl+Alt+F1 to F6

---

### Post by mike9682000 on 2008-01-05
I managed to get to a terminal by hitting esc and starting in safe mode.

on startx command I got: 
(WW) VESA (0): SET VBE MODE FAILED
(EE) Fatal server error
AddScreen/ScreenInit failed for driver 0

On lspci command I get my X1950 identified as X1900 at PCI 05:00.0
and an "ATI tech unknown device" at PCI 05:00.1

I tried to manually set up the ati card so I picked ati x server driver, PCI 05:00:0 etc.

when i commanded startx again I got:

No matching device section for instance PCI 05:00:1 (although I picked 00:0 - that and viceversa happened several times)
No devices detected.

I have the driver downloaded from ATI and burnt on a CD (download and burn under vista). How can I install the ATI driver from the terminal?

As well, I am unsing a logitech wireles mouse. the wireless receiver is connected to a USB port. What do I choose on mouse input setup?

---

