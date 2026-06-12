---
title: "Boot strategy for a Lenovo 2558?"
date: 2016-12-17
forum: Installation &amp; Upgrades
---

### Post by mjskier on 2016-12-17
Hi all,

I'm running into an issue trying to install on a Lenovo 2558. (Straight Linux, no dual booting)
I can boot from DVD, or from USB.
But if I install on the hard drive (2T), I end up with `error 1962. No operating system found`

I get the same problem with multiple installations (OpenSUSE Leap 42.2, Mint 18.1, Mint 17.3)

There is nothing in the BIOS that gives any indication about what it expects. The only control is the boot order.
BIOS: ECKT16A
Boot block rev: EC16A
This machine was built in 2012, so I'm thinking EFI, but I'm not sure (is there a way to tell?)

I have tried boot-repair-disk, but that didn't change the behavior.
[http://paste.ubuntu.com/23644318/](http://paste.ubuntu.com/23644318/)
(sdb in this report refers to the USB disk, right?)

Any suggestion?

---

### Post by oldfred on 2016-12-17
Moved to MINT sub-forum.

You have UEFI and Mint in stalled in UEFI boot mode.
Do you still have Secure Boot on in UEFI? Best to have that off.
Check other settings in UEFI.
Many systems only boot "Windows Boot Manager" by description. But do not actually check boot files. This is not allowed in UEFI standard, but multiple vendors seem to be doing this, perhaps suggested by a major operating system vendor, but that might be illegal.

       [SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715) 
            Lenovo rename files
[URL="http://ubuntuforums.org/showthread.php?t=2302170"]http://ubuntuforums.org/showthread.php?t=2302170
[/URL]
 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746) 

**A:** Manually rename files efi boot files in efi partition

 **a1**: Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu like this:
Boot0013* UEFI OS    HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\BOOT\BOOTX64.EFI)..BO
Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options.
[https://bugs.launchpad.net/boot-repair/+bug/1531178](https://bugs.launchpad.net/boot-repair/+bug/1531178)

You may have to use efibootmgr to add an entry to UEFI to boot the fallback or hard drive entry. 

Or if only Ubuntu you can usually rename boot entry of shimx64.efi.
 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by mjskier on 2016-12-18
Thanks Olfred for the quick reply.
I've tried the various suggestions from the links you provided, but this thing still gives me the no OS found.
Are the files names under the EFI directory case sensitive? 

Maybe it all boils down to that 'Secure Boot'. The BIOS doesn't show any way to tweak UEFI parameters (in fact, it doesn't show anything related to UEFI)
The only control is the boot order.

---

### Post by oldfred on 2016-12-18
If not a 32 bit UEFI boot which would not have let you install the 64 bit system, Microsoft requires the vendor to let the user turn on/off Secure boot in UEFI.

Because FAT32 is not case sensitive, I do not think UEFI is case sensitive. Windows is not case sensitive, but Linux is.

Some systems require an UEFI password to open more entries. And often the Secure Boot entry is called "Windows" or "Other". Fine print usually says if Windows 7 use "Other" as Windows 7 is not secure boot enabled.
Did you run this, and then boot the Windows entry.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

You may then have multiple Windows entries.
sudo efibootmgr -v

And you can houseclean old entries.
See 
man efibootmgr

---

