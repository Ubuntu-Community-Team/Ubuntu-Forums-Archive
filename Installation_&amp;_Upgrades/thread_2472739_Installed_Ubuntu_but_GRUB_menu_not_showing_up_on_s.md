---
title: "Installed Ubuntu but GRUB menu not showing up on startup"
date: 2022-03-10
forum: Installation &amp; Upgrades
---

### Post by rahidz on 2022-03-10
I have a PC with an SSD and HD, Windows 10. I installed Ubuntu using a USB drive. No errors.
However, my PC is still booting straight into Windows.

I am able to access Ubuntu by going into Windows -> Advanced Startup Options -> Advanced Startup -> Ubuntu, and this shows me the GRUB menu and from there I can proceed to either Windows or Ubuntu.

I have tried running boot-repair from the USB drive, which gave no errors but does not resolve the issue: [https://paste.ubuntu.com/p/SQzJnpHkCb/](https://paste.ubuntu.com/p/SQzJnpHkCb/)

Thank you for any assistance.

---

### Post by linux-sysop on 2022-03-11
This has been a very typical issue ever since Microsoft made UEFI.

**Warning!** If this doesn't work, you could end up with an invalid EFI boot, only proceed if you feel comfortable with this guide.

If you can boot into Live USB Linux, drop to terminal and run;
$lsblk

Identify the partitions, root system, efi boot, and the efi boot disk.  With a 2 disk system you will find sda and sdb.  The Linux system is identified as / and efi will read as /boot/efi.
For the follow **example**, I will pretend, the system root was found on sdb partition #2 (sdb2)  and efi boot was found on sda1. The boot disk should be where you found the efi.

[FONT=var(--ff-mono)]$ sudo apt install grub-efi
[/FONT][FONT=var(--ff-mono)]$ sudo mkdir /media/root && sudo mount /dev/**sdb2** /media/root
[/FONT][FONT=var(--ff-mono)]$ sudo mkdir /media/efi && sudo mount /dev/**sda1** /media/efi
[/FONT][FONT=var(--ff-mono)]$ sudo grub-install --target=x86_64-efi /dev/[/FONT]**sda**[FONT=var(--ff-mono)] --efi-directory=/media/efi --boot-directory=/media/root/boot[/FONT]

[FONT=var(--ff-mono)]Make certain you have the proper device IDs and[/FONT]** do not copy my example word for word**[FONT=var(--ff-mono)].  This will rewrite the grub found within the efi.  Should you find 2 boot/efi (one on each disk), then you should remove the other as you only require 1 for both OS.[/FONT]

[FONT=var(--ff-mono)]Upon return to your Linux OS after reboot, [/FONT]
[FONT=var(--ff-mono)]$ sudo update-grub [/FONT]

[FONT=var(--ff-mono)]will find your Windows OS and add it as the second choice on the grub menu.[/FONT]

[FONT=var(--ff-mono)]By the way, my [/FONT]preferred[FONT=var(--ff-mono)] method, is to install Linux OS first, then install the Windows OS.  Unfortunately many users don't want to move or back up data files from Windows to perform this method.  All my Linux OS documents are stored in a [/FONT]separate[FONT=var(--ff-mono)] partition from the OS should anything go wrong. I then use soft links to point to that partition.[/FONT]

---

### Post by tea for one on 2022-03-11
[COLOR="#0000FF"]Line 187[/COLOR] - OS#1:   Ubuntu 20.04.4 LTS on sda4
[COLOR="#0000FF"]Line 188[/COLOR] - OS#2:   Windows 10 or 11 on sdc4

As you have Ubuntu and Windows on separate disks, can you not set the Ubuntu disk (sda) to be the priority?

[COLOR="#0000FF"]Line 81 [/COLOR]- If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.

---

### Post by oldfred on 2022-03-11
It looks like each drive sda & sdc have ESP with each systems boot loader.

What brand/model system?
Many with HP, do not recognized boot order changes using efibootmgr. Grub uses efibootmgr to change boot order to have Ubuntu first.
Those HP systems then have to use UEFI settings (not UEFI boot menu) to change boot order.

Note that grub only boots working Windows.
After a Windows update it may change settings like fast start up, so grub will not boot Windows. 
And may make Windows first in boot order again.

---

### Post by rahidz on 2022-03-11
> **tea for one said:**
> [COLOR=#0000FF]Line 187[/COLOR] - OS#1:   Ubuntu 20.04.4 LTS on sda4
[COLOR=#0000FF]Line 188[/COLOR] - OS#2:   Windows 10 or 11 on sdc4

As you have Ubuntu and Windows on separate disks, can you not set the Ubuntu disk (sda) to be the priority?

[COLOR=#0000FF]Line 81 [/COLOR]- If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.

Thank you! This did the trick and was much simpler than I had assumed.

I rebooted, pressed Delete to enter my BIOS/MSI settings, then went into Settings, then Boot.
At first I tried to switch the two disks, but that gave me an error which said "Reboot and Select proper Boot device".
What I had to do instead was go into "UEFI Hard Disk Drive BBS Priorities" below that, and switch options 1 and 2 so Ubuntu was 1.

And now my PC properly boots with the GRUB menu.

---

### Post by breakdaze on 2022-03-16
@rahidz Glad you got it working. Just curious, you installed Ubuntu, did you leave all options at default?

@oldfred Is there any way to avoid this situation in which the installer creates another EFI System Partition?

---

### Post by oldfred on 2022-03-16
Installer only creates an ESP, if UEFI install and one does not exist on "first" drive.

I typically want ESP on same drive as install & have to do a work around or reinstall of grub to not have it on first drive.
I have main working install on NVMe SSD & want to keep that as default boot. Then test installs to sda drive, overwrite that default boot unless I do the work arounds.
Grub will boot all installs, but I also turn off os-prober as I now have old obsolete installs that I have not yet erased and do not want grub to find them.
It is ok to have one ESP per device. And I have seen where users have multiple FAT32 partitions. UEFI only boots from the one ESP, but grub may find boot files in other partitions.

---

