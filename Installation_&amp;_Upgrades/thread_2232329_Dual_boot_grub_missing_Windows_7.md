---
title: "Dual boot grub missing Windows 7"
date: 2014-07-01
forum: Installation &amp; Upgrades
---

### Post by tiger4 on 2014-07-01
I'm having a hard time to get dual boot (ubuntu 14.04-64 and windows 7 home 64) working on a Lenovo B590 laptop.

Detailed boot info here [http://paste.ubuntu.com/7730579/](http://paste.ubuntu.com/7730579/)

Summary of installation procedure and symptoms:
- Factory default started with 3 partitions (SYSTEM_DRV, Window7_OS, LENOVO_RECOVERY)
- Shrinked Windows7_OS and freed about 200GB for an extended partition, under which created ubuntu logical partitions
- Installed ubuntu 14.04-64
- After reboot grub is not working, so boot through live cd and ran boot-repair
- After reboot grub is displaying ubuntu entries but does not show Windows 7 entry; so boot into ubuntu and ran boot-repair again
- Still not showing windows7 ...

Here is content of grub menu at boot:
* Ubuntu
* Advanced option for Ubuntu
* EFI/ubuntu/MOkManager.efi
* System setup

Other things tried
- update-grub



Please let me know if there is any other information needed.
Thanks.

---

### Post by yancek on 2014-07-01
Your bootinfoscript shows the Ubuntu Grub boot code in the master boot record and also indicates the core.img file is where it should be.
If you scroll down to the grub.cfg file on sda8 where Ubuntu is, you will notice there is no entry for windows.  The standard method for fixing this is to run:  sudo os-prober, then watch the output to see if windows is detected.  If it is, run:  sudo update-grub.  I don't have much hope that this will work but it won't cause any problems so you might try it.

Other problems, sda6 shows near the top as VFAT and the EFI files are there.  Further down under drive/partition info sda6 shows as a Linux partition.

Further down in the script you see this output:
> Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootx64.efi
You can also see this at the bottom of the page and just above that an indication that there is not windows entry in grub.cfg.  os-prober might help but I haven't used EFI so you might wait for someone more familiar with it to give a suggestion.

> The boot files of [The OS now in use - Ubuntu 14.04 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)) 

---

### Post by oldfred on 2014-07-01
Your Windows looks like it is installed in BIOS boot mode.
And with BIOS boot mode drive has to be MBR which it is.
Many newer Windows 7 computers have UEFI/BIOS but boot in CSM/Legacy/BIOS boot mode. 
But then Ubuntu can be booted from installer in either boot mode which can lead to confusion.

But sda6 is an efi FAT32 partition with efi boot files. 
I thought you could only boot in UEFI mode from gpt drives as that is what UEFI expects.

Boot-Repair will convert a UEFI to BIOS or BIOS to UEFI if drive is gpt and you have correct gpt partitions. But it does not convert drive nor add partitions which you have to do inadvance.

You cannot easily convert a Windows install to UEFI on a BIOS boot computer, but it can be done. Generally better just to boot with BIOS until you decide to upgrade to a new hard drive.

You show a /boot/efi in fstab which would indicate Ubuntu is configured for UEFI boot.
Best then to use Boot-Repair to convert Ubuntu from UEFI to BIOS boot. Then you can dual boot from grub menu.

---

### Post by tiger4 on 2014-07-02
[**[COLOR=#000000]yancek[/COLOR]**]("http://ubuntuforums.org/member.php?u=1928724") and [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711"),
Thank you so much for the quick responses.
The problem was really caused by mixed boot modes (ubuntu:efi and windows 7: bios).
For some reason I thought windows was installed with EFI mode but apparently I was wrong (BTW: how did you figure out my windows was installed on BIOS mode from bootinfo?)
After I forced legacy boot (no UEFI) in BIOS setting, os-prober was able to find windows boot partition (cannot find windows before).
I did update-grub and boot-repair. Now both windows 7 and ubuntu are present in grub menu and working well.
Thanks a lot!

---

### Post by oldfred on 2014-07-02
Glad you got it working.

Windows only boots in BIOS mode from MBR drives and only boots in UEFI mode from gpt drives.
Very surprised that Ubuntu did boot in UEFI mode from MBR drive.

Also in BIOS mode Windows normally has a 100MB NTFS boot partition.
And in UEFI mode Windows uses the efi partition and has no separate boot partition. It also has to have a small system reserved unformatted partition just before the main install.

This is for gpt with UEFI. But shows you can configure for both UEFI & BIOS.
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

But if your system did boot with UEFI even though drive was MBR you could boot either way for Ubuntu only if you want to experiment. Better to have gpt partitioning.

---

