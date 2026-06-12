---
title: "Ubuntu 18:10 -  2 Computer Installs  - One boots Purple and the other boots Black?"
date: 2018-11-11
forum: Installation &amp; Upgrades
---

### Post by Ice-Tea on 2018-11-11
I installed Ubuntu 18:10 when it was first released and that computer boots Purple and i installed 18:10 on a different computer last night and that one boots Black , What's that all about? :P

Both ISO's where downloaded from Ubuntu webpage and hash checked.

---

### Post by kc1di on 2018-11-11
With the information you provided I can only guess that they have different video cards and need different drivers.

---

### Post by Ice-Tea on 2018-11-11
Both have Nvidia cards and both installed with the standard nouveau drivers , when does a different video card select a different colour for the Grub and Boot splash screens anyway?

---

### Post by oldfred on 2018-11-11
Is this after install or the installer.

You get two different screens with installer, one with BIOS and another with UEFI.
       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by kc1di on 2018-11-11
depending on the Nvidia card - you may need nomodeset on the one that gets the black screen.

---

### Post by Ice-Tea on 2018-11-12
> **oldfred said:**
> Is this after install or the installer.

You get two different screens with installer, one with BIOS and another with UEFI.
       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Funnily enough i found that link at Google shortly after my last post and it turns out the PC keeps those Bios differences even after install which explains why one is Purple and the other Black.

To confirm this i done a fresh install on both PC's using the same USB stick  on both and the old Bios computer stayed Purple and the newer UEFI computer stayed Black as they did before , though the newer computer has UEFI disabled so i assume the installer still detects it as a UEFI.

---

### Post by oldfred on 2018-11-12
New UEFI systems, should offer two boot options for Ubuntu live installer. One clearly UEFI and other just a name or label of flash drive which is then the BIOS/CSM/Legacy boot option.
How you boot installer is then how it installs.

Many systems require settings to turn on/off UEFI Secure boot or Legacy/CSM/BIOS boot.  And separate setting to allow USB boot, required if Secure Boot on.
Secure Boot may be  "Windows" or "Other". And fine print will say use "Other" for Windows 7 as it does not support UEFI Secure Boot.

---

### Post by Ice-Tea on 2018-11-12
I disabled UEFI on the newer computer so the only option was legacy boot yet it sill chose black for the grub and splash screen so i can only assume the hardware detection sees the computer as UEFI and chose that colour scheme.

I can't think of any other reason as both computer work perfectly with Nouveau and Nvidia drivers , There is no corruption or blank screens that either need nomodeset as both show the splash screen working with the 3 dots and with quiet splash disabled there are no on screen boot errors or dmesg problems.

---

