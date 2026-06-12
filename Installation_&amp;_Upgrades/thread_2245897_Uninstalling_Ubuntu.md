---
title: "Uninstalling Ubuntu"
date: 2014-09-26
forum: Installation &amp; Upgrades
---

### Post by zach20 on 2014-09-26
I had 8.1 on my c drive and ubuntu on my D drive. I wanted to free up space on my D drive so I heard that OS-Uninstaller works great and fixes the MBR issue.

So I made a live usb disk and had it do it's thing but now I'm unable boot into Windows. If I boot off the C drive(Which I believe is NTFS) it tells me the OS is missing. If I point it to where Ubuntu(D (GPT)) was I get broken grub line. I don't care which I use, be it windows boot or Grub to boot, as I plan to eventually put another distro on my D drive.  How can I fix this? 

FYI, My Motherboard is a z87m Gaming from MSI. It has UEFI and Legacy, or just UEFI.

---

### Post by oldfred on 2014-09-26
Is Windows installed in UEFI mode or BIOS mode?
And then was Ubuntu in UEFI or BIOS boot mode?

If drive is gpt then Windows had to be in UEFI mode as that is the only way it boots from a gpt partitioned drive.

If UEFI, you should just be able to go into UEFI menu and choose Windows.

If still an issue post this. You need Ubuntu live install and then install Boot-Repair into it.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by zach20 on 2014-09-26
Windows I think is NTFS, the C drive where it's installed. And my D Drive was GPT but it would seem that Gparted is reporting it as NTFS now as well. I am most certain Windows is installed in UEFI mode. 

As I said in my original post, I have already made a Boot-repair disk and used the OS-Uninstall program. That is what caused this issue. When I boot to the windows partition via UEFI it says Missing Operating system, also as stated in the original post.

Here is the boot info: [http://paste.ubuntu.com/8437147/](http://paste.ubuntu.com/8437147/)

---

### Post by oldfred on 2014-09-27
You have Windows in UEFI boot mode.
Windows only boots in UEFI mode from a drive that is gpt partitioned.
Gpt(GUID) and MBR(msdos) are partitioning or how drive is divided up.

NTFS is the format of your Windows partitions(s). The efi partiiton is formatted fat32. And usually Ubuntu uses ext4 for its format.

It looks like you used uninstaller in BIOS mode as it installed a Windows boot loader to the MBR for BIOS boot. That will not work. 
But you should just be able to go into your UEFI and choose or turn on UEFI mode and choose to boot Windows from boot choices menu. 

Whenever you boot your system you need to be sure you are in UEFI mode not BIOS mode.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by zach20 on 2014-09-27
And this was all gathered from my log? In my stupidity I ran the program a number of times, thinking I messed something up. This is my most recent one: paste.ubuntu.com/8437721

I have tried booting from UEFI and it looks like it's trying to load but it just gets stuck. After attempting to boot a few more times it takes me to recovery, but since I used a pirated copy of win8 to try it, I think I have limited options because half the things don't work. And i'm unable to use half the commands of bootrec such as fixmbr, in fact it doesn't even detect my windows installation.

I'm quite confused

---

### Post by zach20 on 2014-09-27
Its fine. I've accepted Ubuntu and Linux isn't ready yet for the real world outside of servers, phones and security. Just gonna accept my fate and ask lord Gates for his forgiveness and follow the righteous M$. 

Reinstallation here I come. Thankfully I know better to keep data and os separate

---

### Post by oldfred on 2014-09-27
Some others with z87 or motherboard installs.

 ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)
Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

---

