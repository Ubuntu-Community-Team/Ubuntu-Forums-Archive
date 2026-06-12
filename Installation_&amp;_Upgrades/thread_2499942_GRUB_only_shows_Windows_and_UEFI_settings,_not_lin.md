---
title: "GRUB only shows Windows and UEFI settings, not linux."
date: 2024-08-16
forum: Installation &amp; Upgrades
---

### Post by punishedyuri on 2024-08-16
Hello! I have met a dead end. 

The original situation:

I had a notebook, Lenovo Thinkpad L15, which had an NVME drive and dualboot setup, with W10 and Linux, booting into GRUB. After some updates last week and this week respecitvely, specifically the 22H2 update for the Windows 10, the computer had started booting directly into Windows 10 without asking. 

The troubleshooting that I had done allready:
 
1. I booted into Windows, turning off the fast-boot option of windows, and setting back the bootloader using: "bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi"

This made it possible to boot back into GRUB2, showing me only two options:
1. Windows Boot Manager
2. UEFI settings

No other options were available. 

2. Boot repair. Despite trying Live USB and installing boot-repair, even after the boot-repair said the repair finished succesfully, I get met with the same old criteria. 

3. Manual chrooting and update-grub. I mounted all nessesary folders, including the efi partition to /mnt/boot/efi, and running update-grub. No joy. 

At this point, I am helpless. The PC is not mine, and I would really hate to just tell the person to just reinstall it. Would be a pain, but this is as well, so idk I guess. 

So, to reiterate: PC boots to UEFI only, GRUB shows only WinBootManager, os-prober detects linux as well, boot-repair failed, update-grub is also nojoy. 

Please, if anyone has any idea on what to try, I am here waiting for help. <3 lots of love.

---

### Post by yancek on 2024-08-16
>  After some updates last week and this week respecitvely, specifically  the 22H2 update for the Windows 10, the computer had started booting  directly into Windows 10 without asking. 

Of course, windows does that on some updates and of course doesn't bother to ask or inform the user.  Standard behavior.  You should have been able to simply access the BIOS firmware and go into the Boot Options and set Ubuntu/Grub to first boot priority.

>  and setting back the bootloader using: "bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi"


So you are bootin with the windows bootloader (bcd) to an Ubuntu efi file.  Do you actually see a Grub menu as the options you show in your post are UEFI options?  You might have to reinstall Grub and then update it.  You failed to post a link to the boot repair output which they suggest you do so anything we suggest will be without any actual information and just guessing.  Run it again and post the link when it finishes.

---

### Post by oldfred on 2024-08-16
Windows updates may include UEFI firmware update.
And that can reset to UEFI defaults and Windows often turns fast startup back on and may turn Secure Boot on.
Also UEFI fast boot may then be on, not allowing time to press any key to get into UEFI settings or UEFI one time boot menu.
If UEFI Secure boot on, you need to boot with shimx64.efi, not grubx64.efi and have to have installed with the signed versions of grub & kernel.

Some Lenovo have a boot lock setting in UEFI. Check that setting.
Lenovo T450 Problem with boot repair GRUB - Boot Lock issue
[https://ubuntuforums.org/showthread.php?t=2494747](https://ubuntuforums.org/showthread.php?t=2494747)
Lenovo Locked UEFI/BIOS setting:
[https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg)

And if not those issue, post link to summary report from Boot-Repair.

---

### Post by broadcast23 on 2024-08-20
Last Tuesday update corrupted my UEFI  and grub wouldn't load, just shutdown the computer.  Reinstalled UEFI firmware all is back to normal.

---

