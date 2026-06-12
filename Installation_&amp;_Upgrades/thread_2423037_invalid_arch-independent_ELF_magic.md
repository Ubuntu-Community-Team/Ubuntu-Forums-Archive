---
title: "invalid arch-independent ELF magic"
date: 2019-07-16
forum: Installation &amp; Upgrades
---

### Post by ebdavison on 2019-07-16
I have a Ubuntu 18.04 install on a laptop booting in Legacy mode, not UEFI.  Ubuntu is the only OS installed and this appeared after doing an apt upgrade.  I have tried all sort of solutions including:

1. boot-repair
2. booting a rescue CD, mounting directory, chrooting to install disk, reinstalling grub-pc, running update-grub
3. re-install of Ubuntu 18.04 on top of current OS, without erasing disk to preserve home directory and this boots UNTIL I do a full apt upgrade at which point I am back to the same error message.

Occasionally, some combination of the above gets me past the ELF error at which point I get a grub rescue menu where it does not see any disks and cannot do anything else at that point except go back to the looping repair issue.

[Edit] BTW, here is a link to the boot-repair report/summary if it helps: [http://paste.ubuntu.com/p/vRvkvXMTj7/](http://paste.ubuntu.com/p/vRvkvXMTj7/)

I really do not want to format my hard drive as so many random google posts recommend as I need to preserve the home directory.

Can someone explain what this means and how to fix it for real?

---

### Post by oldfred on 2019-07-16
elf is usually related to booting in wrong boot mode, or install is BIOS and you are booting in UEFI mode or vice-versa.

Is system new enough (since 2012) to be UEFI and that is default boot mode?
If so make sure CSM/BIOS/Legacy is set as only boot mode, not even a UEFI or BIOS boot option.

Boot-Repair posts message about far from start of disk. That really only applied to old BIOS systems, not newer UEFI even if BIOS boot.  But may also apply to USB boot systems.
If that is an issue, better to have / (root) as 25 GB partition at beginning of drive & rest of drive as /home or data partition(s).

You have some older kernels, still shown. You probably can just houseclean those. If an upgrade they may not be in dpkg any more which makes it a bit more difficult to completely houseclean as files may not just be in /boot.

You are using a large flash drive? Just for installer?
Installer is now 2GB, so you only need a 4 or 8GB flash drive for installer.
My large flash drives have a full install of Ubuntu and I use grub to boot ISO directly.  A bit to set up if newer user, but allows larger flash drive to be used for both data & emergency boot.

---

### Post by ebdavison on 2019-07-16
Thanks for the reply.
The flash drive that is listed is a recovery disk (System Rescue CD) that I use to get into the system and mount the hard drive.
I have a new-ish laptop that does support UEFI but the BIOS mode is intentionally set to Legacy and when I installed from the USB install media (again with NO format to preserve /home), it did boot initially.  I do not need or want UEFI (or do I?) so I have it turned off since I am not going to be using Windows on this box.
I can clean the "old" kernels but do not know which kernel versions I should be using.  Recommendations?
Can I "move" the root partition further back on the disk and add a /boot at the beginning in a non-destructive manner?  Again, the entire goal here is to preserve the /home directory as this is/was a working box and I need that data.

---

### Post by oldfred on 2019-07-16
I always suggest UEFI with gpt partitioning. A few others in the forum still like BIOS boot. Microsoft has required vendors to install Windows in UEFI boot mode since Windows 8 released in 2012.

If you really want BIOS, I still suggest gpt partitioning. But with gpt you have to have either an ESP - efi system partition for UEFI boot or a bios_grub partition for the BIOS boot version of grub. Before I had an UEFI system, I would add both the ESP & bios_grub, so I could later move drive to a new UEFI system and just reinstall grub in UEFI mode without having to totally redo drive.

If data in home is that important, you need to have good backups. I do not see a separate /home partition, so your data is inside / (root) in /home/$USER folder. If you have good backups then any issue, system hiccup or user error is not the end of the world.
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) 
    
It looks like you have 18.04 but have a kernel upgrade. I have original kernel & do not do the rolling enablement stack updates for newer kernels. That is mostly for newer hardware that needs newer kernel for full support. You have to keep updating until 18.04.5, although 16.04 when to .6 for some issue.
       [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

---

### Post by ebdavison on 2019-07-16
Thank you very much.  I will review those links as they look quite promising.

I understand the mix of BIOS and UEFI can cause this issue but that is not my situation.

I think the bigger question is why does it boot normally for a while and then, after updating packages (and maybe a kernel?) would it start to suddenly start behaving this way with errors?  The Ubuntu installer created a perfectly happy, booting system with BIOS/Legacy and all being unchanged between install and update/break.  What breaks this?  No evidence of UEFI in the boot partition or grub config ...

As to GPT and UEFI, I will consider it.  Any way to convert this existing setup to UEFI in a lossless way?

---

### Post by oldfred on 2019-07-16
Not easy to convert. You technically can do conversion to gpt, create new ESP for UEFI boot loader, & totally reinstall grub2's UEFI version.
But often better just to totally reinstall & restore your data & applications from your backups.

I suspect some sort of interaction with UEFI/BIOS. Vendors are updating UEFI for cpu based virus and both Windows & Ubuntu have newer kernels for those issues.

Have you updated UEFI? If you do, you have to redo all the settings, you changed as it reverts to default.

Linux now has UEFI update built in for some newer models, so you might not know it updated?
       [https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

---

### Post by ebdavison on 2019-07-19
Thank you very much for all of the links for backup and explanation of what might be going on here.  Though I did not really solve my original issue and fix the grub errors, I did re-install with UEFI mode enabled on the BIOS and using the UEFI boot USB and got the install to work properly, update packages and continue to reboot without further grub issues.

---

