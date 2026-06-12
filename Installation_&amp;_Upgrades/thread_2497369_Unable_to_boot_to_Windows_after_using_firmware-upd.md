---
title: "Unable to boot to Windows after using firmware-updater snap"
date: 2024-05-02
forum: Installation &amp; Upgrades
---

### Post by superian on 2024-05-02
Dell Latitude 5410 laptop, that was dual booting into Ubuntu MATE and Windows 10 22H2.  

The snap store said I needed to update the "firmware-updater" 0+git.5007558. I allowed that. It reboots the laptop and updates the BIOS.  

After that, it wouldn't boot properly. Only 'Linux Firmware Updater' and network boots were appearing in the EFI options. If I allowed the former to boot, there would be the two line message:  

fwupd-efi version 1.4
WARNING: No update to process, exiting in 10 seconds.  

I installed a fresh Ubuntu MATE 24.04 over the old Ubuntu MATE partition after copying the files to a USB stick. That's worked OK and it'll boot to that, but it still won't boot into Windows. The Windows installation is still detected by update-grub and appears in the grub menu, but selecting it results in the screen changing colour to a different grey for a second or two and then returning to the grub menu.  

I have followed the advice on dell.com to repair the EFI bootloader.. still no joy.

What to try now?

---

### Post by superian on 2024-05-02
Ah, what's worked is doing

bcdboot c:\windows

via a Windows command line on an installation ISO. That got the laptop booting straight into Windows, but using BootRepair ISO fixed that...

I'd still like to know why allowing the snap upgrade caused this, mind.

---

### Post by oldfred on 2024-05-02
Some UEFI firmware updates, reset UEFI to defaults.
That may turn UEFI Secure Boot on, or make other changes from any you may have made to install Ubuntu originally.

My desktop is now older and is not in fwupdate list. I orginally only could manually update UEFI firmware & NVMe firmware.
But had to keep a list as I made several changes to default UEFI settings.

---

