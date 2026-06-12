---
title: "Unable to boot Ubuntu 14.04.1 LTS"
date: 2014-10-25
forum: Installation &amp; Upgrades
---

### Post by johan5 on 2014-10-25
Hello, I'm new to this, but here goes:

I have a Sony Vaio laptop that I wanted to run only Ubuntu, so I removed Windows 8 and used a bootable USB stick to start and install Ubuntu. After doing so, I can't boot Ubuntu (or anything), other than from the USB-stick. I was told to paste the following link that I got from using the Boot-Repair tool: [http://paste.ubuntu.com/8676303/]("http://paste.ubuntu.com/8676303/")

Any help on how I can get this computer to boot would be greatly appreciated. Thank you!

---

### Post by JKyleOKC on 2014-10-26
You've been bitten by the change from conventional BIOS booting to EFI booting that Windows 8 forced upon the world. Unfortunately I'm not expert enough to walk you through the fix; OldFred is the resident expert on this problem and he apparently hasn't yet come across your message.

Use the "search" facility of the forum software to look for messages posted by "OldFred" (I don't think the search is case-sensitive) and you should find lots of his help to others with similar problems. Yours seems to be a bit different in that the Boot Repair program failed to install the correct version of the "grub" package for you. Can you boot properly if you have the USB stick in place?

I may be gone for a day or two due to some relatively minor surgery I'm having tomorrow, but if you can get OldFred's attention you'll be in the best possible hands...

---

### Post by ubfan1 on 2014-10-26
Can you use a function key (varies by machine) at power-up to select ubuntu?  On some machines you might have to select HDD, then another windows pops up and you can select ubuntu.  Looks like a good secure boot install, and without Windows, it's a non-issue if secure boot is on or off.  I do like to set up a possible fallback bootloader (on the EFI partition)/EFI/Boot -- put a copy of shimx64.efi there renamed to bootx64.efi, and the grubx64.efi.  The grub.cfg file may remain in the /EFI/ubuntu directory.  That bootloader normally will not be run, but under some error conditions (like trying to boot grubx64.efi instead of shim with secure boot on), it might run and work.

---

### Post by yancek on 2014-10-26
Ubuntu is installed in UEFI/GPT and you have the correct Ubuntu files for efi in the sda1 partition.  You might check your BIOS to verify that EFI is enabled.  I don't use it either so can't be more  specific so you will either need to wait for someone with more knowledge on UEFI comes along or google setting EFI on your specific Sone Vaio.

---

### Post by oldfred on 2014-10-26
Sony is one of those that only boot Windows as they modified UEFI.
If you have installed in UEFI boot mode:

You can probably edit ubuntu description to be Windows in UEFI or create a new /efi/Microsoft/Boot folder it that does not still exist and copy grub or shim into that and rename grubx64.efi to be bootmgfw.efi.

See choice d: for renaming UEFI boot entry using efibootmgr.
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

 Sony Vaio Pro  hard coded to only boot "Windows Boot Manager"
[http://ubuntuforums.org/showthread.php?t=2196415](http://ubuntuforums.org/showthread.php?t=2196415)
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"


This is ubfan1's suggestion which may work.
 One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )

If you do not have Windows then you can copy grub to the Microsoft folder as Windows is not using it.
[http://ubuntuforums.org/showthread.php?t=2101840&p=12440378#post12440378](http://ubuntuforums.org/showthread.php?t=2101840&p=12440378#post12440378)


If not you may have installed in CSM/BIOS mode. 
Post link to summary report to show details:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by JKyleOKC on 2014-10-27
> **oldfred said:**
> Post link to summary report to show detailsFYI he did so at the top of the thread, post #1...

---

