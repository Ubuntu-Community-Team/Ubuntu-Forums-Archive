---
title: "GRUB problem in HP Pavilion Sleebook w/UEFI"
date: 2014-11-18
forum: Installation &amp; Upgrades
---

### Post by mirabalj on 2014-11-18
I try install elementaryOS but fail, on boot show "GRUB Minimal Bash Like", I run Boot-Repair twice but don't resolve the problem.

Can I help me? The paste of BootInfo is [http://paste.ubuntu.com/9064866/](http://paste.ubuntu.com/9064866/)

Thanks in advance.

---

### Post by oldfred on 2014-11-18
Did you overwrite Ubuntu with Elementary?
Your UEFI still shows an Ubuntu entry but you only show Elementary partition.

It loosk like at some point you tried a BIOS install as you have a non-working grub in the MBR and a bios_grub partition. 
But all your installs are UEFI and you must be consistent to always boot and install in UEFI boot mode not BIOS/CSM.

You also have an HP. They only boot Windows, so you have to do one of the many work arounds to boot anything else. Most seem to rename bootx64.efi. And it looks like that was done as you have bkpbootx64.efi which probaly was the original file and grub is now bootx64.efi. But which grub the old Ubuntu or Elementary's grub?

       [URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019
      [/URL]
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

    
Also I would turn off os-prober to remove all the HP repair entries from grub menu. I assume you can access them from UEFI menu if needed. You copy just the Windows efi boot stanza into 40_custom and turn off os-prober. The grub menu will just have Kernels & Windows.

       
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by mirabalj on 2014-11-18
Hi oldfred, months ago I install Linux Mint (don't remember how). Work fine. But have problems with wireless.

Some days ago I decided try ElementaryOS. I installed this, but it problem appeared. Mi BIOS is in Legacy Mode Disabled and Secure Boot Disabled. I need to change something?

---

### Post by oldfred on 2014-11-18
Those settings should be good, but just be sure to boot installer in UEFI mode and then Boot-Repair should reinstall grub in UEFI mode. 

If simple update does not work, then use advanced options and a full uninstall & reinstall of grub. Just make sure Internet is working as it has to download the entire grub package again.

---

### Post by mirabalj on 2014-11-21
Well, after hours of research. I found the problem. It's a bug (and other thing).

ElementaryOS point to /boot/grub/EFI/ubuntu, not to /boot/grub/EFI/elementary
[https://bugs.launchpad.net/elementaryos/+bug/1355698](https://bugs.launchpad.net/elementaryos/+bug/1355698)

Solution:
1. Boot from the same ElementaryOS Installer
2. Mount the partition with EFI's files (in my case is /dev/sda2), and enter in your mount directory.
3. Optionally **copy** [COLOR=#333333][FONT=monospace]/boot/efi/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]EFI/elementary/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]grubx64.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]efi. t[/FONT][/COLOR]o [COLOR=#333333][FONT=monospace]/boot/efi/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]EFI/ubuntu/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]grubx64.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]efi[/FONT][/COLOR]
4. Check the uuid for the partition of Elementary in the grub.cfg (this is my thing wrong), in my case pointed to other partition.
5. **Change the uuid** if is necessary in the grub.cfg (from Ubuntu EFI, not Elementary), save this.
6. Reboot and be happy. :)

Thanks for all.

---

### Post by oldfred on 2014-11-21
Was that perhaps Boot-Repair that copied it incorrectly? Or was it really Elementary's grub? Boot-Repair mostly just runs grub scripts and does very little itself.

You should file bug report.
But it may also be just this:

cat /etc/default/grub

And does this say Ubuntu or Elementary
 GRUB_DISTRIBUTOR=

---

