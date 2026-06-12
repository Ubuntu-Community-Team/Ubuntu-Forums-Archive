---
title: "Unable to install GRUB and Ubuntu 17,04"
date: 2017-08-26
forum: Installation &amp; Upgrades
---

### Post by xeroz2 on 2017-08-26
I tried updating my Ubuntu 16.04 to Ubuntu 17.04 but failed to upgrade somewhere in the middle (I think it was either a loss of power or something).

So I burned the Ubuntu 17.04 image to a USB drive using netbootin then formatted my Toshiba Satellite's Hard Drive and attempted to install it again as I have been able to in the past with 15.04, 15.10, etc.
However after I finished installing it and rebooted, I keep getting an error with "reboot and select proper boot device", I have attempted to use boot repair (as I thought the problem may have been ubuntu) from the live sesson but in the report it told me that my MBR had no bootloader. 

I've been hacking at this all day trying to find a workaround to no avail, as all lead to the same "reboot and select proper boot device" error upon rebooting without the live USB.

My Toshiba is in UEFI mode and I keep formatting with GPT.

---

### Post by oldfred on 2017-08-27
If UEFI boot, you should not have a boot loader in the gpt partitioned drive's protective MBR.
The protective MBR is primarily for one partition table entry in effect saying drive is totally gpt, so old tools do not see an unformatted drive and reformat it.
But it can be used for BIOS boot with Ubuntu.

Normally gpt is used with UEFI and boot files are in the ESP - efi system partition which is FAT32 formatted and often first partition.

Some Toshiba's have the same issue as HP where they only boot "Windows Boot Manager" UEFI entry or a fallback or hard drive entry, but not anything else.
Did you create one of the work arounds, perhaps with an old version of Boot-Repair. Years ago Boot-Repair renamed the Windows boot entry to actually boot Ubuntu. But in dual boot systems Windows soon overwrite the modified entry and reset to only boot Windows.

You may need one of the several work arounds, best or alternative may depend on configuration.Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
 [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 
    
The work arounds are all listed in the link in my signature, if you want to read ahead.

---

