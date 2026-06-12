---
title: "boot issue"
date: 2022-05-01
forum: Installation &amp; Upgrades
---

### Post by baho13 on 2022-05-01
Good day, my apologies if this question was asked. I can not boot into my Live-Usb of Ubuntu16.04LTS.

Boot-Info Summary is attached file **Boot-Info_20220501_1514.txt**.

Thank you in advance!

---

### Post by oldfred on 2022-05-01
Your has expired or EoL - end of life.
Best to have good backups and install 20.04 or 22.04.

I thought Boot-Repair only worked on current versions, anyway.

---

### Post by baho13 on 2022-05-01
I have Ubuntu 22.04 installed on my machine already. I am trying to dual-boot it with Live usb Ubuntu 16.04 which I need to test a usb-adapter driver.

---

### Post by tea for one on 2022-05-01
> **baho13 said:**
> Good day, my apologies if this question was asked. I can not boot into my Live-Usb of Ubuntu16.04LTS.
Please remove your Live-USB of Ubuntu 16.04.
Can you still boot into your installed Ubuntu 22.04?

---

### Post by grahammechanical on 2022-05-01
Please explain what happens when you try to boot from the 16.04 USB Memory stick? Are you entering the UEFI settings utility and selecting the 16.04 USB memory stick as the boot option? 

From what I can see from the Boot Repair summary you have Ubuntu 22.04 in sda and have run Boot Repair from it. But sda has both a BIOS boot partition and an EFI boot partition and you were running 22.04 in BIOS/Legacy/CSM mode. 

> The firmware seems EFI-compatible, but this installed-session is in Legacy/BIOS/CSM mode (not in EFI mode).

> OS#1:   The OS now in use - Ubuntu 22.04 LTS CurrentSession on sda3
OS#2:   Ubuntu 22.04 LTS on sdb3 

You also have 22.04 on sdb and that only has an EFI boot partition. We should not mix UEFI installs and BIOS/Legacy/CSM installs. If we do then the only way we can boot an OS would be to select it from the UEFI settings boot manager. If each OS is installed in the same mode then we will get a Grub boot menu which will give us options to boot either OS.

All this is separate from the problem of not being able to load the Ubuntu 16.04 live session from the USB memory stick. Which is why it would be helpful if you explained what happens when you try to boot from the USB memory stick.

Regards

---

### Post by baho13 on 2022-05-01
Yes, I can boot to my Ubuntu 22.04 desktop.

---

### Post by baho13 on 2022-05-01
That's the problem - it just boots into Ubuntu 22.04 system. I tried pressing Esc and Shift but no luck.

---

### Post by tea for one on 2022-05-02
> **baho13 said:**
> boot it with Live usb Ubuntu 16.04 which I need to test a usb-adapter driver.

This is not strictly a problem with booting an installed Ubuntu system where boot-repair is needed.
It seems to be a hardware issue using an unsupported 6 year old OS?

Perhaps consider opening a new thread in the Hardware Forum with exact details of the USB-adapter and what it is intended to do.

The usual info: The action you performed, the expected result and the actual result.

Silly example:-
Using Ubuntu 22.04, I inserted my USB device
I expected my time-travelling capsule to land in the garden
My toaster ejected a slice of bread directly into the kitchen sink

---

### Post by baho13 on 2022-05-04
[COLOR=#000000]Yes, I can boot to my Ubuntu 22.04 desktop.[/COLOR]

---

### Post by baho13 on 2022-05-04
> **tea for one said:**
> Please remove your Live-USB of Ubuntu 16.04.
Can you still boot into your installed Ubuntu 22.04?

[COLOR=#000000]Yes, I can boot to my Ubuntu 22.04 desktop.[/COLOR]

---

### Post by ajgreeny on 2022-05-04
You need to either set your BIOS/UEFI to boot from the USB first or more conveniently use the Device Boot Priority key, often F8 or F12, but it can be any number of the F# keys, pressed and held immediately after pressing the Power-on button.

Esc or Shift are used normally at boot to show the grub menu but this is not what you need.

However, as others have told you already, 16.04 is now EOL so it is a bit pointless using that just to check a usb-adapter driver as in the six years since 16.04 was released many system files and methods of working have changed; newer kernels in both 20.04 and more in 22.04 will possibly, maybe probably, now incorporate drivers for hardware that did not work in 16.04.

---

