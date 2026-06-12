---
title: "Partitioning Hard Drive in order to Dual Boot 13.10 Alongside Windows 8.1"
date: 2013-12-04
forum: Installation &amp; Upgrades
---

### Post by FeverishFenrir on 2013-12-04
As a complete newcomer to Linux, I'm trying to install Ubuntu 13.10 onto a Toshiba C55-A5386 alongside Windows 8.1. However, I'm having some difficulties. First of all, when I boot up the installer from within the Live USB, I'm only given the option of wiping the drive clean or "something else"; apparently, Ubuntu doesn't recognize Windows 8 as a valid OS. When I go to GParted to resize the partitions (which I read up on in the forums but have never actually done), I find that the four primary partitions have already been made:
[INDENT]
/dev/sda1: System, nfts, 1GB, hidden, diag
/dev/sda2: fat32, 100MB, boot
/dev/sda3: nfts, 128MB, msftres
/dev/sda4: TI106733200G, nfts, 456.38GB, msftdata (warning sign that says that some parts of this partition are unavailable because I don't have the right support package)
/dev/sda5: Recovery, nfts, 8.16GB, hidden, diag
[/INDENT]

I can resize all of these partitions except sda4, the one that I would actually like to resize. I don't know if it's safe to mess with any of the other ones, and so I can't move forward with installing Ubuntu. In addition, Firefox is not working in my Live session, so I can't download any support packages to help me out.

As the experts, do you guys know any way that I could still move forward with the installation? Or should I start over somewhere, maybe with a different version or something? I honestly have no clue what to do at this point.

Sorry if something like this has already been posted, but I've been at this for a week now and I'd just like it to work at this point. Thanks in advance for the help.

---

### Post by oldfred on 2013-12-05
You have Windows 8.1, so that will be installed with UEFI and Windows only boots with UEFI from gpt partitioned hard drives. With gpt the new limit is 128 partitions, not the 4 primary partitions that we had under MBR(msdos) partitioning.

You need to use Windows own partitioning tools to shrink Windows. And after a resize Windows has to run chkdsk and make repairs to its new size so reboot so it can fix itself.
Best to turn secure boot off.
Windows also has fast boot which really is just always on hibernation and Linux will not mount or use hibernated partitions (or partitions that need chkdsk).

Make a Windows repairCD or flash drive.
Back up your efi partition and all of Windows.

Most important instructions are here, but a lot more in links in my signature.
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you c55 is a new Haswell or Intel 4th gen chip, you may need these also:
      
 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

Turning NIC off may turn off Ethernet, but wireless may still work. You really should have Ethernet on during install but can install without it. See it then you can turn it back on after install.

---

### Post by FeverishFenrir on 2013-12-06
Turns out that I just had to partition from inside Windows and everything worked out fine. Thanks for the help!

---

