---
title: "Cannot boot from USB without using Windows"
date: 2019-02-24
forum: Installation &amp; Upgrades
---

### Post by sanctimonious on 2019-02-24
Hi all,

I am wondering if anyone can help.

What I want to achieve:

[LIST=1]
[*]Have Ubuntu installed on a USB stick to use on a laptop, but also as a portable installation, if necessary.
[*]I want my main laptop (a HP Envy 13ah) to recognise the USB is bootable and to directly boot from it, if connected, without my having to do anything else. 
[*] I do not wish to change the Windows boot partition on the local disk.
[*] (laptop is UEFI only; I intend to keep it that way. I want the USB pen drive to only work on UEFI systems, too. Not bothered about MBR)[/LIST]

What I have done:

[LIST=2]
[*]The laptop's BIOS boot sequence is set to boot from USB. A USB drive with Ubuntu 18.04 live (FAT32) boots seamlessly.
[*] I used the above USB Drive to install Ubuntu on another USB drive. I created the following partitions:
[INDENT]a. EFI partition (FAT32), 300MB [/INDENT]
[INDENT]b. ext4 partition for /, 20GB [/INDENT]
[INDENT]c. swap partition, 5GB [/INDENT]
[INDENT]d. some unallocated space, which I will later use to create another partition[/INDENT]
[*]Installation went smooth, including secure boot setup.[/LIST] 

What happens: 
[LIST=3]
[*]When attempting to start laptop from the newly installed USB pen drive, the laptop goes straight into Windows.
[*]Only way to go into the Ubuntu drive is via the "Reset this PC/ Restart dialogue in Windows 10 settings.
[/LIST]

Additional steps I took:

[LIST=4]
[*] Installed and ran boot-repair while in the new Ubuntu install. First report found an error and recommended re-installation of GRUB.
[*] Boot-repair ran cycle of repairs, but the issue was not fixed. This is the current pastebin from boot-repair: [https://paste.ubuntu.com/p/BqhT7CsCPk/](https://paste.ubuntu.com/p/BqhT7CsCPk/)[/LIST]

One of the suggestions in this log is to disable safe boot - I do not wish to do this, as this is not affecting my other USB Pen drive with the Live image.
Another suggestion in this log is to tamper with the Windows boot file. Again, I should not have to do this, as the Live  USB Pen drive can boot seamlessly just based on the BIOS boot sequence setting.

Both USB drives are the same Brand (SanDIsk) and type. Only different in size.

Any help will be appreciated.

---

