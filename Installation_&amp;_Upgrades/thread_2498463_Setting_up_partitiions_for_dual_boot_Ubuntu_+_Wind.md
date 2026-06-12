---
title: "Setting up partitiions for dual boot Ubuntu + Windows 10"
date: 2024-06-14
forum: Installation &amp; Upgrades
---

### Post by a-g-j on 2024-06-14
Hello.

I am trying to install Ubuntu 24.04 LTS alongside Windows 10 but quite confused about the partition setup and also whether any specific BIOS settings are requried. Can you pls. help?

Disks - I have a single SSD drive with 3 primary partitions (main drive + recovery + MBR boot) used by Windows 10.
Since this is MBR (not GPT) sounds like I'd need to create a new extended partition and have one or more Linux partitions under that...

When I select Manual Installation option in Disk setup (as part of the Ubuntu installation), I face this:
- If I create a root partition using the free space, then the SSD drive is disabled under "Device for bootloader installation" dropdown (seemingly because MBR allows no more than 4 partitions)
- If I skip the root partition and first slect SSD under "Device for bootloader install", then it creates a new /boot/efi partition...and I can't create any further partitions

I am not quite sure why it creates the /boot/efi partition too, rather than update the MBR boot partition used by Windows?
Not sure if any BIOS settings too have a bearing on all this...

---

### Post by tea for one on 2024-06-14
> **a-g-j said:**
> 
I am not quite sure why it creates the /boot/efi partition too, rather than update the MBR boot partition used by Windows?
Not sure if any BIOS settings too have a bearing on all this...
Perhaps, because you booted the Ubuntu installer in UEFI mode.
When you are in a "Try Ubuntu" session, you can check the boot mode with a terminal command:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
If your PC is UEFI compatible, I would recommend that you backup your Windows data and re-install Windows in UEFI mode with GPT.

---

### Post by a-g-j on 2024-07-01
Thanks so much @tea_for_one...and sorry about the slow reply :(

It was indeed in UEFI mode! I'll try doing a Windows reinstall with GPT if possible...
There also seems to be an option to switch MBR to GPT using mbr2gpt.exe without a reinstall, though that would create a new EFI partition instead of replacing the original one
Wonder if that will all work with Ubuntu....

---

### Post by oldfred on 2024-07-01
Linux has a gdisk entry that will convert MBR to gpt or vice versa.
But both UUIDs & GUIDs change.
Best only with data only drives as there are many places in grub/ubuntu where uuid is used and even with data only drives you may need to update fstab with new uuids.
Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

If your data is backed up like it should be, then new install can be a lot easier that finding & editing the corrections needed.
And have seen one or two posts where users tried the Windows conversion & ended up just doing a re-install. But successful conversions would never post so do not know if it works or not.

---

### Post by a-g-j on 2024-07-01
Finally decided to do it the proper / straightforward way with backups + full disk clean + reinstall :)
Needed a few tries as initially Windows was reinstalling as MBR (since the BIOS setting was set to Legacy/UEFI instead of UEFI)

I was also a bit concerned about the Windows serial no / key and potentially not being able to activate it again, but seems it was linked to my microsoft account so all good :)

Thanks for all your help!

---

