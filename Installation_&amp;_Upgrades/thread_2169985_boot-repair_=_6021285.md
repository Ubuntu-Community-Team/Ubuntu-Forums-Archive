---
title: "boot-repair = 6021285"
date: 2013-08-24
forum: Installation &amp; Upgrades
---

### Post by marcw on 2013-08-24
I just bought an HP 2000 notebook with Win 8 pre-installed.  In the bios I disabled Secure Boot before installing 12.04.3 for a dual boot.  The install completed without any issues.  After a reboot went to the Win loader I followed the Boot-Repair instructions which also went well except for a "Buggy kernel" message but it still boots to Windows.  My boot-repair URL is [http://paste.ubuntu.com/6021285](http://paste.ubuntu.com/6021285) in case anyone can make a recommendation.

---

### Post by oldfred on 2013-08-24
I think someone else with an HP said he could only boot with UEFI on which also made the secure boot on. Most UEFI systems have several settings UEFI with secure boot, UEFI with secure boot off and CSM/BIOS/Legacy boot. But some in CSM try to boot with files from efi partition in UEFI mode (but not secure boot) and if no efi partition then try to boot in BIOS mode from MBR.

Can you boot Windows with secure boot off? If not you will have to install the secure boot version of grub and the kernel to easily dual boot.

---

### Post by marcw on 2013-08-24
Yes, Windows can boot with Secure Boot either disabled or enabled.  I didn't mention it earlier but I had also tried the 12.04.3 unstall with Secure Boot enabled, first naked and then with Boot-Repair.  Same thing happened that happens now - no grub menu.  I should add that if I choose to select from the HP boot menu the option of F9 Boot Device Options I can boot Ubuntu from there.  That choice brings me to the grub menu from which I can boot Ubuntu just fine.  But that's a pain.  I'd like this thing to boot right into Ubuntu.  I haven't tried anything Legacy yet.  Should I?

Here's my F10 BIOS choices that seem relevant to UEFI

Network Boot Protocol
    IPv4 (UEFI)
    IPv6 (UEFI)
    IPv4+IPv6 (UEFI)

Legasy Support
    Disabled
    Enabled

Secure Boot
    Disabled
    Enabled

Clear All Secure Boot Keys

UEFI Boot Order
    DVD
    OS boot mgr
    USB Hard Disk
    USB DVD

Legacy Boot Order
    <same options as UEFI Boot Order>

---

### Post by oldfred on 2013-08-24
I would think under UEFI boot order you should have both Windows and ubuntu.
Others with different UEFI posted these:

---

### Post by marcw on 2013-08-25
So I said 'screw it' and installed Ubuntu on the whole drive after making recovery DVDs using HPs included tool.  No matter if Legacy was enabled or disabled or if Secureboot was enabled or disabled, I could not get my Ubuntu installs to display their grub menus by default.  With each one I could hit Esc and the drill down through the HP boot menus to get to the grub menu but what a pain.

So even though I now don't get a choice to use Win 8 - it doesn't exist any longer - I get what matters most, Ubunti desktop.

---

