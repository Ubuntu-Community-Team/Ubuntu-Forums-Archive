---
title: "GRUB, EFI- ESP doesn't seem to be mounted! it must be VFAT! Aborting!"
date: 2015-01-01
forum: Installation &amp; Upgrades
---

### Post by aqk on 2015-01-01
I recently had a few problems with grub - eventually it was re-installed and its menu seems OK.
I am using both  Linux 14.04  and Windows-8. 

Whenever I attempt some sort of system change - apt-get, upgrade, update etc, I get the
following errors in the terminal:   (all packages now appear to be current). 

[B][COLOR=#800000]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up refind (0.8.4-0ppa2) ...
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.
Installing rEFInd on Linux....
The ESP doesn't seem to be mounted! Trying to find it....
// doesn't seem to be on a VFAT filesystem. The ESP must be
mounted at //boot or //boot/efi and it must be VFAT! Aborting!
dpkg: error processing package refind (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 refind
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR][/B]

 Do I really need EFI?  I am runnng an "older" mainboard and the BIOS is American Megatrends V11.6

Until I recently re-installed my GRUB, these EFI errors never happened. 
Even SYNAPTIC no longer works properly.
 Can I get rid of the EFI? If so, how?
 Or could I upgrade my above BIOS to UEFI properly? Would it even be worthwhile?

---

### Post by oldfred on 2015-01-03
Did you install Windows in BIOS boot mode?

And then why is rEFInd installed, that only works with UEFI, so that is why you are getting errors.

---

### Post by aqk on 2015-01-03
I have a Win8 (64 bit) and  Ubuntu 14.04 (64 bit) on a 1-TB drive. With 8 GB of RAM.
The BIOS is "ancient" (2008 or 2009)  pre-EFI. But the mainboard and AMD processor still kick a--. 

HD0  /sda -
sda1 - an EXT4 partition holding the Ubuntu 14.04
sda2 - Ubuntu swap
sda3 - Windows-8 NTFS - **with boot flag** .
sda4,5 - More NTFS data partitions.

As well, I have an  HD1 / sdb drive but it is basically data for various perposes, in 2 or 3 more NTFS partns.

Win-8 was installed first as a a beta a few years ago., upgraded from Win-7.
The Ubuntu was installed later - without problems  - 11.10? 12.04? 13.04? I really do not remember
It was upgraded to Ubuntu 14.04 last April.
I had NO problems with Grub **until recently**. Some problem (I forget what) caused me to do a update-grub.

Somehow the update in its wisdom, must have decided to add the UEFI subsystem, which is useless (I think!) with my old BIOS. Am I right?

Now: I would love to uninstall this rEFInd, as well as all this UEFI nonsense! Just advise me how. 
I've tried doing a re-install of GRUB, using the "legacy" version, and even done a Boot-repair two or three times.

And- there is **no such thing as "SECURE BOOT"** in my ancient (2009?) BIOS.

**The website [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)**  **[COLOR=#0000cd]"Converting Ubuntu into Legacy mode"[/COLOR]** suggests that I do a sudo boot-repair and ***3.Untick the "Separate /boot/efi partition" *** option
 There is** no such option** in the current boot-repair.
I DID find a "legacy" option which I clicked,  when I i did an apt-get install grub-pc   but theUEFI problem remains.  Are there different versions of Legacy grub?

What is grub-PC?  I had Grub 1.99 at one point, Then I think it went to 2.01. Now it appears to be 2.02.  Is 2.02 only for uEFI?

Strangely almost all my apt-gets and Synaptic stuff works, in spite of this 20 lines of rEFInd error messages, AFAIK.
 
 However, occasionally re-tuning the Grub params, such as with GRUB-CUSTOMIZE, causes the Windows entry to be lost.
And Grub-customize itself hangs.

I would be happy to find out how to un-install the UEFI and rEFInd, if any one can suggest how. 

Thanx.

---

### Post by oldfred on 2015-01-03
With that older BIOS system, you do not have any UEFI. 
So not really anything to uninstall.

But I do not know details of rEFInd to know how to uninstall it, which is needed.

Grub now has versions. The ancient grub is now grub legacy. The grub2 for BIOS is grub-pc, and grub2 for UEFI is grub-efi which now has two versions, the original 64 bit grub-efi-amd64 and a 32 bit version for some of those crippled 64 bit systems where the vendor uses a 32 bit UEFI.

If rEFInd has updated to much just uninstall it and then do a total un-install of grub-pc and reinstall of grub-pc.

---

### Post by aqk on 2015-01-06
OK-
Let's  consider this problem closed. In fact I'll close it myself.
All apt-gets and Synaptics seem to be OK, and GRUB shows the Ubuntu 64bit 14.4 upon boot.
But-  (yes the dreadful "but" again.)
Grub (and Grub update) cannot find my Win8 partition, even though it has the BOOT flag on sda3 (my Windows-8 partition)
And  sudo update-grub hangs.  I have to kill it.
So... I'll open this as another thread.

---

### Post by oldfred on 2015-01-06
Grub2's os-prober does not care about boot flag. It opens the NTFS partition and looks for the standard Windows boot files.
Often Windows 8 is hibernated, or fast boot is on. With the hibernation flag set, the Linux NTFS driver does not open NTFS partitions to prevent damage, then the prober cannot see the boot files. 

Make sure fast boot or always on hibernation of off.
Same with chkdsk. If partition needs chkdsk it will not be opened.

---

