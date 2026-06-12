---
title: "New install of Ubuntu 22.04 cannot proceed"
date: 2023-12-16
forum: Installation &amp; Upgrades
---

### Post by grandmasterporkins on 2023-12-16
I have a *AMD Gigabyte B650 + RTX 4090* desktop that runs Win 10. Have a second nvme drive that I want to install Ubuntu for dual-booting purposes.

Steps

[LIST=1]
[*]Used balenaEtcher to write Ubuntu Desktop 22.04 (ubuntu-22.04.3-desktop-amd64.iso)
[*]Boot from UEFI Sandisk flashed drive
[/LIST]

This opens a text interface *GNU GRUB version 2.06* with following options:
[LIST=1]
[*]Try or Install Ubuntu
[*]Ubuntu (Safe Graphics)
[*]OEM Install
[*]Boot from next volume
[*]UEFI Firmware Settings
[/LIST]

Accessing "Try or Install Ubuntu" results in about ten of these errors:

```

ACPI Bios Error (bug) Failure creating named object SB.PCI0.GPP7._PRW
AE_ALREADY_EXISTS

```

And the last message is:

```

ACPI BIOS error Failure 
hub 8-0:1.0: config failed, hub doesn't have any ports (err -19)
nouveau 0000:01:00.0: unknown chipset

```

Then it's basically locked until I manually reboot the system.

I read some workarounds related to `nomodeset` among other things but it was mostly old advice around Ubuntu 18x. What am I supposed to do here? My setup seems pretty bog standard - AMD Chipset + NVIDIA GPU. 

I can't find any basic info around how to install Ubuntu 22.04 for the *first time* with a nVidia RTX setup. Do I connect my monitor to the onboard GPU and install Ubuntu then later go download nVidia drivers???

---

### Post by ubfan1 on 2023-12-16
Did you try the "Safe graphocs" choice?  That includes the nomodeset.  Used to be safe boot had to be off, but don't think that's necessary anymore.  Once you get it booted, then run ubuntu-drivers or the Software & Updates/Additional drivers to install the latest recommended Nvidia driver.

---

### Post by SeijiSensei on 2023-12-17
> **grandmasterporkins said:**
> I can't find any basic info around how to install Ubuntu 22.04 for the *first time* with a nVidia RTX setup. Do I connect my monitor to the onboard GPU and install Ubuntu then later go download nVidia drivers???
If you check the "download third-party drivers" box during installation, the installer will download the correct drivers for your NVIDIA card.

---

