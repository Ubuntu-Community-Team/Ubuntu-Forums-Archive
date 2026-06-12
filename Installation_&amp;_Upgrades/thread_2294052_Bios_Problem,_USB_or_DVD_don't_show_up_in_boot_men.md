---
title: "Bios Problem, USB or DVD don't show up in boot menu,"
date: 2015-09-09
forum: Installation &amp; Upgrades
---

### Post by gabrielandersson18 on 2015-09-09
Hello!

I Have an ASUS R505CB laptop, bought it with windows 8 installed, i have an windows 8 upgrade key

Installed windows 10 just for testing, the system crashed and i successfully installed linux 15.04 which works just perfect
Though  i want to go back to windows 7 and have a dual boot, and i've heard  that it best to go from windows to linux in a dual boot?

And now to the problem,

i've  tried to create a bootable USB drive, burned discs with windows, but it  won't show up in bios at all. And if it shows up, i can't boot with it
Called asus and microsoft and they had no idea what to do

anyone who can help?

---

### Post by sudodus on 2015-09-09
How did you burn the DVD disk, and how did you create the USB boot drive?

- Which tools did you use?

- Look at the DVD disk and the pendrive in a working computer: Can you see several folders and files or only one big iso file?

-o-

How did you create/install the 'linux 15.04 drive'?

- Do you mean Ubuntu 15.04?

- Did you run a live session from a DVD disk or USB pendrive, or did you install it to an internal drive?

- Did you install it in UEFI mode or BIOS mode?

-o-

And finally, in order to make it possible for us to give relevant advice, please specify your computer

- Brand name and model: ASUS R505CB, but we don't know the details:
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by gabrielandersson18 on 2015-09-09
- Which tools did you use?
I used UNetbootin for the usb stick, and it is a folder with alot of files including setup and so on

And for the DVD i used Brasero
My computer is working fine with Linux 15.04 and i had a disc laying around with ubuntu linux that i used when windows crashed
i installed it on the internal drive

CPU - Intel® Core&#8482; i5-3337U CPU @ 1.80GHz × 4 
RAM - 8 GB
Graphics - Nvidia Geforce 740M 2GB GDDR3


can't find the chip, but the full computer model is "
[h=1]R505CB-XO462H[/h]

---

### Post by oldfred on 2015-09-09
Back to original question UEFI or BIOS?
If system was originally Windows 8 it was UEFI with gpt partitioning.
But Ubuntu can install to a gpt partitioned drive with UEFI or BIOS.
Windows only installs to gpt drives with UEFI.
Windows only installs to MBR drives with BIOS or if BIOS install drive must be MBR(msdos).

And Windows 7 installer is a BIOS installer unless you make some changes on flash drive to move the efi boot files to correct location. Windows 7 also does not work with secure boot on, so make sure that is off in UEFI. Windows 7 does not have the fast boot setting like Windows 8 or later, but do not turn on hibernation.

        How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)

Note major assumption that you have made backups & repair disks.
 Downgrade Windows 8 to Windows 7 BIOS/CSM/Legacy
[http://www.eightforums.com/tutorials/13326-downgrade-windows-8-windows-7-a.html](http://www.eightforums.com/tutorials/13326-downgrade-windows-8-windows-7-a.html)

---

