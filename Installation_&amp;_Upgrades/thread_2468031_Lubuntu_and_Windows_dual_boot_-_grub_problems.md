---
title: "Lubuntu and Windows dual boot - grub problems"
date: 2021-10-16
forum: Installation &amp; Upgrades
---

### Post by digitronics on 2021-10-16
Have similar problems. I had Windows 7 SP1 originally installed and after installing Lubuntu 21.04, there are no possibility to boot Windows. Not even Windows own tools are capable to fix the mess. After reinstalling Windows, it's not possible to boot Lubuntu (*obviously*). Even though I would like to ditch Windows completely, I still use software that don't have any serious match in the Linux world, like raw photo and sound editing, so I'm stuck with those I have ... I also do some work related stuff in Windows, that can't be done in Linux. Have been looking at Wine and Virtual Box, but have neither time nor desire to mess with those. Virtual Box seems to be the easiest one, but discovered that it don't use correct full screen size and at best, I end up with 1024x768 on a 1920x1080 screen - correct proportions with wide black border, so no ...

At first, I used some HDD's in RAID mode 0 in Windows, but Lubuntu don't recognise the setup of those drives. Easy fix though, but time consuming, as the HDD's of concern are two 75% full 4TB disks (*photos & sound files*). In the BIOS settings, there are three HDD controller modes available for  both controllers - IDE, AHCI and RAID. I'm now using only the AHCI.

The first attempt of installing Lubuntu, it chose to install GRUB on the only HDD available on the secondary controller (*!*), which is a removable HDD (*hot plug*) - a backup disk, despite the Lubuntu disk was (*is*) located on the primary controller ... Without it, the system refuse to boot. The solution was to remove the HDD, reinstall Lubuntu and then reconnect the HDD. No HDD boot order settings in BIOS - only type order and which HDD controller to use for boot (*primary, secondary or both - only used primary, but Lubuntu ignored the settings ...)*.

Did several attempts to make it work, but GRUB[2] don't install properly - what so ever. It doesn't show up at boot, unless a 'Live' USB is used. The 'Live' version don't allow fixing the GRUB settings ... When trying to figure out what happen and after checking out advices on  the Internet, I found out that GRUB do recognise the Windows installation,  but apparently don't bother much about it. Not even after reinstalled  both Windows and Lubuntu in that specific order. Have tried the GRUB repair utility, but no change.

The motherboard is a Xeon E5 workstation type (*X10DAi*). Have also a computer with the server version (*X10DRi*), but that is only running Lubuntu, so no issues. At boot, the BIOS recognise that the shift key is pressed and reports that the related BIOS function is not supported (*Only visible for couple of seconds. Seems to be a Supermicro thing, as I've not seen it with other brands ...*)

At the moment, a workaround is to switch between two hot swap disks. One with Windows and one with Lubuntu, but in the end, that doesn't make any sense ... (*Mechanical wear and booting takes long time - over a minute, as it seems the POST process is done in a [slow] secure mode - no fast boot available.*)

---

### Post by yancek on 2021-10-16
You had windows 7 "originally" installed, what does that mean.  Did you upgrade it to 8 or 10 or is it still 7?  Windows 7 was almost always installed in Legacy/CSM mode and 8 and 10 almost always UEFI.  Which mode are you currently using with windows?  If it is a Legacy boot, you need to install Lubuntu in Legacy mode in order to boot it and windows from Grub.  If you want to boot both in Legacy mode from the windows BCD bootloader, that's possible.  Good luck with that.  

If you have windows installed in UEFI mode then it is necessary to install Lubuntu in UEFI mode if you expect to boot both from Grub.

If you haven't resolved this problem, I would suggest you get boot repair from the link below.  Use the 2nd option explained at the link below, select the Create BootInfo option in boot repair and post the link you get when it finishes here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by coffeecat on 2021-10-16
Post, and reply, moved to its own thread with new title. Please start your own threads.

---

### Post by oldfred on 2021-10-16
Since 4TB drives, you have UEFI installs.
Windows only installs in UEFI mode to gpt partitioned drives and Ubuntu should also be in UEFI boot mode.

UEFI forgets UEFI boot entry for a drive that is removed. Many UEFI auto find an UEFI entry for Windows, but not Ubuntu/grub.
But from UEFI you should be able to directly boot Ubuntu using a drive boot entry, just like you do with live installer. That entry uses /EFI/Boot/bootx64.efi which is a copy of shimx64.efi. An Ubuntu entry in UEFI for a removed drive, often is reset to something that does not work.

With both drives connected.
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by digitronics on 2021-10-16
Never mentioned Win 8.x, nor Win 10 (*those are pure crap ...*)

'Originally' means that was the first OS installed (*what else ...?*)

As I wrote, I was using it in RAID mode, but only two disks had RAID volumes.

Not UEFI, as it isn't supported by the motherboard. AHCI is.

Already tried 'Boot-repair', as mentioned ('*GRUB repair utility*' - sorry about that) and don't do anything but wasting time ...

My fault that it might not be obvious that I installed both OS's using same mode, but it is not the issue.

---

### Post by digitronics on 2021-10-16
This relates to the post I comment in, so why move it ???

---

### Post by digitronics on 2021-10-16
No, the motherboard do not use UEFI. Only AHCI.

All internal drives I have use MBR, except for my externals and hot plugs, that use GPT.

---

### Post by oldfred on 2021-10-16
So the installs are not on the 4TB drives.

UEFI is separate from AHCI.
UEFI or BIOS is how system boots. AHCI is what driver is used for drives.

Post this:
lsblk -f

---

### Post by QIII on 2022-10-23
> **digitronics said:**
> This relates to the post I comment in, so why move it ???

Because you hijacked someone else's thread to direct attention to your problem rather than theirs.

---

