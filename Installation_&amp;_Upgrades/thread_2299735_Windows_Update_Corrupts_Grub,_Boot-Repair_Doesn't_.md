---
title: "Windows Update Corrupts Grub, Boot-Repair Doesn't Fix the Problem"
date: 2015-10-20
forum: Installation &amp; Upgrades
---

### Post by Zachary_Balleisen on 2015-10-20
Hi,

I have a dual-booted Lenovo Thinkpad T450 with Windows 8.1 and Ubuntu 15.4.  After a routine Windows update, Grub completely disappeared, and the system started booting straight to the Windows.  I ran Boot-Repair using a Live Disk; this failed to restore Grub to a usable condition.  The pastbin can be found at [http://paste.ubuntu.com/12786614/](http://paste.ubuntu.com/12786614/).

My Ubuntu partition has all of its files intact, so I don't think Windows Update corrupted Ubuntu itself.

Thanks ahead of time for any suggestions you may have.

Best,
Zach

---

### Post by oldfred on 2015-10-20
With UEFI, operating system can access UEFI and change some settings like Boot order. So the Windows update probably just set the UEFI boot order to have Windows first.
Can you go into UEFI and change order back to Ubuntu first?

Or was this a system that required a work around to get it to boot anything other than Windows?

---

### Post by Zachary_Balleisen on 2015-10-21
Hi Oldfred,

> [COLOR=#000000]So the Windows update probably just set the UEFI boot order to have Windows first.[/COLOR]

I checked the Boot order - Ubuntu is ahead of Windows.  Additionally, Secure Boot is disabled.  When I try to manually select Grub to load from BIOS, nothing happens.  When I select Windows or a live disk, it works fine.  For this reason, I think Grub is corrupted.

> [COLOR=#000000]Or was this a system that required a work around to get it to boot anything other than Windows?[/COLOR]

There was no major workaround, I just changed the boot order and disabled Secure Boot.

---

### Post by oldfred on 2015-10-21
I know many systems require work arounds, and Boot-Repair used to auto do one fix that renamed the Windows efi boot file making it really grub. But that is not now recommended as a Windows update overwrites the grub copy and stores just Windows boot.

If you cannot do what you did before you can create on of the other work arounds. Boot-Repair sugests the entry into Windows BCD. That is ok if primarily a Windows user as you boot into Windows & then use the one time UEFI reboot, to boot back into grub/Ubuntu.

Most copy /EFI/ubuntu into /EFI/Boot and rename shimx64.efi to bootx64.efi. The bootx64.efi is the fallback or default hard drive boot entry that all UEFI (so far) will still boot. Many UEFI will automatically add an entry if that file exists. And if it exists it probably is just another copy of Windows efi boot file. If not you can create an UEFI boot entry with efibootmgr.

Also more details in link in my signature
 [URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019

[/URL]
 T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[URL="http://ubuntuforums.org/showthread.php?t=2255746"]http://ubuntuforums.org/showthread.php?t=2255746
      [/URL]
 [SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

    [URL="http://ubuntuforums.org/showthread.php?t=2255746"]
[/URL]

[URL="http://ubuntuforums.org/showthread.php?t=2234019"]
[/URL]

---

