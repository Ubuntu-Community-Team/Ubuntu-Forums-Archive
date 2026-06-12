---
title: "RTL8192E and the Testing version of Lucid"
date: 2010-01-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lotharmat on 2010-01-29
Well - In the vain hope that my wireless card would work in Lucid (Kernel 2.26.32.11??) I booted from the live cd

lspci shows that the card is present and occupying a resource but still no dice

dmesg shows the following.

```
[   78.493865] r8192_pci: module is from the staging directory, the quality is unknown, you have been warned.
[   78.497707] ieee80211_crypt: registered algorithm 'NULL'
[   78.497711] ieee80211_crypt: registered algorithm 'TKIP'
[   78.497712] ieee80211_crypt: registered algorithm 'CCMP'
[   78.497714] ieee80211_crypt: registered algorithm 'WEP'
[   78.497726] 
[   78.497727] Linux kernel driver for RTL8192 based WLAN cards
[   78.497728] Copyright (c) 2007-2008, Realsil Wlan
[   78.497785] rtl819xE 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   78.497793] rtl819xE 0000:02:00.0: setting latency timer to 64
[   78.560674] Dot11d_Init()
[   78.560685] IRQ 16
[   78.667604] uvcvideo: Found UVC 1.00 device Namuga 1.3M Webcam (0ac8:c335)
[   78.676323] input: Namuga 1.3M Webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input9
[   78.676432] usbcore: registered new interface driver uvcvideo
[   78.676436] USB Video Class driver (v0.1.0)
[   78.941393] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04711/0xa00000
[   78.976767] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[   79.360062] usb 2-3: reset high speed USB device using ehci_hcd and address 2
[   80.287327]   alloc irq_desc for 22 on node -1
[   80.287330]   alloc kstat_irqs on node -1
[   80.287337] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   80.287399] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   80.500496] rtl819xE: PlatformInitFirmware()==>
[   80.500497] 
[   80.500519] rtl819xE 0000:02:00.0: firmware: requesting RTL8192E/boot.img
[   80.529380] hda_codec: ALC272: BIOS auto-probing.
[   80.530851] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
[   80.539643] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   80.539709] HDA Intel 0000:01:00.1: setting latency timer to 64
[   80.547019] rtl819xE:request firmware fail!
[   80.547021] 
[   80.547023] rtl819xE:ERR in init_firmware()
[   80.547024] 
[   80.547026] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
[   80.547027] 
[   80.551493] sky2 eth0: enabling interface
[   80.553754] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

Any ideas?

---

### Post by falconindy on 2010-01-29
You need to find the firmware file for the card. [This](http://www.linuxquestions.org/questions/linux-wireless-networking-41/firmware-for-realtek-8192-761714/) may be of help to you.

---

### Post by lotharmat on 2010-01-29
I think that may be in the file that Realtek sent me..

Would it just be the boot.img file in the firmware folder?

---

### Post by Ibidem on 2010-01-29
> **lotharmat said:**
> I think that may be in the file that Realtek sent me..

Would it just be the boot.img file in the firmware folder?
They say it's "requested as boot.img" in the thread referred to (post #10)...
Good luck getting it working, it seems that others were having plenty of trouble.

---

### Post by Asem on 2010-01-30
Hi
I have the same card and i am using this driver
[http://launchpadlibrarian.net/38201251/rtl8192se_linux_2.6.0014.0115.2010.tar.gz](http://launchpadlibrarian.net/38201251/rtl8192se_linux_2.6.0014.0115.2010.tar.gz)
just compile it while you are root like that
sudo su
make ;make install
to know more about the driver have a look at this launchpad bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all)

i hope that the driver will be included in Lucid by default to have a better support.

---

### Post by lotharmat on 2010-01-30
Hmm - those links seem to refer to the 8192SE. Bitter experience has told me that these cards are totally different and the SE drivers do not work with the E

Does anybody reccon that with the final version of Lucid; the firmware will be included?

---

### Post by Daniel Lewandowski on 2010-01-30
What kernel do you use - i386 or amd64?

---

### Post by lotharmat on 2010-01-31
i386.

But I managed to get the realtek provided drivers working. It seems like just the firmware is missing in 2.6.32.xx

Problem is that I have been testing using the Live CD and so I am unsure how to make the firmare folder /lib/firmware/[uname-r]/rtl8192/ stick on a reboot.

Any ideas?

Pendrivelinux doesn't have an installer yet for Lucid.

---

### Post by ssam on 2010-02-17
bug and workaround
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508746](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508746)

---

