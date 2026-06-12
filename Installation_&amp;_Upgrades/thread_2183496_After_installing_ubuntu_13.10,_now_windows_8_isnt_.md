---
title: "After installing ubuntu 13.10, now windows 8 isnt istalling"
date: 2013-10-25
forum: Installation &amp; Upgrades
---

### Post by Tjkhan on 2013-10-25
I had windows 8 with ubuntu 13.04. I installed 13.10 from USB. Now when i try to install the windows 8, while i select drive its says slected drive GPT so unable to install in that drive. same to all drives. what should i do now? Please help. 

little info:
500 GB HD (ubuntu installed in it)
2TB HD (Want to format NTFS for windows)

---

### Post by fantab on 2013-10-25
Are you using 32bit Ubuntu or 64bit?
If you are using EFI boot then only 64bit will install. 32bit won't install to GPT disks.

---

### Post by oldfred on 2013-10-25
I believe Windows is like Ubuntu in that it will install in UEFI or BIOS mode based on how you boot install media. Windows 7 would not install in UEFI mode from DVD only from a flash drive with extra drivers added.

Windows also has particular partition requirements with UEFI.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

If two drives make sure you install both in UEFI (or both in BIOS) otherwise dual booting is more difficult. If both UEFI then better to have an efi partition on both drives, but each install may put boot files in one. Boot-Repair can create a chain load from grub in one efi to Windows in another drive's efi partition.

More info on two drive installs in link in my signature.

---

