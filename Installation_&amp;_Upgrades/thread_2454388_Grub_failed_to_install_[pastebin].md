---
title: "Grub failed to install [pastebin]"
date: 2020-11-28
forum: Installation &amp; Upgrades
---

### Post by zaddy1435 on 2020-11-28
[https://paste.ubuntu.com/p/3nPBckwB95/](https://paste.ubuntu.com/p/3nPBckwB95/)

It failed at installation from Live CD.

I have Windows 10 and tried successfully after a fresh install except drivers failed to install from /cdrom/ when I installed OS from USB at this time. So I burned a DVD/Live CD because mounting etc after I googled for help on this. Since then, I fresh installed Windows again and was wanting to try Solus Budgie but it couldn't load. Ubuntu has same issues except I know where safe graphics mode is. GTX 1660 Ti is blocking normal procedure, I'm sure.

I might have luck with grub if I fresh install Windows again on this brand new SSD by the way. Crucial MX 500. I had a Kingston? 120GB ensues this upgrade of storage and speed, but I also want to dual boot to linux. Right right, instead of fresh install after so many installs already of Windows, I used Win Disk Manager to delete partitions to redo linux. I think this created the grub fail. Any thoughts or solutions to get around another install?

---

### Post by oldfred on 2020-11-28
You have UEFI system and Windows on sdb in UEFI boot mode with gpt partitioned drive.
But have old Windows boot loaders for BIOS boot in MBR of sda, sdc & sdd?

You also show no UEFI boot entries in UEFI.
Windows UEFI boot files are in ESP - efi system partition on sdb1.

You have a bios_grub on sdb4 for grub to install in BIOS boot mode to sdb's protective MBR that gpt partitioning has.
But since Windows is UEFI on sdb, you should be installing UEFI mode.

Boot-Repair also found this ( line 369):
> SFS detected.
That is Windows dynamic partitions which do not work with Linux. And is why all the error messages on sda drive.
Windows used dynamic partitions as another (proprietary) work around for the old MBR(msdos) 4 primary partition limit. Most use an extended partition and then as many logical partitions as needed. But now with gpt partitioning, there is little reason for dynamic partitions.
More info on dynamic partitions:
[https://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](https://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)

Since UEFI install of Windows, but no UEFI boot entry, was entry deleted?
If can be readded if Windows otherwise ok, or you have to run a set of Windows repairs from your Windows repair/recovery disk.

Ubuntu's Ubiquity installer in UEFI mode only installs to ESP - efi system partition on first drive. But your sda does not have an ESP.
Boot-Repair can in its advanced mode when booted in UEFI boot mode let you choose correct ESP and reinstall the UEFI version of grub.
If you have nVidia, you should have installed nvidia driver as part of install. But you can use nomodeset boot parameter to get to low quality graphics and install nVidia drive from Ubuntu repository.

Safe Graphics Boot option on installer adds nomodeset.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Shows Windows screens
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi) 

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall to correct drive. 

[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

