---
title: "Trouble with bios_grub and multiple boot"
date: 2019-01-08
forum: Installation &amp; Upgrades
---

### Post by ronaldo176 on 2019-01-08
(English translated by google)
Initially, I installed multi boot with win10, macOS and ubuntu.
Then, for some reason I did not master, ubuntu started to request the partition with bios_grub.
So, I reduced the sda1 partition where the EFI is, by 2mb, and created the bios_grub.
Now I can no longer access the old grub that gave me access to windows and mac.

I tried several ways with boot repair; through gparted I deactivated the flag; and nothing else worked.
I searched the forum here, but I could not find identical situations.

What would happen if I resized sda1 by resuming 2mb of bios_grub?
Anyway, how can I re-access the other systems without having to format everything again?
Thank you.

My currently disk.

[ATTACH=CONFIG]282133[/ATTACH]

---

### Post by oldfred on 2019-01-08
Somewhere you switched from UEFI boot to BIOS/CSM/legacy boot.
The ESP is used for UEFI boot.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

UEFI & BIOS are not compatible. Or once you start booting in one mode from UEFI boot menu, you cannot switch. But then from UEFI boot menu you should be able to boot your UEFI systems.

    
And a bios_grub is only required for BIOS boot. Probably better to not have created it and installed grub in BIOS mode, but you should just need to boot live installer and reinstall the UEFI version of grub. Often easier with Boot-Repair, but be sure to boot Ubuntu live installer in UEFI mode. When I still booted in BIOS but knew I was soon getting an UEFI system, I added both ESP & bios_grub partition, so having both is not an issue.

May be best if someone reviews report first, as in a few cases the auto fix from Boot-Repair is not the best fix. You probably have to use its advanced mode to get a full reinstall of the UEFI version of grub anyway.
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the summary report ( not post full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ronaldo176 on 2019-01-09
Thanks, OldFred

I tried many variations on the bios of the asus h270 Pro, but only find a disk with system, in the current form, that is, hybrid with uefi and bios.

I submit the report link produced by live boot-repair:

[http://paste.ubuntu.com/p/4p6sbXTgqJ/](http://paste.ubuntu.com/p/4p6sbXTgqJ/)

---

### Post by oldfred on 2019-01-09
Is this a Mac? We do not support use of Apple on PC.

And Mac uses UEFI to boot since conversion to Intel chips.
But you show no ESP?
Several of your partitions show issues.

---

### Post by ronaldo176 on 2019-01-09
Well, in the first post I said that I have multiple systems: windows 10, Mac High Sierra and Ubuntu.
Sda1 is the EFI partition, which I reduced, and before that, I created sda7 with the bios_grub flag, due to a new version of ubuntu, if I remember correctly. And since then I no longer have a grub that presents the possibility of entering other systems, in addition, as shown in the gparted image in the first post, all partitions were classified as problematic.
Really, all I would like is to find a way to get my boot done through sda1, which boot-repair can not even mount.
I do not want to bother or make others waste time. I just want to know if there is a solution and what this solution would be, without having to reinstall everything again.
Thank you, OldFred.

---

### Post by oldfred on 2019-01-09
But if you moved the ESP sda1 to add bios_grub in front of it, then it needs chkdsk from your Windows repair disk or dosfsck from Linux.

       [http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872](http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872)
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

