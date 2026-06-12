---
title: "Unable to EFI boot after Ubuntu 12.10 install (Lenovo E30)"
date: 2013-04-10
forum: Installation &amp; Upgrades
---

### Post by sirianni on 2013-04-10
After a clean install of Ubuntu 12.10 the system won’t boot. After the BIOS screen I get the message: “Error 1692: No operating system found”

I ran the ‘boot-repair’ utility without success. Here is the boot info that utility generated:

[http://paste.ubuntu.com/5695250/](http://paste.ubuntu.com/5695250/)

Everything looks correct as far as I can tell. I booted a liveCD, mounted /dev/sda1, and poked around the “EFI” directory. Everything looks correct in there also. Here is a pastebin for the commands I ran there:

[http://paste.ubuntu.com/5695339](http://paste.ubuntu.com/5695339)

Does anyone have any idea how to fix this situation? I've been through all the options in the BIOS and nothing seems to help. I noticed this message from 'boot-repair'

    "Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/grubx64.efi file"

However, I do not see any options in the BIOS startup for selecting which option to boot from.

I also tried 13.04 beta and had the same exact problem.

---

### Post by oldfred on 2013-04-10
You do have to go into UEFI and find the setting for ubuntu so it boots grub. You need to be booting in UEFI mode. At some point you did run Boot-Repair in BIOS mode as it installed syslinux (a Windows boot loader) into the protective MBR to boot in BIOS mode. That does not matter as that will never be used.

Many UEFI combine hardware boot choices & efi boot choices, but some have it separate, just like it was with BIOS.

Many have posted that UEFI remembers settings and you have to go into UEFI to change those settings. So it may still be booting the Windows efi entry? You still have the Windows efi files in the efi folder.

Someone posted this on renaming or deleting entries, you may want to remove the Windows entry.
>  Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 
And to remove entries as UEFI remembers them.
UEFI system only shows ubuntu. Delete ubuntu entry & reboot a couple of times & it resets to defaults including drives & USB ports.



I prefer to install Ubuntu into a smaller system partition of 25GB and have separate /home or data partitions. That keeps the system files closer together on hard drive.

---

