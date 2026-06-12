---
title: "This PC currently has no detected operating systems"
date: 2022-12-16
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-12-16
Lenovo ThinkCentre M83 running Win 11 Pro (insider build).  I have booted to USB stick with Ubuntu 21.10.  Ubuntu installation says there is NO OS on this PC.  When I try to install 21.10 on D:\ which is EXT4 and 50 GB (previously formatted with Minitool partition wizard) , the Ubuntu installer will not let me.  Why?  All partitions are GPT and UEFI boot.  I did the exact same thing on the PC I am using to post this thread, and I got none of the grief that Ubuntu is giving me now.  Are there step-by-stem instructions for the installer.  How do I make Ubuntu install where I want it to?  What are the other steps I need to take? I think boot needs to go to fat32/efi/boot and should D: get the "/".  

Thank you,

John

---

### Post by Impavidus on 2022-12-16
Ubuntu cannot detect Windows unless the filesystem is clean and properly unmounted. So make sure FastStartup is switched off in Windows and after partition changes, allow Windows to reboot so that it can run filesystem repairs.

I though Windows only assigned drive letters to partitions it understood, and normally it doesn't understand ext4. Use Windows tools to change Windows partitions, use Linux tools for the Linux partitions.

---

### Post by cigtoxdoc on 2022-12-16
I have confirmed that FAST START is off.  I have warm booted and I have cold booted and Ubuntu installation still claims "no detected operating systems" How do I fix this?

Thank you,

John

---

### Post by yancek on 2022-12-16
Not related to your problem but, 21.10 support is over and you should try using a supported version.
Have you used the Try Ubuntu option to open a terminal and manually mount the windows partition.  Run sudo fdisk -l first to determine which windows partition is the largest and what partition it is then try to mount it and see what error message you get.  If you get a message indicating the partition is in an unsafe state, it is hibernated.
Have you looked at the Power Settings options in windows?  The link below explains how to check as well as how to enable/disable it.  The 2nd link also explains it and is the actual microsoft site.

[https://www.makeuseof.com/windows-11-hibernate-enable-disable/](https://www.makeuseof.com/windows-11-hibernate-enable-disable/)

[https://learn.microsoft.com/en-us/troubleshoot/windows-client/deployment/disable-and-re-enable-hibernation](https://learn.microsoft.com/en-us/troubleshoot/windows-client/deployment/disable-and-re-enable-hibernation)

I'm surprised you show a drive letter for your Linux formatted partition as windows generally only assigns drive letter to windows partitions.

If the above steps do not resolve the problem, post back with any warning or error messages you get.  Were you having any problems with windows before you tried to install Ubuntu?  If any boot files on windows are corrupted, it won't matter what you do from Ubuntu.

---

### Post by cigtoxdoc on 2022-12-16
Perhaps I typed the wrong number, IT IS 22.10.  The following should answer some questions:

Microsoft Windows [Version 10.0.25267.1000]
(c) Microsoft Corporation. All rights reserved.

C:\Windows\System32>manage-bde -status
BitLocker Drive Encryption: Configuration Tool version 10.0.25267
Copyright (C) 2013 Microsoft Corporation. All rights reserved.

Disk volumes that can be protected with
BitLocker Drive Encryption:
Volume C: []
[OS Volume]

    Size:                 100.00 GB
    BitLocker Version:    None
    Conversion Status:    Fully Decrypted
    Percentage Encrypted: 0.0%
    Encryption Method:    None
    Protection Status:    Protection Off
    Lock Status:          Unlocked
    Identification Field: None
    Key Protectors:       None Found

Volume J: [MyDocuments]
[Data Volume]

    Size:                 90.00 GB
    BitLocker Version:    None
    Conversion Status:    Fully Decrypted
    Percentage Encrypted: 0.0%
    Encryption Method:    None
    Protection Status:    Protection Off
    Lock Status:          Unlocked
    Identification Field: None
    Automatic Unlock:     Disabled
    Key Protectors:       None Found

Volume K: [MyChemistry]
[Data Volume]

    Size:                 90.00 GB
    BitLocker Version:    None
    Conversion Status:    Fully Decrypted
    Percentage Encrypted: 0.0%
    Encryption Method:    None
    Protection Status:    Protection Off
    Lock Status:          Unlocked
    Identification Field: None
    Automatic Unlock:     Disabled
    Key Protectors:       None Found


C:\Windows\System32>

---

### Post by cigtoxdoc on 2022-12-16
Also, using FILES on the 22.10 installation USB, I was able to open PFD files there were stored under C:\windows\users\myusername.

Again, what do I need to do to install 22.10?

John

---

### Post by cigtoxdoc on 2022-12-16
PC works perfectly under Win 11.  Also, see my follow up message on using FILES from the 22.10 install USB to read files in my user area under C:\windows

---

### Post by cigtoxdoc on 2022-12-16
ADDITIONAL INFORMATION -- I tired the installation with a known, good USB stick with 22.04 LTS.  Again the same error.  Unless others know more than I do, it would imply that I have a problem with settings on the BIOS or whatever.  John

---

### Post by Impavidus on 2022-12-17
A possibly similar issue here: [https://ubuntuforums.org/showthread.php?t=2480928](https://ubuntuforums.org/showthread.php?t=2480928)

Do you use any form of RAID on Windows? Or dynamic partitions?

Maybe you can run an Ubuntu live disk and get some more details about your system: [https://ubuntuforums.org/showthread.php?t=2475931](https://ubuntuforums.org/showthread.php?t=2475931)

---

