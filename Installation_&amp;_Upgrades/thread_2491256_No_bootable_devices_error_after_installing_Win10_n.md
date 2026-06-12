---
title: "No bootable devices error after installing Win10 near Ubuntu 22.04 - neither boots."
date: 2023-10-02
forum: Installation &amp; Upgrades
---

### Post by ogrimuto on 2023-10-02
I have a Dell Latitude E6410 laptop. I have made the following structure on a 500 GB GPT SSD: 52 MB partition Reserved by system, 512 MB for EFI, 300 GB for later installation of Windows 10 and 150 GB for Ubuntu 22.04. After that I successfully installed and started Ubuntu 22.04. After 10 minutes I decided to install Windows 10. It installed, but on reboot it said "No bootable devices --strike F1 to retry boot, F2 for setup utility. Press F5 to run onboard diagnostics.". But that's half the trouble.
In the UEFI BOOT section of the UEFI BOOT, I have both "Windows Boot Manager" and "ubuntu", but when I click on either of them, after 3 seconds the same screen with "Windows Boot Manager" and "ubuntu" appears.
Can you please advise me how I can restore the systems to boot?

---
P.S. I've tried this instruction ([https://www.dell.com/support/kbdoc/en-us/000124331/how-to-repair-the-efi-bootloader-on-a-gpt-hdd-for-windows-7-8-8-1-and-10-on-your-dell-pc](https://www.dell.com/support/kbdoc/en-us/000124331/how-to-repair-the-efi-bootloader-on-a-gpt-hdd-for-windows-7-8-8-1-and-10-on-your-dell-pc)) but the bootrec /FixBoot command failed, Access Denied. I also tried removing the Windows bootloader with efibootmgr from Ubuntu Live USB, hoping that this would make Ubuntu work, but it didn't work.
P.P.S Now I've tried running Boot-Repair from my Ubuntu Live USB, but it is not working: An error occurred during the repair.
Error: NVram is locked (Ubuntu not found in efibootmgr). [https://paste.ubuntu.com/p/GmW2vWzSwK/](https://paste.ubuntu.com/p/GmW2vWzSwK/)
Locked-NVram detected.

---

### Post by TheFu on 2023-10-02
Always install Windows BEFORE installing Linux.  Always.

When trying to show storage layouts, verbal descriptions make it harder for us.  Please just run this command in a terminal and post the output wrapped in **forum code tags**. For example:
```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```

Without code-tags, the columns won't be retained and the output is impossible to read.

---

### Post by oldfred on 2023-10-02
Other threads with Locked-NVram issues. 
Usually a setting in UEFI.

Locked-NVram
[https://ubuntuforums.org/showthread.php?t=2482909](https://ubuntuforums.org/showthread.php?t=2482909)
[https://ubuntuforums.org/showthread.php?t=2490084](https://ubuntuforums.org/showthread.php?t=2490084)
Locked NVRAM - turning on Secure boot & reset UEFI Dell XPS 9530
[https://ubuntuforums.org/showthread.php?t=2490359](https://ubuntuforums.org/showthread.php?t=2490359)
Locked UEFI/BIOS setting: Lenovo UEFI screen
[https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg)

---

