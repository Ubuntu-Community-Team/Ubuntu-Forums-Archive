---
title: "Ubuntu not booting on secondary SSD"
date: 2023-12-01
forum: Installation &amp; Upgrades
---

### Post by Shishimaru on 2023-12-01
Hello peeps, good day.

I have a new MSI laptop with Windows 11 running it.

I installed a "secondary" SSD and decided to have two partitions: a simple data one and another little one for Ubuntu.

I installed Ubuntu 22.04 from Live USB on the partition and GRUB on the root of the disk, believing that a simple F11 on the restart of the computer would let me choose the secondary SSD.

Fact is, the secondary SSD is not present in the list of bootable disks. It's there in the system infos, it correctly gets detected in Windows and in Ubuntu Live USB, even GParted, but not when I decide to actually choose this SSD as a boot option.

Any idea on what I should do?

Thanks in advance!

---

### Post by ubfan1 on 2023-12-01
Probably you need an EFI partition on the SSD -- these days, all the bootloaders are kept in the EFI partition, I don't know what you mean you installed grub on the root of the disk (MBR???). Then be aware of bug  [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379) Grub installs to wrong disk. 
 Do add yourself to the "Does this affect me?" list on the bug.
There are workarounds/solutions in the bug comments. Another problem is
that your host system probably will not boot without the external device (since
needed grub files are on it).

Note the problem has been fixed in Ubuntu 23.xx releases by using a different installer.  grub-install will work
and install to wherever you indicate (complicated switches so read the man page).

---

### Post by TheFu on 2023-12-01
UEFI changed how booting happens around 2011.  The days of trivially pointing the BIOS at a boot device are long over.

There should be just 1 UEFI partition inside any computer to be booted. You can have 1 HDD or 50 HDDs, there should be only one UEFI partition. Additionally, this single UEFI partition needs to know about all the installed OSes on the storage connected to the computer, so it can hand over booting (secure boot) at startup time.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for some background on MSFT's choice to use UEFI to solve their issues and mandate it onto all vendors that ship MS-Windows.
[https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot) is about SecureBoot ... another MSFT solution for a MSFT problem.

Lest people think I'm anti-MSFT ... well, I am, sorta.  MSFT had some problems and mandated an entire industry modify to help them fix their issues.  Turns out, the ideas for the fixes were good for Linux too, but things needed to change, which is why the idea of keeping Linux and MS-Windows 100% separate isn't possible any more.  There are other problems using dual-boot, but that's for you to discover on your own.  Just remember that MSFT still thinks they are the only OS on any computer and their patching assumes that, so don't be surprised if Linux is removed from the list of OSes in the boot menu after you get all this solved and it happens about once a year while you dual boot Linux with MS-Windows.

Depending on your specific hardware, you might find that running Linux or Windows inside a virtual machine to be an acceptable alternative.  I stopped dual booting around 2008 with virtual machine performance became more than good enough for my needs.  Around 2012, I moved an MS-Windows install into a VM running under Linux control and have never looked back.  If you don't do video editing or other graphics intensive work under one of the OSes, then that one should be put into a VM. The other that needs direct GPU access would run the base OS directly on the hardware.

Only you can decide what you should do.

Hopefully, some others who do use dual, quad, octo-booting will chime in with their ideas.  They've learned about these issues much more than I.  I just avoid them completely.

---

### Post by Shishimaru on 2023-12-01
Thanks! I will definitely try the newest 23.10 then. I will safely update to 24.04 later next year.

About the EFI partition, I'm 100% sure I don't have any on the secondary disk. Should I follow any guide in order to understand what to do?

I guess I should shrink my existing data partition, format, make it somehow EFI...?


EDIT: pardon me, totally missed TheFu's message and it appeared after posting this message.

---

### Post by Shishimaru on 2023-12-01
Hmm, it must be something related to EFI partition indeed.
When deciding where to install the bootloader, the disk is grey'd out.

Nevermind, this is just too weird. In 10 years, our "friends" at msoft only managed to make things even harder than what I used to do. :\

---

### Post by tea for one on 2023-12-01
> **TheFu said:**
> Hopefully, some others who do use dual, quad, octo-booting will chime in with their ideas.
Infrequent dual boot user chiming in (not to be contentious, just a different perspective)
> **TheFu said:**
> There should be just 1 UEFI partition inside any computer to be booted. You can have 1 HDD or 50 HDDs, there should be only one UEFI partition 
I have to disagree with this - let the arm-wrestling commence......
One OS per disk each with an ESP allows independent operation.
> **TheFu said:**
> so it can hand over booting (secure boot) at startup time
Windows 11 may mandate Secure Boot during installation but it still functions if Secure Boot is disabled.
More info [https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/disabling-secure-boot?view=windows-11](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/disabling-secure-boot?view=windows-11)

---

### Post by TheFu on 2023-12-01
I knew others would know more than me. Thanks for chiming in!
I assumed the OP was relatively new to UEFI and didn't think extra effort required to have 2 or 50 EFI partitions made sense.  The default is to have 1 per system, yes?

Both UEFI and SecureBoot **are** recommended by the Linux Foundation's Workstation Security Recommendations.

---

### Post by oldfred on 2023-12-01
I believe in one ESP per device/drive.
I use Kubuntu and 22.04 and even the newer versions still use the Ubiquity installer.
All my installs are now Kubuntu, desktops, external SSD, and several flash drives. Now prefer SSD for external use.
The Ubiquity installer only installs by default to first drive, usually the Windows ESP if dual boot.
But that does not work for external drives. And requires a work around.

I have a SSD external drive which I can use with my Dell 5310 laptop that has Secure boot on. But I have ESP on external drive and used same  SSD to boot on BIOS only 2006 Laptop. But had to add a BIOS boot stanza  on old systems HDD, to directly boot install, bypassing UEFI boot.

Very old bug in Ubiquity installer, supposed fixed with new installer, but I have not used that yet.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. 
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode.

If always booting external drive from same system, you have let it install boot loader to internal drive's ESP and use "ubuntu" entry. Otherwise you boot like live installer from UEFI menu and name/label of external drive.

My Dell seems to remember I am booting from external drive, so now defaults to that. I have to manually use F12 to boot Windows. Have not tried booting Windows from grub with secure boot on, yet as I rarely want Windows.
Efibootmgr on Dell shows Ubuntu as first entry now from external drive's SSD and I get grub error, as it does not auto switch to Windows entry. I do not remember changing boot order with efibootmgr, but may have?

---

### Post by tea for one on 2023-12-01
> **TheFu said:**
> I assumed the OP was relatively new to UEFI and didn't think extra effort required to have 2 or 50 EFI partitions made sense.  The default is to have 1 per system, yes?
Yes, one ESP per system provided that each OS occupies its own disk.
One OS per disk is superior to the usual dual boot of 2 systems (Windows and Ubuntu) on one disk.

When a PC has two disks, I always recommend that only the target disk is visible when installing any OS.
If the Windows disk is isolated (or removed), then a UEFI installation will automatically create an ESP.
> Both UEFI and SecureBoot **are** recommended by the Linux Foundation's Workstation Security Recommendations.
I would like to see the end of Legacy mode, if only to avoid the difficulty of helping users with mixed mode dual boot problems.
Secure Boot is undoubtedly essential in commercial environments but, speaking as a home user, I always disable it (together with TPM).

---

### Post by Shishimaru on 2023-12-01
Anyways, I just cloned the disk1 efi partition to a partition on disk2 and I resolved.

---

