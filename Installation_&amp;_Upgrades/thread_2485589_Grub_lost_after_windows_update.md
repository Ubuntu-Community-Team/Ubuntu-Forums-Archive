---
title: "Grub lost after windows update"
date: 2023-04-03
forum: Installation &amp; Upgrades
---

### Post by cressrt2 on 2023-04-03
Hi,
The Windows OS had an update installed and afterwards the Grub has disappeared .  I ran the Boot Repair from a USB but it failed to repair it, the following is the report [https://pastebin.ubuntu.com/p/2MBqbTX9f2/](https://pastebin.ubuntu.com/p/2MBqbTX9f2/)
Any help gladly received

Thanks

---

### Post by oldfred on 2023-04-03
What Brand/Model system?
Seen several previous posts with this issue: 
```
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
```

I see UEFI Secure Boot is off.
But do you have additional settings in UEFI for locking or preventing changes in UEFI?

Some examples:
HP Zbook 15 NVRAM locked, install issues
[https://ubuntuforums.org/showthread.php?t=2482555](https://ubuntuforums.org/showthread.php?t=2482555)
Fujitsu lifebook ah512. Secure boot options blocked in bios - UEFI password required
[http://ubuntuforums.org/showthread.php?t=2171114](http://ubuntuforums.org/showthread.php?t=2171114)

The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.
Lenovo Thinkpad T495 Boot Order Lock
[https://askubuntu.com/questions/1404259/getting-grub-menu-to-work-on-dual-boot-ubuntu-22-04-windows-11-currently-boots](https://askubuntu.com/questions/1404259/getting-grub-menu-to-work-on-dual-boot-ubuntu-22-04-windows-11-currently-boots)

---

### Post by cressrt2 on 2023-04-03
Hi,
it is a Lenovo Ideapad 3, I have looked at the links you posted and could not see anything there that helped.

---

### Post by tea for one on 2023-04-03
Can you double-check/disable the following (if they exist) in your UEFI settings?

Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Fast Boot (It may prevent access to one-time boot menu via dedicated keys because the device boots too fast) 
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module)
Disable Device Guard (some Lenovo devices)
Disable OS Optimised Defaults (some Lenovo devices)

---

### Post by cressrt2 on 2023-04-03
Its a Lenovo Idea Pad 3 running Ubuntu 22.04 and Windows 10
I had a look at the links and couldn't see anything that matched.

---

### Post by oldfred on 2023-04-03
This was with an older Ubuntu, not sure if he mentions anything related. 
Newer Ubuntu should be better.

Lenovo Ideapad 3 15 with Ryzen 5 5500U Ubuntu 21.04 with the Linux 5.11 kernel, it's been working out fine.
[https://www.phoronix.com/scan.php?page=article&item=lenovo-ryzen5-5500u&num=1](https://www.phoronix.com/scan.php?page=article&item=lenovo-ryzen5-5500u&num=1)

Have you updated UEFI to latest available from Lenovo?

---

### Post by cressrt2 on 2023-04-04
Have looked at all you have suggested and still no grub!  If I try to reinstall Ubuntu would that bring it back and not affect any of the data and files that I currently have?

---

### Post by oldfred on 2023-04-04
You always need to have good backups.
Depending on issues, you may be able to reinstall without formatting, so your data is preserved, but any configuration files you edited will go back to defaults.

[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) & 
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

When you have good backups, it becomes easy to reinstall & restore from backup. Often as quick as an hour once you know how.

---

### Post by cressrt2 on 2023-04-05
OK installed a new version and back up now.
Thanks

---

