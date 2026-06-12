---
title: "Windows re-install; grub gone"
date: 2016-12-01
forum: Installation &amp; Upgrades
---

### Post by ssilvi on 2016-12-01
I recently had to reinstall Windows 10, and of course my GRUB bootloader was trashed in the process. I have two hybrid SSDs in my system, along with a 750GB WD HDD (/sda). The HDD does not contain any OS, it it strictly a storage drive. In my original Win 10/Ubuntu MATE 16.04 dual boot configuration (Win 10 was installed first), I remember I installed GRUB to my /sdb drive (which contains the Ubuntu OS) and could boot into the GRUB screen and select either MATE or Win 10. After re-installing Windows, the computer boots directly into Windows (/sdc)if I don't enter the BIOS settings and select the appropriate partition to boot from. If I do this, MATE boots up properly. [This]("http://paste.ubuntu.com/23562978/") link is the boot-repair-disk output before attempting the recommended repair option. [This]("http://paste.ubuntu.com/23562982/") is the output after attempting the recommended repair (which was not able repair the boot issue). Any help would be appreciated.

---

### Post by col48 on 2016-12-01
Wise to make sure you have everything essential backed up....

Look into update-grub - I'm no expert, but it could be that running this when logged into Ubuntu will provide the solution.

---

### Post by oldfred on 2016-12-01
You have a mess. :)

Once you change to UEFI with gpt partitioning you must always boot in UEFI mode and should convert all drives (at least eventually) to gpt. I started converting drives to gpt in 2011, and adding the ESP - efi system partition soon after Windows 8 which was UEFI as I knew eventually I would get new hardware with UEFI.

Your sda is dyanmic or SFS, you need to undo the dynamic and may want to consider converting to gpt as it is a bit more reliable and does not have the 4 primary partition limit.

Your sdb is MBR for BIOS boot, but sdb2 shows partition as compaq, and is most of drive. Probalby an error in partition table type.

Your sdc is gpt and shows two ESP - efi system partition. While UEFI spec allows more than one, most UEFI implementations do not work if you have more than one ESP. With gparted/parted the ESP is set (actually very long GUID) by using boot flag. But in BIOS you set which Windows partition to boot from. You cannot mix that logic as they boot flag on gpt is totally different than the BIOS boot flag.

How you boot install media UEFI or BIOS is then how it installs. If you were able to boot both systems from grub and Ubuntu was BIOS/MBR then your previous install of Windows must have been BIOS also. But sdc is now gpt with UEFI boot. If you reinstall Windows on sdc in BIOS mode it will not correctly convert from gpt to MBR. Windows will work but Linux will see it as both MBR & gpt and not see drive correctly. You can then use fixparts.

If you want to stay with UEFI/gpt, then you need to reinstall Linux on sdb in UEFI boot mode. Be sure ot backup data first. May have to fix partition type error, first. But grub only installs to ESP on drive seen as sda. But your sda is not gpt nor have an ESP, so grub fails.

I typically suggest that you have Windows drive in SATA port SATA0 or first port, and then be sure not to skip any ports. Then Windows & its ESP can be used by Ubuntu install on another drive.
Use gparted and remove boot flag from sdc4.

Make sure you have Windows fast start up or always on hibernation off.

       [http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

A am sure you will have more questions. Let us know which way you want to procede. 
If full conversion to UEFI, lots more info on UEFI in link in my signature. Best to a least skim, but it is a lot of info.

---

### Post by ssilvi on 2016-12-01
Thanks for the fast and informative reply, oldfred. Yes, I have my MATE install backed up to my 750GB HDD, so no worries if I need to re-install MATE. I've done it many times before. What I'm not clear on is the UEFI boot mode. That's a BIOS setting, isn't it? I do have an option in my BIOS to use UEFI or Legacy (other OS) boot. So, as long as I am booting my computer with UEFI, any OS installs will automatically install in that mode? BTW, if necessary, I will reinstall Win10, since I've already had to do it about fifty times already for various reasons.lol Also, thanks for the update-grub suggestion, col48. I think I tried that already but will revisit it.

---

### Post by oldfred on 2016-12-01
There are three boot modes. UEFI with Secure Boot, standard UEFI , and BIOS/Legacy/CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

But boot mode of your system and boot mode of your USB installer do not have to match. You can install in BIOS mode but have system set to boot in UEFI mode and then install does not work. Or vice-versa.  While booting system in UEFI with Secure boot will only allow Secure boot, you may not be able to boot flash drive at all without special settings or passwords as flash drive boot is not considered Secure.

How you boot install media, is then how it installs. And some systems like Dell seem to need to have legacy on, but still let you choose UEFI boot. My Asus motherboard would only let me boot flash drive in UEFI mode with Secure boot off and UEFI only setting for USB port. It has a UEFI & CSM setting that only booted in BIOS mode. So systems vary.

Generally with Secure boot off, you get two boot choices for a flash drive installer. One clearly says UEFI flash drive and other is just flash drive. Where the flash drive is the brand/name/label of the flash drive. But that choice may not match current boot mode of an actual install. Have not installed Windows but understand it works just like Ubuntu. Or you get two boot choices of flash drive and that is then how it installs.

---

### Post by ssilvi on 2016-12-01
oldfred:
OK. My Asus board is similar to yours regarding the flash drive. I've been installing Windows from a flash drive and will be sure to use the UEFI flash drive mode when re-installing. I've been installing Ubuntu from a CD-ROM and am fairly sure there's a BIOS option to use it in UEFI mode. If I decide to re-install one or both of the OSes (in UEFI mode), does it matter if Windows is installed first or second?

---

### Post by oldfred on 2016-12-01
If installing to different drives, install order should not matter.

But issues on drives can matter. Many suggest to avoid issues to only have Windows drive connected when installing Windows and only Ubuntu drive connected when installing Ubuntu.

But with UEFI, UEFI has NVRAM to remember UEFI boot entries/menu. When you disconnect a drive it forgets those. Many systems auto find new entries on a full cold boot or two, but some require efibootmgr to add entries.

And drive order or SATA port order can be important. UEFI uses GUID and Ubuntu uses UUID which should not change, but best to keep Windows in SATA port 0 and use each SATA port in order with no gaps. I have skipped ports and later had issues when plugging in a flash drive and rebooting changed other drives device entry like /dev/sdb. Flash drive filled in gap or missing port and became sdb changing all other devices. Even having DVD between drives also caused similar issues.

If you keep multiple drives connected you must have an ESP - efi system partition on the drive seen as sda or hd0 in grub. UEFI install only installs grub to sda's ESP. I have tried many times with full installs to sdb & flash drives and every time it overwrites my /EFI/ubuntu in sda's ESP.

---

### Post by Steve_Silvi on 2016-12-01
OK. I have already reinstalled Windows in UEFI mode and will attempt to re-install MATE from a Clonezilla backup I made a few days ago. Thanks for your help!

---

### Post by oldfred on 2016-12-01
If you cloned a BIOS/MBR configuration, you cannot covert to UEFI.
Better to partition to gpt and do a full install. Then restore /home and list of installed apps from your previous install.

There are tools to convert a MBR drive to gpt with gdisk. And you can add an ESP for UEFI boot or just a bios_grub for BIOS boot with gparted. And then if you have gpt and the ESP, you can run Boot-Repair to uninstall grub-pc(BIOS) and install grub-efi-amd64(UEFI).

UEFI & BIOS are not compatible. Once you start booting in one mode you cannot switch to another system in other mode. Or from grub you can only boot other installs in same boot mode.
You can dual boot only from UEFI boot menu.

---

### Post by Steve_Silvi on 2016-12-02
That's what I'll do because I'm pretty sure the cloned image is a BIOS/MBR. Thanks. BTW, the Thread Tools dropdown doesn't have a "Mark as solved" option.

---

### Post by oldfred on 2016-12-02
I see Solved. but do not know if that is because I have moderator privileges.
But official instructions show it also.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Wait until you know if it works before changing to Solved.

---

