---
title: "Help with fixing Ubuntu Bootloader on invisible drive"
date: 2024-07-29
forum: Installation &amp; Upgrades
---

### Post by snowman732 on 2024-07-29
My problem actually goes beyond the bootloader, so I will explain.
I have both windows 10 and Ubuntu 22.04 installed in my PC. Windows on an SSD (256GB), Ubuntu on a HDD (512GB). I started an update to my windows and when it shut down and tried to restart to complete the update, the computer booted into Ubuntu because it is the first (default) option on the bootloader. I exited Ubuntu and went back to Windows, and the update seemed to go fine. Today I try to boot my PC but I don't see the grub menu. Instead it shows a command line "grub>_________". I could boot into Windows through safeboot, but I can't get into Ubuntu. I thought it was just an issue with the boot, so I tried to use a liveUSB (16GB) and boot-repair to fix the grub. That did not work because the place to click recommended repair did not appear. Here is the diagnostics on pastebin: [https://paste.ubuntu.com/p/yZJ4XfCdH3/](https://paste.ubuntu.com/p/yZJ4XfCdH3/)

I then tried using chroot, but then I discover that on Gparted I cannot see the HDD where my Ubuntu was installed. I can only see the SSD where the Windows is. Could this mean my HDD may be damaged and so invisible to Gparted? If it is not damaged and this issue is just with the bootloader, then how do I fix it? I've searched the forum and did not find much help on this, so I decided to make my own thread. Please help, thanks.

---

### Post by oldfred on 2024-07-29
do not think this would hide drive.
> SecureBoot enabled according to mokutil
Windows update and/or UEFI firmware update which Windows may have included, resets UEFI settings. And may turn Secure boot back on as well as Windows fast startup.
Did you install Ubuntu in UEFI Secure boot mode? Or with it off?

In UEFI settings you should show drives. Is HDD shown?
If not check connections.
If drive not seen then no software will work to try to fix it.
If seen try Smart Status.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
In Disks alias gnome-disks you can click on icon in upper right corner and see Smart Status
[https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1](https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1)
[https://ubuntuforums.org/showthread.php?t=2445397&p=13965854#post13965854](https://ubuntuforums.org/showthread.php?t=2445397&p=13965854#post13965854)

Your UEFI boot entries for both Windows & Ubuntu use same partUUID or sda1's ESP.
Often better to have separate ESP on Ubuntu only drive, but not required.

---

### Post by tea for one on 2024-07-29
[COLOR="#0000FF"]Line 55[/COLOR] - 0 (zero) OS detected
[COLOR="#0000FF"]Lines 122 -125[/COLOR] - Device sda with 4 partitions (probably Windows) is seen by boot-repair but the OS is not recognised.
When you last booted into Windows 10 , did you leave it encrypted/hibernated or something else?
> **snowman732 said:**
>  I can only see the SSD where the Windows is. Could this mean my HDD may be damaged and so invisible to Gparted? If it is not damaged and this issue is just with the bootloader, then how do I fix it?
Difficult to confirm that the Ubuntu HDD is damaged, only that it is invisible to boot-repair.
Perhaps the connection is loose, can you double check?

I would temporarily remove the Ubuntu disk and concentrate on Windows 10 first e.g.

Ensure that Windows Boot Manager is working independently of grub
Back up all Windows data
Run chkdsk/defrag and other repair utilities if required
Reboot a few times to see if Windows is in good order.

---

### Post by snowman732 on 2024-07-30
I have been using windows frequently. It was properly shutdown before the incident happened and even before the report was generated. I can still log into windows either through safe mode or if the grub option appears, i type exit command and it move over to windows. Point is that the windows is safe and works fine.

---

### Post by snowman732 on 2024-07-30
So I think the Ubuntu was installed in secure boot. I'm not certain of this, but I guess so. In the UEFI boot order, ubuntu is shown, but the name of the drive is not shown. This is unlike the USB and the SSD. What I see is this:
UEFI boot order
------------------
USB: verbatim STORE N GO 
ubuntu
SATA2: Windows boot manager
USB verbatim STORE N GO

The name of the HDD holding the Ubuntu is not visible. I now think the problem may then be with the physical drive and I should remove it and check it. What do you think?

---

### Post by snowman732 on 2024-07-30
This issue has been solved. It was never a problem with the bootloader or grub. The HDD where the Ubuntu is installed had physical connection issues with the motherboard, so the bootloader failed to launch because there was no HDD connected to the PC. The ports were cleaned, the HDD was tested for errors and reinserted back into the PC and everything works fine like expected. It was mostly a coincidence that this happened right after a windows update. I appreciate all the responses I got. Thanks.

---

