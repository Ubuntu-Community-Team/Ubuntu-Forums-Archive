---
title: "Operating not found even after boot-repair"
date: 2024-08-20
forum: Installation &amp; Upgrades
---

### Post by leavesyoucaneat on 2024-08-20
I am trying to install Ubuntu on an old laptop. It seems to install without a hitch but I'm struggling to get it to boot. I get the "operating system not found" error message on start up.
I have tried the Yann ubuntu boot-repair several times with different options, without success. I've tried manually moving the boot partition to the start of the disk as suggested by the boot-repair, but no success there either. I've tried installing LVM and without but that doesn't make a difference.

I'm not sure what else to try. I'm a bit confused by the info dump produced by the boot-repair utility it. It seems to have several suggestions for repair even after running the repair function with the suggested options ticked. Is the boot-repair utility robust anymore? It appears to run through without error.

Here is the link to the latest output from the boot-repair: [https://paste.ubuntu.com/p/Xvp37yDDMy/](https://paste.ubuntu.com/p/Xvp37yDDMy/)

Thanks in advance for any help.

---

### Post by oldfred on 2024-08-20
You have an older but UEFI capable system.
UEFI with gpt partitioning become the standard starting in 2012 when Microsoft required it for Windows 8.
Some very early UEFI do work better with BIOS boot, but usually UEFI is better.
Have you updated UEFI firmware to latest, may be old but newer than what you have.

Did you install optional proprietary drivers to support nVidia.  But some older ones are not supported with proprietary driver anymore & you use the open source Nouveau driver.

How you boot install media, is then how it installs & repairs. That is a selection in the UEFI/BIOS one time boot menu. One is clearly UEFI and one just has name/label of flash drive. Most tools to create USB installer create one that can boot in either mode. But some will create an installer that only works in one mode or the other & then UEFI boot only can offer that one mode.

But you have a selection in UEFI system settings menu on default boot mode. That can be UEFI only, CSM/Legacy/BIOS mode or sometimes a setting for either. That setting must match how you installed. And some find changing setting helps, often both mode settings needs to be the one choice or the other depending on install.

---

### Post by leavesyoucaneat on 2024-08-20
Thanks for your reply. How do I go about updating UEFI firmware? I have BIOS A05 but there is no mention of UEFI anywhere.


I installed ubuntu using a usb installer created with rufus. There was a drop down box for "target system" but the only option was BIOS/UEFI. There were no options to install UEFI.


When I installed ubuntu I ticked the box for installing proprietary drivers, if that is what you mean.

---

### Post by oldfred on 2024-08-20
If you know you have A05, go to Dell site for support for your system and see what versions are available.
You usually can download an update file into a FAT32 formatted partition that UEFI can then read.
Some require  a Windows install, or DOS CD/flash drive to install updates.

Do not know Rufus & details on how it now works. I thought it created an installer that could be UEFI or BIOS/CSM/Legacy.
Then how you boot from UEFI one time boot menu, is how it installs. System then must have default boot mode in UEFI settings, set to that mode.

Tutorial Rufus Userufus' for creative live usb (GPT - UEFI) for UEFI
[https://ubuntuforums.org/showthread.php?t=2348851](https://ubuntuforums.org/showthread.php?t=2348851)
UEFI (non CSM) options.  (CSM is BIOS emulation in UEFI.)

Yes, checking install proprietary drivers should install any that are available.

---

