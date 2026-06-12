---
title: "ubuntu 13.04 x64/windows 8 x64 dual boot"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by gmathiou4 on 2013-04-25
i have a uefi  bios motherboard.
for the installation of ubuntu 12.10 i made a mbr partition
now if i install 13.04 inin the same mbr partition i will have problem with windows 8 dual boot ?
or i must reconfigure the partition to gpt for the installation of ubuntu 13.04?

---

### Post by oldfred on 2013-04-25
If you are installing your own system, you can stay with MBR. 

The issue is that for ease of dual booting both systems need to be either UEFI or both BIOS/Legacy/CSM boot mode. You can boot if different, but have to change UEFI/BIOS boot mode each time.

And Windows only boots from gpt drives with UEFI or only UEFI from gpt drives.
Ubuntu will boot from gpt drives with BIOS or UEFI.
If MBR(msdos) you have to use BIOS mode to boot.

I would think it best just to stay with MBR, unless you do want to totally backup data, reformat and reinstall.
There are tools to convert a MBR drive to gpt, but if a bootable drive it will require a lot of reconfiguration or just about a new install anyway. I would only consider conversion on data only drive.

---

### Post by gmathiou4 on 2013-05-16
i have no problem with clean install...
so the best solution is to make the both partition gpt and reinstall ubuntu and windows with uefi mode?

---

### Post by oldfred on 2013-05-16
MBR & gpt are partitioning types or how the partitions are defined on the drive. You only have to have gpt if you have a drive or 2TB or if you want to boot with UEFI.

 MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
      
 GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

But Windows will not install in UEFI boot mode from DVD.
      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

  You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

---

