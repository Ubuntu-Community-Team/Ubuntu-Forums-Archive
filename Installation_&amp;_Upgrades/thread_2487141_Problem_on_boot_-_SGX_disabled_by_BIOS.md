---
title: "Problem on boot - SGX disabled by BIOS"
date: 2023-05-24
forum: Installation &amp; Upgrades
---

### Post by frajolz on 2023-05-24
Hi!

I'm having problems on booting my PC with Ubuntu. It's an Acer Aspire 5, and here's the extraction from Boot Repair info:

```

boot-repair-4ppa125                                              [20230524_2239]
============================== Boot Info Summary ===============================

 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32784 of /dev/sda1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys


================================ 0 OS detected =================================


============================ Architecture/Host Info ============================

CPU architecture: 64-bit
Live-session OS is Ubuntu 64-bit (Boot-Repair-Disk 64bit 20200604, bionic, x86_64)


===================================== UEFI =====================================

BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.

efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001,0000,2001,2002,2003
Boot0000* ubuntu    HD(1,GPT,5af50e92-6f67-4ddc-83ce-ab1ae1dafebb,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0001* Linpus lite    HD(1,MBR,0x14a28c36,0x800,0xe6f800)/File(\EFI\Boot\grubx64.efi)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC



============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________


Partitions info (1/3): _________________________________________________________


Partitions info (2/3): _________________________________________________________


Partitions info (3/3): _________________________________________________________


fdisk -l (filtered): ___________________________________________________________

Disk sda: 7.2 GiB, 7751073792 bytes, 15138816 sectors
Disk identifier: 0x14a28c36
      Boot Start      End  Sectors  Size Id Type
sda1  *     2048 15138815 15136768  7.2G  c W95 FAT32 (LBA)
Disk zram0: 486.4 MiB, 510021632 bytes, 124517 sectors
Disk zram1: 486.4 MiB, 510021632 bytes, 124517 sectors
Disk zram2: 486.4 MiB, 510021632 bytes, 124517 sectors
Disk zram3: 486.4 MiB, 510021632 bytes, 124517 sectors
Disk zram4: 486.4 MiB, 510021632 bytes, 124517 sectors
Disk zram5: 486.4 MiB, 510021632 bytes, 124517 sectors
Disk zram6: 486.4 MiB, 510021632 bytes, 124517 sectors
Disk zram7: 486.4 MiB, 510021632 bytes, 124517 sectors

parted -lm (filtered): _________________________________________________________

sda:7751MB:scsi:512:512:msdos: USB DISK 2.0:;
1:1049kB:7751MB:7750MB:fat32::boot, lba;
zram5:510MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:510MB:510MB:linux-swap(v1)::;
zram3:510MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:510MB:510MB:linux-swap(v1)::;
zram1:510MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:510MB:510MB:linux-swap(v1)::;
zram6:510MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:510MB:510MB:linux-swap(v1)::;
zram4:510MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:510MB:510MB:linux-swap(v1)::;
zram2:510MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:510MB:510MB:linux-swap(v1)::;
zram0:510MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:510MB:510MB:linux-swap(v1)::;
zram7:510MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:510MB:510MB:linux-swap(v1)::;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                   
â&#8221;&#8221;â&#8221;&#8364;sda1 vfat     822B-97CB                            14a28c36-01                          BOOT-REPAIR 
zram0                                                                                                 
zram1                                                                                                 
zram2                                                                                                 
zram3                                                                                                 
zram4                                                                                                 
zram5                                                                                                 
zram6                                                                                                 
zram7                                                                                                 

df (filtered): _________________________________________________________________

        Avail Use% Mounted on
sda1     6.4G  12% /cdrom

Mount options: __________________________________________________________________

sda1   ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

====================== sda1/boot/grub/grub.cfg (filtered) ======================

Boot-Repair-Disk session
Boot-Repair-Disk session (failsafe)

========================= sda1/syslinux.cfg (filtered) =========================

DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/

==================== sda1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

================== sda1: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1


=============================== StdErr Messages ================================

File descriptor 63 (pipe:[44838]) leaked on lvs invocation. Parent PID 12247: /bin/bash

Suggested repair: ______________________________________________________________
 The default repair of the Boot-Repair utility would not act on the boot.


```

Anyone knows what to do from here?

---

### Post by idmbe on 2023-05-24
same here:
x86/cpu: SGX disabled by BIOS.

(SGX) Software Guard Extensions
that in 11th and 12th generation Intel core processors and motherboards when support that, so i don't see that effect on system at all.

---

### Post by MAFoElffen on 2023-05-25
Are you reporting that it boots... But in the boot process... Right before the Grub menu displays, that it displays a BIOS error message like the attached screenshot?

If so, in the BIOS Security section there is a checkbox that says: Intel Software Guard Extension (SGX)... Check it, to enable that.

That error should go away.

---

### Post by idmbe on 2023-05-25
> **MAFoElffen said:**
> Are you reporting that it boots... But in the boot process... Right before the Grub menu displays, that it displays a BIOS error message like the attached screenshot?

If so, in the BIOS Security section there is a checkbox that says: Intel Software Guard Extension (SGX)... Check it, to enable that.

That error should go away.

Some motherboards don't show that feature to enable or disable SGX,  like mine, so i never see that effect on system at all.

But in his case I'm not sure about that.

---

### Post by tea for one on 2023-05-25
The boot-repair report shows:- 0 (zero) OS detected.

Let's double-check some details.
Can you boot into a live (Try Ubuntu) session, open a terminal and enter:-
```
sudo parted -l
```
Please post the output (inc. the command) in code tags.

---

### Post by MAFoElffen on 2023-05-25
Let's see the hardware & BIOS info, as report by the BIOS:
```

sudo dmidecode -t 0,1,4

```

---

### Post by frajolz on 2023-05-25
There they are!

```

lubuntu@lubuntu:~$ sudo parted -l
Model:  USB DISK 2.0 (scsi)
Disk /dev/sda: 7751MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  7751MB  7750MB  primary  fat32        boot, lba




Model: Unknown (unknown)
Disk /dev/zram5: 510MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End    Size   File system     Flags
 1      0.00B  510MB  510MB  linux-swap(v1)




Model: Unknown (unknown)
Disk /dev/zram3: 510MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End    Size   File system     Flags
 1      0.00B  510MB  510MB  linux-swap(v1)




Model: Unknown (unknown)
Disk /dev/zram1: 510MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End    Size   File system     Flags
 1      0.00B  510MB  510MB  linux-swap(v1)




Model: Unknown (unknown)
Disk /dev/zram6: 510MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End    Size   File system     Flags
 1      0.00B  510MB  510MB  linux-swap(v1)




Model: Unknown (unknown)
Disk /dev/zram4: 510MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End    Size   File system     Flags
 1      0.00B  510MB  510MB  linux-swap(v1)




Model: Unknown (unknown)
Disk /dev/zram2: 510MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End    Size   File system     Flags
 1      0.00B  510MB  510MB  linux-swap(v1)




Model: Unknown (unknown)
Disk /dev/zram0: 510MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End    Size   File system     Flags
 1      0.00B  510MB  510MB  linux-swap(v1)




Model: Unknown (unknown)
Disk /dev/zram7: 510MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End    Size   File system     Flags
 1      0.00B  510MB  510MB  linux-swap(v1)




lubuntu@lubuntu:~$

```

```

lubuntu@lubuntu:~$ sudo dmidecode -t 0,1,4
# dmidecode 3.1
Getting SMBIOS data from sysfs.
SMBIOS 3.2.0 present.
# SMBIOS implementations newer than version 3.1.1 are not
# fully supported by this version of dmidecode.


Handle 0x0000, DMI type 0, 26 bytes
BIOS Information
	Vendor: Insyde Corp.
	Version: V1.22
	Release Date: 12/14/2020
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 4608 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
		Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
		5.25"/360 kB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 kB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		8042 keyboard services are supported (int 9h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
		UEFI is supported
	BIOS Revision: 1.22
	Firmware Revision: 1.9


Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Acer
	Product Name: Aspire A515-54
	Version: V1.22
	Serial Number: NXHQMAL00V146035C29Z00
	UUID: 926461E3-4957-4620-BFC2-706979A21E30
	Wake-up Type: Power Switch
	SKU Number: 0000000000000000
	Family: Aspire 5


Handle 0x0004, DMI type 4, 48 bytes
Processor Information
	Socket Designation: U3E1
	Type: Central Processor
	Family: Core i7
	Manufacturer: Intel(R) Corporation
	ID: EC 06 08 00 FF FB EB BF
	Signature: Type 0, Family 6, Model 142, Stepping 12
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (FXSAVE and FXSTOR instructions supported)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Multi-threading)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Intel(R) Core(TM) i7-10510U CPU @ 1.80GHz
	Voltage: 0.6 V
	External Clock: 100 MHz
	Max Speed: 8300 MHz
	Current Speed: 1782 MHz
	Status: Populated, Enabled
	Upgrade: <OUT OF SPEC>
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: 0x0007
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Part Number: To Be Filled By O.E.M.
	Core Count: 4
	Core Enabled: 4
	Thread Count: 8
	Characteristics:
		64-bit capable
		Multi-Core
		Hardware Thread
		Execute Protection
		Enhanced Virtualization
		Power/Performance Control


lubuntu@lubuntu:~$ 



```

Thanks a lot for your help!

---

### Post by tea for one on 2023-05-26
The output from [COLOR="#0000FF"]sudo parted -l[/COLOR] only shows your USB disk.

Can you access the UEFI settings and see if your internal disk is visible?
Many PCs have UEFI settings to de-activate various devices such as Bluetooth, Wifi, disks (sata and nvme) etc.

Even if you try and re-install, the concern is that your internal disk is unavailable.

---

### Post by frajolz on 2023-05-26
I'll send a screenshot when I get home today.

But, just to check every possibility: Is there any other indication of a possible problem on the outputs I've sent?

I remember entering the UEFI settings and seeing everything ok. But I'll double-check.

Thanks!

---

### Post by frajolz on 2023-05-26
Here are the UEFI setup images:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292293&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292294&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292295&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292296&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292297&stc=1[/IMG]

---

### Post by idmbe on 2023-05-27
Just make: TPM Disable 
Then save setting and try again, hope that will solve this for you

---

### Post by tea for one on 2023-05-27
After disabling TPM, then also:-
Disable Secure Boot (You may need supervisor privileges)
Change Sata mode to AHCI (i.e. disable RST with Optane)
Disable Fast Boot

---

### Post by frajolz on 2023-05-27
Did all that, except changing SATA mode (didn't find where to), and still getting the same initial message.

---

### Post by idmbe on 2023-05-27
For me, I don't find a reason after this except that the problem is in the ISO itself or the program used to burn it

If you try to boot from USB flash and you use windows to burn ubuntu iso to USB I recommend use this: 
[https://ubuntu.com/tutorials/install-ubuntu-desktop#3-create-a-bootable-usb-stick](https://ubuntu.com/tutorials/install-ubuntu-desktop#3-create-a-bootable-usb-stick)

Also if you can download fresh ISO then burn it with above program.

---

### Post by tea for one on 2023-05-27
> **frajolz said:**
> Did all that, except changing SATA mode (didn't find where to), 
Is this info useful:- [https://community.acer.com/en/kb/articles/13993-how-to-change-sata-mode-to-ahci](https://community.acer.com/en/kb/articles/13993-how-to-change-sata-mode-to-ahci)
> In the MAIN section of the system BIOS, select SATA Mode and switch to AHCI.
Can you see if it is there?

---

### Post by MAFoElffen on 2023-05-27
***Important***-- Do this in order, or you will break the Windows Boot process, and cause yourself to have to reinstall Windows.

First, get into Windows > Select the Search Bar in the lower left corner > Type "cmd.exe" > Right-click and choose "Run as Administrator" > Type 
```

powercfg.exe /hibernate off
bcdedit /set {default} safeboot minimal

```
The PC will reboot. As it boots, Hold down the <F2> key. Then select SCU to get into the BIOS setup.
 
For the Acer InsydeH2O BIOS... Go to Boot Menu > Boot Mode > Choose UEFI as the type. In that same menu, change the Quick Boot to disabled, and USB Boot to enabled. Press <F10> Save and Exit... 

On reboot, Hold down the <F2> key again and when the menu comes up, select <SecureBoot Option> At that BIOS Menu, disable Secure Boot, ensure Admin password is cleared. etc.
RE: [https://kb.igel.com/securitysafety/en/enabling-uefi-secure-boot-in-ud2-lx-40-2271736.html](https://kb.igel.com/securitysafety/en/enabling-uefi-secure-boot-in-ud2-lx-40-2271736.html)
[quote="tea for one"]In the MAIN section of the system BIOS, select SATA Mode and switch to AHCI. [/quote]
That should not be visible by default. There is a "Hidden Menu" there to enable/disable that feature... In the Main Information section (second tab), Press <Cntrl><S> to make the "Hidden Menu" visible... Go to SATA Mode, press <Enter> and select AHCI, instead of Intel Optane... <F10> Save and Exit.
RE: [https://community.acer.com/en/discussion/comment/924230/#Comment_924230](https://community.acer.com/en/discussion/comment/924230/#Comment_924230)

On the reboot, boot Windows (Will boot into safe mode). In safe mode, it will look for the AHCI driver and load it. Then exit Windows and reboot. (cross fingers and hold your tongue to the left. 
[I]
"If you choose to take this mission, this message will self-destruct in 20 seconds... Good Luck."[/I](Read to the tune of the Mission Impossible theme music.)

---

### Post by frajolz on 2023-05-28
> **tea for one said:**
> Is this info useful:- [https://community.acer.com/en/kb/articles/13993-how-to-change-sata-mode-to-ahci](https://community.acer.com/en/kb/articles/13993-how-to-change-sata-mode-to-ahci)

Can you see if it is there?

It worked! I dodn't know about that AHCI mode being necessary for Linux.

Thank you very much for all that help, guys. Ubuntu community is amazing.

---

### Post by tea for one on 2023-05-29
That's welcome news.
It is a nice gesture to mark the thread as solved to help other forum members/searchers.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

