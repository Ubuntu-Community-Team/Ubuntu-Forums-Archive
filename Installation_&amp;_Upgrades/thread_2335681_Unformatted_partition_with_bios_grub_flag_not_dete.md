---
title: "Unformatted partition with bios_grub flag not detected."
date: 2016-08-31
forum: Installation &amp; Upgrades
---

### Post by tankobot on 2016-08-31
After attempting to install Ubuntu on my previously Windows computer, I was greeted by a consistent message saying "No bootable-device found." I'm now using a live-USB with boot repair to attempt to fix the issue. Boot repair first asked me to create an unformatted partition >1MB with the bios_grub flag using Gparted. I finished doing that and now the partition is 32 MiB and located at sdb3 (unformatted with flag). But, when I rerun the boot repair, it still complains that an unformatted bios_grub partition does not exist. Did I miss a step somewhere? 

Link to paste-bin of boot-info: [http://paste2.org/E3VYjzvb](http://paste2.org/E3VYjzvb) 

Thank you, Michael

---

### Post by slickymaster on 2016-08-31
*Thread moved to **Installation & Upgrades**.*

---

### Post by tankobot on 2016-08-31
It was able to complete once, while complaining about the bios being in UFI mode and not having a 250MB fat32 partition, which after being created, was still not detected. 
New info: [http://paste2.org/PgzO6eZZ](http://paste2.org/PgzO6eZZ)

---

### Post by sudodus on 2016-08-31
Welcome to the Ubuntu Forums :-)

Please tell us what you have and what you want! The more details you give us, the better. It is fine with the BootInfo output, but we can give better help if we get more information from you.

1. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

2. Please tell us

- Which version of Ubuntu did you download and flash to the USB pendrive - 16.04.1 LTS? amd64 or i386? The downloaded file name would be a good answer.

- Do you want to dual boot with Windows, or is this a linux (Ubuntu) only installation? I do not see any NTFS file system, but I ask anyway, because there were traces of Windows in the MBR in the first BootInfo output.

- Do you want to install in UEFI mode or BIOS/CSM/legacy mode?

- Where do you intend to install Ubuntu - in which drive(s) and partitions?

- Would it be an option for you to remove the (internal) drive, and keep only the drive connected, where you want to install Ubuntu (unless you want to use both drives)? It would make things easier.

- Would it be an option for you to let Ubuntu create its partition table automatically?

- You wrote 'It was able to complete once'. Where in the process did it complain about the 250MB fat32 partition - in the installer or when trying to boot into the installed system? Is the installed system booting at all - in that case, how far does the startup process continue, what can you see and hear during that process?

---

### Post by ajgreeny on 2016-08-31
Did you actually run the Boot-Repair or just create the boot-info report?

---

### Post by oldfred on 2016-08-31
You are going to have issues.

Your sda drive is MBR which is normally used with BIOS boot.
Your sdb is gpt which with Ubuntu can be either BIOS boot or UEFI boot. With Windows is could only be UEFI boot.

And you now show two ESP - efi system partitions on sdb. You should only have one per device. It shows sdb3 & sdb4 as ESP.

But main issue is that grub only installs to the ESP on sda. But your sda is MBR, so you do not have an ESP on sda. 

Choices seem to be to change sda to gpt and add an ESP.
Or install Ubuntu in BIOS boot mode on sdb, but then you must have a bios_grub unformatted 1 or 2MB partition anywhere on drive (sdb3? but is ESP also, which cannot be). Normally ESP is first or one of first partitions near start/front of drive.

Is partition on sda full of data? Or can you convert to gpt and easily add an ESP to sda?
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html) 

I might delete sda3 as it in some places says it is the ESP and in others the bios_grub. Then create new bios_grub if you want BIOS boot from sdb. And bios_grub only needs to be 1 or 2MB.

Since newer UEFI system, I might now convert sda to gpt even if you want BIOS boot from sdb.
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

