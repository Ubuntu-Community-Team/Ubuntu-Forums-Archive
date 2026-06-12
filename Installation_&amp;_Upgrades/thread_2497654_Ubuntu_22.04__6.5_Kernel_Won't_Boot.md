---
title: "Ubuntu 22.04:  6.5 Kernel Won't Boot"
date: 2024-05-13
forum: Installation &amp; Upgrades
---

### Post by ben@kietzman.org on 2024-05-13
I have had difficulty booting Ubuntu on my new HP 15.6" Portable Laptop.* My other eight computers run Ubuntu 22.04 without any issues.* I attempted to install 22.04 from the live USB.* The live USB booted up fine and installed the OS.* However, when I rebooted, I would receive the following error:

[INDENT]
Gave up waiting for root file system device.* Common problems:
 - Boot args (cat /proc/cmdline)
* * - Check rootdelay= (did the system wait long enough?)
*- Missing modules (cat /proc/modules: ls /dev)
ALERT!* UID=b6adad20-b6c6-4e8a-8b5f-6d1d34ffb50a does not exist.* Dropping to a shell!
[/INDENT]

I attempted to install 24.04 and saw the same kind of error.* I attempted to install 20.04 and it booted up successfully.* However, my trackpad and wifi did not work under*20.04.* From there, I upgraded from 20.04 to 22.04 and it no longer booted.* I then chose the 5.15 kernel instead of the 6.5 kernel under 22.04 and it booted but the trackpad and wifi did not work.* Booting under the 6.2 kernel yielded the same result.* So I then booted the live USB for 22.04 and ran the boot-repair program.* I saved the Boot Info Summary to:

[https://paste.ubuntu.com/p/4Vy5yRVrpy/](https://paste.ubuntu.com/p/4Vy5yRVrpy/)

I then chose the Recommended Repair and this is the resulting Boot Info Summary:

[https://paste.ubuntu.com/p/JQhBjrZs3Y/](https://paste.ubuntu.com/p/JQhBjrZs3Y/)

I'm not sure where to go from here.* Any suggestions would be appreciated.* Thank you.

---

### Post by tea for one on 2024-05-14
> **ben@kietzman.org said:**
> 
I then chose the Recommended Repair and this is the resulting Boot Info Summary:
[COLOR="#0000FF"]Line 76[/COLOR]  - Warning: NVram is locked (Ubuntu not found in efibootmgr)

Can you search your UEFI setttings and disable the following (if present):-
TPM (Trusted Platform Module)
PTT (Platform Trust Technology)
FTPM (Firmware Trusted Platform Module)
TPT (Trust Platform Technology)
Lock UEFI BIOS Settings
Boot Order Lock

Again, if present - Enable Microsoft 3rd Party UEFI CA

---

### Post by oldfred on 2024-05-14
How new of an HP?
Is this the latest UEFI firmware for your system?
> BIOS/UEFI firmware: F.09(15.9) from AMI


There is a bug somewhere. Not sure if Boot-Repair, grub, kernel or modprobe.
> modprobe: FATAL: Module efivars not found in directory /lib/modules/6.5.0-18-generic

Note sure if older systems had efivars in the /lib/modules for each kernel or not.

But even back with 13.04 efivars was in /sys/firmware/efi/efivars
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1146868](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1146868)
 And conclusion was 'CONFIG_EFI_VARS' is the culprit

Actually is here where my system shows it:
ls /sys/firmware/efi/efivars
And I get this error, if I run modprobe even though no issues on UEFI install.
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo modprobe  efivars [/COLOR]
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.8.0-31-generic


[/FONT]
```

We seem to see this more with some upgrades, not new installs. So was an older kernel not configured correct?

---

