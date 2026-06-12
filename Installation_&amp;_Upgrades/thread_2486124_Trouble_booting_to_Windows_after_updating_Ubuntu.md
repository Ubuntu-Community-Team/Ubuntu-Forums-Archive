---
title: "Trouble booting to Windows after updating Ubuntu"
date: 2023-04-20
forum: Installation &amp; Upgrades
---

### Post by n7tae on 2023-04-20
My Boot-Info url:

[https://paste.ubuntu.com/p/5StGJSvpVQ](https://paste.ubuntu.com/p/5StGJSvpVQ)

Thanks!

---

### Post by yancek on 2023-04-21
Line 7 of boot repair shows windows code installed in the MBR of sda with windows installed on sda2.  Line 9 of boot repair shows a windows install on mmcblk0p1.  Which version of windows is installed on these partitions?  Beginning at line 17, boot repair shows an EFI partition which appears to have only Ubuntu EFI files on it although line 80 shows an entry for windows on the EFI partition.  Lines 97-99 show that all 3 drives are GPT and it is my understanding that windows will only boot EFI on a GPT partition.

What do you mean by 'updating Ubuntu'?  Did you just do a standard update or did you do an upgrade from an earlier version of Ubuntu to a newer one?

---

### Post by n7tae on 2023-04-21
This single board computer (Odyssey J4105) originally had just the mmcblk0 with an OEM licensed Windows 10 (Home?). Then I added the nvme0 with Ubuntu 20.04.

Later, I installed the sda and put Windows 10 Pro on it with a license purchased directly from MS and erased the ntfs partition on the mmcblk0. For a couple of year, I dual booted this system: Windows 10 Pro or Ubuntu 20.04.Then I installed Mint (fresh install from usb), didn't like it and ended up with Ubuntu 23.04 (again, fresh install from USB).

The Windows 10 Pro installation at sda is what I want to repair. After the Ubuntu 23.04 install, I could no longer boot into windows.

---

### Post by oldfred on 2023-04-21
The Windows boot entry in UEFI shows a GUID that does not exist. 
Not sure if it was on another drive & overwritten.

Do you want Windows only on sda?, you would need to add an ESP to sda.
Otherwise you need a new Windows entry in UEFI and new Windows folder in ESP. You would have to use a Windows repair recovery flash drive to reinstall all the Windows boot files.

---

### Post by tea for one on 2023-04-21
> **n7tae said:**
> The Windows 10 Pro installation at sda is what I want to repair. After the Ubuntu 23.04 install, I could no longer boot into windows.
Line 269 - LegacyWindows detected. You may want to retry after deactivating the [Separate /boot/efi partition:] option

It's a bit unusual to have Windows 10 installed in Legacy mode.
Windows 10 installer would default to UEFI mode automatically?
In order to be more robust for the future, I would certainly consider backing up the Windows data and re-installing in UEFI mode.
Each disk with an ESP and each OS in UEFI mode would reduce dual boot problems.

---

### Post by oldfred on 2023-04-21
Because Boot-Repair cannot find an UEFI boot entry, it thinks it is legacy.
But drive is gpt and Windows can only be UEFI with gpt partitioned drive.

Partitioning also looks more like UEFI/gpt, but some possibility Windows was BIOS, boot partition deleted & drive converted to MBR. But that seems less likely.

---

### Post by tea for one on 2023-04-22
> **oldfred said:**
> Because Boot-Repair cannot find an UEFI boot entry, it thinks it is legacy.
Ah, I understand - I didn't know that, I took the report at face value.

Anyway, if there is a missing Windows 10 UEFI entry, then boot-repair will not be much help.
I would even doubt that Windows repair tools will be able to create a new UEFI entry from scratch.

If the OP decides to try and repair Windows using native utilities, I would advise that the Ubuntu disk is removed to prevent any unanticipated consequences.

---

### Post by n7tae on 2023-04-24
That's what I thought. Thanks for looking at this. I rebuilt my system from scratch.

---

