---
title: "? redundant entry in efi system partition"
date: 2022-05-22
forum: Installation &amp; Upgrades
---

### Post by bingodingo on 2022-05-22
Odd problem after setting up an Ubuntu 20.04 / Windows 10 multi-boot - wondering if it's an errant entry in an EFI system partition, and if so how to fix or if not what to do.

Symptom: After a clean install of Ubuntu 20.04 onto an ssd (only one connected at the time), two boot options for Windows now appear in my UEFI bios boot screen. The (now Ubuntu) ssd previously had Windows 10. 
If I select Ubuntu in the bios it works fine; if I select the correct Windows 10 bootloader it works fine; if I select the incorrect Windows 10 bootloader, I get a diabolical looking Windows recovery screen that I promptly cancel (which I think would otherwise erase Ubuntu and mess up Windows 10 as well).

Context: 
I did a clean install of Ubuntu 20.04 onto an ssd (only one connected at the time) and selected 'Erase disk and install Ubuntu'. Fairly unremarkable install (though I bailed on 'Install third-party software ...' and 'Install updates ...'; installation was rapid without these but just seemed to hang if I chose them - a little odd as I have a good ethernet connection).

System:
i9 9900k, Radeon 6800x, Z390-AORUS-PRO-WIFI (F12 bios), 2* 500 GB SSD (each with own EFI system partition; W10 has 500 GB, Ubuntu has 200 GB on other, and 300 GB is a separate NTFS for windows), using ethernet (not wifi), hardware TPM, secure boot and other annoying bios settings OFF.

To avoid Windows v. Ubuntu conflicts, I disconnect one drive whenever doing an installation or (major) upgrade, and I choose which to boot into by going into bios on start up and selecting a boot drive.

Probably a separate question: 
The separate 300 GB partition on the Ubuntu SSD is something I'm trying for the first time - am I likely to hit problems with this when I do an upgrade down the track? 
My plan is to eventually do a clean install of 22.04.1 with the Windows drive disconnected - would that mess up the Windows (non system) partition on the Ubuntu drive (the windows EFI partition is on the other drive, only data on this Windows non system partition).

Thanks!

---

### Post by ubfan1 on 2022-05-22
I just did a Windows install, and noticed a lot of duplicate EFI entries, and duplicates on the EFI (boot selection) menu.  Going into the UEFI settings and "disabling" the second set of dups. removed them from the EFI menu.  Supposedly I could delete them, but for some reason, that didn't work, but the disable did.

---

### Post by bingodingo on 2022-05-23
Thanks ubfan. Can you point me to a simple guide on how to edit the EFI entries? I have no experience of that, though I have a reasonable amount of eperience in linux and c.
Are you suggesting Windows created the additional EFI entry? I wondered if, even though I selected 'erase disk', Ubuntu used the existing EFI partition and left the existing Windows entry alone. 
I built the Ubuntu distribution on this disk second (with the Windows disk disconnected), and then created a new, blank NTFS parition on this disk. 
It would seem a little weird for Windows to create an entry in an EFI partition for a blank NTFS partition (but I don't claim to understand the logic of Windows).

---

### Post by yancek on 2022-05-23
If you now have windows installed UEFI on another disk and you previously had windows installed on the drive on which you now have Ubuntu, that is the reason for the 2 windows entries.  When you installed Ubuntu on the previous windows drive, it did not and will not remove the UEFI entry for the old windows install.  You need to use either efibootmgr as root (sudo) to do that or do it in the BIOS firmware.  If you mount your EFI partition, you should see a directory named ubuntu containing the Ubuntu boot file.  You should also see a directory named Microsoft which contain the windows boot files for EFI.  Might try disabling or deleting one entry for windows in the BIOS firmware test booting each to make sure you get the correct (unbootable) entry.

---

### Post by bingodingo on 2022-05-23
Hi Yancek, thanks I'll try that.

---

### Post by bingodingo on 2022-05-23
I tried using efibootmgr (as root). Says entries deleted but when I reboot (as ubfan notes) the entries re-appear. 
I tried disabling the entry from within the efi bios as ubfan suggested (and clearing cmos) - it still re-appears upon booting. 
To simplify, I've done all of this with the Windows drive disconnected (so I know the entries I'm deleting are for the old / deleted windows installation).
I'm currently looking to see if there are directions on how to delete boot entries specific to this motherboard.
I have a hardware TPM, could that be relevant?
Might the Uefi bios be creating the Windows Boot Manager?
Update:
I just deleted all existing partitions for this drive / created new partitions (with the Windows drive disconnected), did a clean install and magically a Windows Boot Manager appears! when you look at the boot partition using efibootmgr, but (fingers crossed) it hasn't reappeared in the uefi bios, so, maybe, problem solved. (Perhaps it's a placeholder ubuntu uses to negotiate custom secure boot using a windows key?)
(My kids sometimes use the computer, if they boot into bios and try to change to windows and hit the wrong boot manager it's going to cause problems, so I'd really like to get rid of it.)
Any suggestions?

---

