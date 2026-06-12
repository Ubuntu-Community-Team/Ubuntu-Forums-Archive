---
title: "compaq presario a900 &amp; lucid"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by dangermanfears on 2010-05-08
I just installed lucid on My laptop , COMPAQ PRESARIO A900. 
First I notice that the wirelssLan light lit up on startup and after about 1 minute in the system, it just freezes, but I can still use the tab key to move around.

But then when I restart without the usbmouse it worked almost fine. the touchpad seems slow.

Then i upgraded the kernel to 2.6.32.14 and now keyboard, mouse doesn't work.

So frustrated, I had wiped out my nicely setup 9.10.

Is there any hope for me, Or should I default back to 9.10?

---

### Post by Catharsis on 2010-05-09
I'm assuming the keyboard and mouse are bluetooth? Hence the mention of wireless?

I doubt it'll work, but try:
1) Hold down Shift as you boot to enter grub.
2) Hit 'e'. Add "i915.modeset=1" after "quiet splash".
3) Ctrl+x to boot.

Could you also post your hardware specs?
```
lspci
```

---

### Post by dangermanfears on 2010-05-09
> **Catharsis said:**
> I'm assuming the keyboard and mouse are bluetooth? Hence the mention of wireless?

I doubt it'll work, but try:
1) Hold down Shift as you boot to enter grub.
2) Hit 'e'. Add "i915.modeset=1" after "quiet splash".
3) Ctrl+x to boot.

Could you also post your hardware specs?
```
lspci
```
Not a wireless mouse or keyboard. it is laptop with a wired mouse.


Reinstaling the fouth time. I found that the culprit was my ace MOUB103 mouse. ubuntu works fine when I use my touchpad or another mouse.

How do I fix this? Are there mouse that not supported by ubuntu 10?

& My wlan button still lit on startup, pressing it should make switch it off, but it doesn't in ubuntu. I would mind this, but becaue of wlan on drains battery life. 

Anyway to not turn it up on startup?

Thanks my lspci below.

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

