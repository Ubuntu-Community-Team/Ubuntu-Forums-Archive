---
title: "[ boot-repair ] [ EFI ] - Issue on creation of EFI grub"
date: 2022-03-30
forum: Installation &amp; Upgrades
---

### Post by lrplrp on 2022-03-30
Hello,

I'm trying to create an UEFI partition on my drive.

I used



[LIST]
[*]On GPT disk 
[*]fresh FAT32 512mb partition, esp flag on. Take note that this EFI partition starts at sector 2048 because of the protection from MBR overwrite. Not sure if that could cause an error but better tell it here :) 
[*]purge+reinstall grub options
[*]I'm running all of this from the installation media(ubuntu-budgie 20.04) usb. Booted in UEFI itself 
[/LIST]
I fear the issue does not lie there. There may be an additional step/flag for my case which eludes me.

No matter what I try it gives the same error.


**Here's the report **[URL="https://paste.ubuntu.com/p/6VnscyC4zb/"]https://paste.ubuntu.com/p/6VnscyC4zb/
[/URL]**And the error part**

[SIZE=1]chroot /mnt/boot-sav/sdg2 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: **Cannot read EFI Boot* variables.**
grub-install: warning: read_file: could not read from file: Input/output error.
grub-install: warning: vars_get_variable: read_file(/sys/firmware/efi/vars/Boot0001-8be4df61-93ca-11d2-aa0d-00e098032b8c/raw_var) failed: Input/output error.
grub-install: warning: efi_get_variable: ops->get_variable failed: Input/output error.
grub-install: error: failed to register the EFI boot entry: Input/output error.
Exit code: 1
[/SIZE]
The popup error message:

[I][SIZE=1]An error occurred during the repair.
**Write-locked ESP. ** Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

Please write on a paper the following URL:
[https://paste.ubuntu.com/p/6VnscyC4zb/](https://paste.ubuntu.com/p/6VnscyC4zb/)


In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] 

**Locked-ESP  detected.** You may want to retry after creating a /boot/efi partition  (FAT32, 100MB~250MB, start of the disk, boot flag). This can be  performed via tools such as gParted. Then select this partition via the  [Separate /boot/efi partition:] option of [Boot Repair].[/SIZE][/I]



Thank you in advance for the answers!

---

### Post by ubfan1 on 2022-03-30
Check your UEFI setings for booting, looks like you might have booted the install media in legacy mode.  The position of the UEFI partition is not critical.  Remember, the complicated grub  install really boils down to creating directories /EFI , /EFI/ubuntu, and /EFI/Boot on the esp, and copying grubx64.efi and shimx64.efi into /EFI/ubuntu, putting a 3 line grub.cfg stub which imports the maintained /boot/grub/grub.cfg into /EFI/ubuntu, and making copies of grubx64.efi and shimx64.efi in /EFI/Boot (then rename shimx64.efi to bootx64.efi).  That should let you boot the device from the EFI boot selection menu (some key at power up).

---

### Post by oldfred on 2022-03-31
Some UEFI have settings to prevent writing into ESP for security.
It may be UEFI Secure boot, or separate setting. Or bitlocker in Windows locking all NTFS & FAT32 partitions.

Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.

Other brands may have something similar, review your manual.

---

