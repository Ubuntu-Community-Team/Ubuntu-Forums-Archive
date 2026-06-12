---
title: "Kubuntu installation failed (dual boot) and I can't access any operating system"
date: 2023-02-14
forum: Installation &amp; Upgrades
---

### Post by XD5mvjNh on 2023-02-14
I tried a dual boot with Windows 10 and Kubuntu. My BIOS mode was "Legacy" and my disk MBR. I prepared the free space to install Kubuntu from the Windows disk manager. I ran the installer. I made sure to use that space to create the /, /boot, /home partitions etc. I had a message asking to create an EFI partition, so I did it and assigned it 1GB. The installation process failed: it had a "fatal error" that said "unable to install GRUB in dev/sda". It restarted and opened what I think was Kubuntu Live, with a shortcut on the desktop that said "Install Kubuntu". I repeated the steps again and same error. The problem is that now I can't access any operating system. The PC boots, appears logo ASUS, black screen with the _ line and then enters the BIOS automatically. Setting boot priority for my hard drive does not change this loop. I am afraid I have corrupted the boot of my Windows. I can only access the Kubuntu installation media via my USB. I ran the Boot-repair report generator from Kubuntu Live, here it is: [https://pastebin.com/jQa9FBSP](https://pastebin.com/jQa9FBSP). Is there a way to start Windows or at least fix Grub? Any way to install Kubuntu correctly so I can access Grub and enter Windows? Or maybe try another Linux distribution that installs correctly? I'm a bit desperate...

Excuse my English, I'm using a translator.

---

### Post by tea for one on 2023-02-14
[COLOR="#0000FF"]Line 102[/COLOR] - The firmware is EFI-compatible, and is set in EFI-mode for this live-session.

Boot-repair reports that your PC is EFI compatible.
Why is your Windows 10 installed in old-fashioned Legacy mode?

My advice is probably not exactly what you want to hear, but nevertheless:-

Back up your Windows data.
Install Windows 10 in UEFI mode with GPT.
Restore your data.
Check that everything is OK and you can boot Windows 10 perfectly.

Then, return to this thread and we can help with a dual-boot of Kubuntu.

---

### Post by oldfred on 2023-02-14
Changed to smaller font.

Make sure you have good backups & a Windows repair/recovery flash drive as well as Kubuntu live installer, so you can repair either install.

You have newer UEFI system, most systems since 2012 are UEFI.
But you have Windows in BIOS/MBR configuration.
And you installed Kubuntu in UEFI boot mode. You cannot mix UEFI & BIOS on same drive.
Windows in MBR boot mode requires boot flag on its boot partition, your sda1, but UEFI requires boot flag on ESP, your sda9.
But you only can have one boot flag per drive, so use gparted on live installer & move boot flag back to sda1.
You can use Boot-Repair booted in BIOS mode or your Windows repair flash drive to restore a Windows BIOS boot loader to MBR of sda.

You may also then be able to convert your UEFI install without total reinstall to BIOS boot, just by using Boot-Repair's advanced mode when booted in BIOS mode to install grub. That should uninstall the UEFI version of grub and install grub to MBR for BIOS boot.

You have to install Ubuntu in BIOS mode & that will install grub's BIOS version to MBR of sda. You should be able to boot Windows from grub, if Windows fast start up is off. Windows may turn fast startup back on with updates, and then you have to restore Windows boot loader to MBR, temporarily as grub will not boot hibernated Windows.

One advantage of UEFI, is that both Windows & Ubuntu/grub boot loaders are in ESP - efi system partition. And from UEFI you can boot either system. So when Windows turns fast startup back on, you just boot Windows directly from UEFI boot menu, fix Windows, boot Ubuntu directly from UEFI & make Ubuntu first in boot order.

I agree with tea for one's suggestion that better backup data & reinstall Windows in UEFI boot mode. Microsoft has required vendors to install in UEFI/gpt mode since 2012. And then that avoids the issue of one MBR & one boot loader per drive.

---

### Post by XD5mvjNh on 2023-02-14
> **oldfred said:**
> And you installed Kubuntu in UEFI boot mode. You cannot mix UEFI & BIOS on same drive.
                         
Hi,  I read about this problem of mixing UEFI and BIOS. How do you  know I  have Kubuntu installed in UEFI mode? Does the report say so?  I'm a  newbie. At no time could I "configure" in which mode Kubuntu is   installed, only I loaded the installation USB and followed the   instructions. 
> **oldfred said:**
> But you only can have one boot flag per drive, so use gparted on live installer & move boot flag back to sda1.
                     
Here are my partitions in gparted. Windows is in **sda1** and **sda2**.  I don't know why sda2 appears with "0 B" used. I have  access to that  partition and all my Windows files from Dolphin. sda1 is  labeled  "System Reserved" and has hidden files (Boot, Recovery, System  Volume  Information, $WINRE_BACKUP_PARTITION.MAKER, bootmgr, BOOTNXT,   BOOTSECT.bak).

---

### Post by oldfred on 2023-02-14
If Windows fast start up is on, it sets a hibernation flag.
Then the Linux NTFS driver will not be able to write into the NTFS partition to prevent damage. And often cannot by default read partition. Normal mount is read/write, but if hibernated it can only be mounted read only.

How you boot live installer is how it installs. You cannot change UEFI boot to BIOS once system starts booting. Or vice-versa.
Most tools to create live installer create one that is both BIOS & UEFI bootable. A few only create or offer to only create a BIOS only or a UEFI only installer.
Then in UEFI boot menu, you should have two options to boot live installer. One clearly UEFI as UEFI : XXXX and other XXXX which is BIOS boot. The XXXX is often name or label of flash drive. I have no-name flash drives and they show as PMAP.

Since so many systems are now UEFI, the installer seems to want an ESP whether install is UEFI or BIOS. But ESP not used if BIOS install. And drive really should be gpt if UEFI install. But converting from MBR(msdos) to gpt usually totally erases drive, so good backups required.
UEFI install will show mount of ESP in fstab line 233, if UEFI and grub/shim boot files in ESP partition. May not be seen if report run from BIOS boot.

---

### Post by tea for one on 2023-02-14
> **marcos1520 said:**
>  How do you  know I  have Kubuntu installed in UEFI mode? Does the report say so?  I'm a  newbie. At no time could I "configure" in which mode Kubuntu is   installed, only I loaded the installation USB and followed the   instructions. 
[COLOR="#0000FF"]Line 290[/COLOR] - LegacyWindows detected. The boot of your PC is in EFI mode. You may want to retry after changing it to BIOS-compatibility/CSM/Legacy mode.
You have booted the live session in UEFI mode and created a boot-repair report.

[COLOR="#0000FF"]Line 165[/COLOR] - sda9  *    1951574016 1953523711    1949696   952M ef EFI (FAT-12/16/32)
This is an ESP created when you booted in UEFI mode.

When you boot a live USB, are you familiar with the two choices of UEFI mode and Legacy mode?
Does this screenshot help?

---

### Post by #&amp;thj^% on 2023-02-14
> **marcos1520 said:**
> How do you  know I  have Kubuntu installed in UEFI mode? Does the report say so?

This report will show you:
```
[ -d /sys/firmware/efi ] && echo "UEFI boot on HDD" || echo "Legacy boot on HDD"

```

---

### Post by XD5mvjNh on 2023-02-14
> **oldfred said:**
> If Windows fast start up is on, it sets a hibernation flag.
Then the Linux NTFS driver will not be able to write into the NTFS partition to prevent damage. And often cannot by default read partition. Normal mount is read/write, but if hibernated it can only be mounted read only.

How you boot live installer is how it installs. You cannot change UEFI boot to BIOS once system starts booting. Or vice-versa.
Most tools to create live installer create one that is both BIOS & UEFI bootable. A few only create or offer to only create a BIOS only or a UEFI only installer.
Then in UEFI boot menu, you should have two options to boot live installer. One clearly UEFI as UEFI : XXXX and other XXXX which is BIOS boot. The XXXX is often name or label of flash drive. I have no-name flash drives and they show as PMAP.

Since so many systems are now UEFI, the installer seems to want an ESP whether install is UEFI or BIOS. But ESP not used if BIOS install. And drive really should be gpt if UEFI install. But converting from MBR(msdos) to gpt usually totally erases drive, so good backups required.
UEFI install will show mount of ESP in fstab line 233, if UEFI and grub/shim boot files in ESP partition. May not be seen if report run from BIOS boot.

Thanks for the explanation, I'm understanding. I remember seeing in the boot menu that my Kubuntu installation unit was duplicated the way you explain it. Surely I select UEFI :(. Does this have to do with the fatal error "unable to install GRUB in dev/sda"? 

> **1fallen said:**
> This report will show you:
```
[ -d /sys/firmware/efi ] && echo "UEFI boot on HDD" || echo "Legacy boot on HDD"

```

Thank you for showing me this.

---

### Post by XD5mvjNh on 2023-02-14
Thank you very much for your help. I changed the boot flags as suggested by oldfred and Windows started normally. I thought it was something more serious. I still need to set up dual booting correctly (now I know the difference between UEFI and BIOS modes), but at least I know I didn't break everything.

---

### Post by oldfred on 2023-02-14
You still need to have good backups.
We all have made major mistakes, sometimes starts with a minor typo. 
But not a major issue, if you have good backups. 

Without backups you have to assume your data is not valuable.

---

