---
title: "Installing Ubuntu on HP EliteDesk 800 G50 Intel i7-9700"
date: 2022-03-21
forum: Installation &amp; Upgrades
---

### Post by ctrl-alt-delete on 2022-03-21
I've just purchased HP EliteDesk 800 G5 Intel i7-9700 to install Ubuntu, in theory it should work on this machine and the [https://ubuntu.com/certified/201912-27552 ]("https://ubuntu.com/certified/201912-27552")states :

> Pre-installed in some regions with a custom Ubuntu image that takes advantage of the system&#8217;s hardware features and may include additional software. Standard images of Ubuntu may not work well, or at all."


However, while there are a few posts containing issues with Network, Monitors and other issues it must be possible to install.

I plan to install the latest version

Has anyone successfully created an error free install?

Where are the custom Ubuntu images stored that work on 18.04?   I read that to get a later version of Ubuntu working one should start with the custom images and find appropriate snaps.

Any help appreciated.

---

### Post by oldfred on 2022-03-21
Is it really a g5?
HP Elitebook 840 G5 gpt issues - 
HP put a fail-safe gpt recovery into the UEFI Settings,  go into the UEFI Menu in Security -> Hard Drive Utilities -> Uncheck "Save/restore GPT System of Hard Drive"
[https://ubuntuforums.org/showthread.php?t=2436271](https://ubuntuforums.org/showthread.php?t=2436271)

You probably need UEFI update & if SSD an SSD firmware update.

HP often has an UEFI that wants to boot "Windows Boot Manager" by description. If only Ubuntu you can change description of  Ubuntu entry to be that Windows. Others boot fallback or drive entry or change boot order in UEFI settings (not UEFI boot menu). HP does not seem to recognize efibootmgr changes to boot order which grub also uses to set Ubuntu/grub as first in boot order with install or major updates.

---

### Post by ctrl-alt-delete on 2022-03-21
> **oldfred said:**
> Is it really a g5? [COLOR=#ff8c00]Yes, noticed it in the thread but not title.[/COLOR]
HP Elitebook 840 G5 gpt issues - 
HP put a fail-safe gpt recovery into the UEFI Settings,  go into the UEFI Menu in Security -> Hard Drive Utilities -> Uncheck "Save/restore GPT System of Hard Drive"
[https://ubuntuforums.org/showthread.php?t=2436271](https://ubuntuforums.org/showthread.php?t=2436271). [COLOR=#ff8c00]&#8203;Some great info from this link thanks! [/COLOR]

You probably need UEFI update & if SSD an SSD firmware update. [COLOR=#ff8c00]Would these only be available to install via Windows?  If so I will create a Windows Drive for future use and a separate Ubuntu boot drive.[/COLOR]

HP often has an UEFI that wants to boot "Windows Boot Manager" by description. If only Ubuntu you can change description of  Ubuntu entry to be that Windows. Others boot fallback or drive entry or change boot order in UEFI settings (not UEFI boot menu). HP does not seem to recognize efibootmgr changes to boot order which grub also uses to set Ubuntu/grub as first in boot order with install or major updates.

[COLOR=#ff8c00]Thanks!
[/COLOR]

---

### Post by oldfred on 2022-03-21
Better vendors now offer UEFI updates via Linux. HP just has a few now.
[https://fwupd.org/](https://fwupd.org/)
[https://github.com/fwupd/fwupd](https://github.com/fwupd/fwupd)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

Also:
HP UEFI update - extract .bin from .exe file and copy into FAT32 partition.
[https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098](https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098) & 
[https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498](https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498)

---

