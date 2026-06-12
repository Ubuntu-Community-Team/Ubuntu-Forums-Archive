---
title: "Ubuntu 18.04 very slow boot in dual boot"
date: 2020-05-21
forum: Installation &amp; Upgrades
---

### Post by m-nikjah on 2020-05-21
I have recently installed Ubuntu 18.04 beside Windows 10 and the problem is Ubuntu boot takes very long time comparing Windows.
It seems there are big gaps here in my boot log

```
[    9.918120] ppdev: user-space parallel port driver
[   32.941450] (NULL device *): hwmon_device_register() is deprecated. Please convert the driver to use hwmon_device_register_with_info().
```

and here

```

[   47.198274] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   58.801534] rfkill: input handler disabled
[   70.037871] ahci 0000:00:17.0: port does not support device sleep
```

and many errors here

```
[    0.074450] ACPI Error: [_SB_.PCI0.RP05.PXSX] Namespace lookup failure, AE_NOT_FOUND (20170831/dswload2-191)
[    0.074450] No Local Variables are initialized for Method [PXSX]
[    0.074450] No Arguments are initialized for method [PXSX]
[    0.074450] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20170831/psobject-253)
[    0.074450] ACPI Error: Ignore error and continue table load (20170831/psobject-642)
[    0.074450] ACPI Error: Skip parsing opcode Scope (20170831/psloop-559)
[    0.074450] ACPI Error: [_SB_.PCI0.RP09.PXSX] Namespace lookup failure, AE_NOT_FOUND (20170831/dswload2-191)
[    0.074450] No Local Variables are initialized for Method [PXSX]
[    0.074450] No Arguments are initialized for method [PXSX]
[    0.074450] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20170831/psobject-253)
[    0.074450] ACPI Error: Ignore error and continue table load (20170831/psobject-642)
[    0.074450] ACPI Error: Skip parsing opcode Scope (20170831/psloop-559)
```

I'm new to Ubuntu and I would appreciate if anyone can help.

---

### Post by oldfred on 2020-05-22
How old is system? Or do you really have a parallel port?
If your UEFI/BIOS had hardware listed that does not exist, it can then write that into available hardware for operating system. Then system has to time out as it cannot find it. Make sure settings in UEFI/BIOS are correct.

What brand/model system?
What video card/chip?

Are you using IPv6?
I do not know wireless  issues, but best to run script from sticky threads in wireless sub-forum and post thread in that forum.
[https://ubuntuforums.org/forumdisplay.php?f=336](https://ubuntuforums.org/forumdisplay.php?f=336)

Most issues with ACPI can be ignored.

Other slow boot threads.
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

---

### Post by m-nikjah on 2020-05-23
The specifications of my system are: Asus fx570UD core i7/ nvidia GTX 1050/ 12GB RAM (2019)
Actually I don't know anything about parallel port. How can I check my UEFI/BIOS settings are correct?
And yes, my IPv6 is enabled.

---

### Post by oldfred on 2020-05-23
Have you updated UEFI from Asus to latest version? May just be something in UEFI?

Your UEFI has multiple tabs.
Check them and see if somewhere you have a setting for parallel port enabled.
I have not seen that in my system, but do have USB ports that need to be set to allow boot, enable keyboard & mouse,  & allow full support settings.

Have you installed nVidia driver?

Issues often common across similar models by vendor.
ASUS TUF FX504GM  Intel i7 8750H & nvidia 1060
[https://ubuntuforums.org/showthread.php?t=2431147](https://ubuntuforums.org/showthread.php?t=2431147)
Asus ZenBook Pro 14 UX480 Black screen acpi=off required, but 19.10 not required
[https://askubuntu.com/questions/1138820/black-screen-after-grub-selection-boot-from-usb-live](https://askubuntu.com/questions/1138820/black-screen-after-grub-selection-boot-from-usb-live)

---

### Post by m-nikjah on 2020-05-23
Actually I don't have parallel port on my system.
I downloaded and updated my UEFI right now but it didn't help.
Yes, I have installed nvidia driver but because it was draining my battery I disabled it and I'm using my intel graphics.

---

### Post by oldfred on 2020-05-23
1.3 says it is a combined port. combined serial/parallel port/floppy controller.

[https://www.infradead.org/~mchehab/rst_conversion/PCI/pci.html](https://www.infradead.org/~mchehab/rst_conversion/PCI/pci.html)

So perhaps some other device is incorrect?

Everything else related is CNC controller using parallel port errors.

---

