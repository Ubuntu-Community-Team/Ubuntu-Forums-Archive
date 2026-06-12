---
title: "Ubuntu 20.04.4 worked and installed before, but not now"
date: 2022-06-09
forum: Installation &amp; Upgrades
---

### Post by cpet1992 on 2022-06-09
Hello, I used to have Ubuntu 20.04.4 on my PC, and it worked no problem. I did a reinstall (or tried) to have a fresh start. It came up with a terminal error: not owned by uid 0, but by uid 999! 

On top of that, it kills the installation. I tried 22.04.4 LTS as well, same thing. Zorin OS Lite, and Core both the exact same error, and it kills the installation.

In fact, if I try to install ANY Ubuntu based distro, they all error out the same way, except Linux Lite. The issue there is that I really like the GUI and feel of Ubuntu 20/22.04.4. 

I have tried taking ownership of that which uid 999 has, no help.

I ran it in both legacy AND UEFI modes, updated BIOS, ran it in ACPI and IDE modes as well.

NOTHING works.

Please help.

---

### Post by cpet1992 on 2022-06-09
326.524486] SQUASHFS error: Failed to read block 0x!5f8ab1e8: -5
Jun 9 16:55:46 ubuntu kernel:
326.524490] SQUASHFS error: Unable to read fragmentcache entry [5f8ab1e8]
Jun 9 16:55:46 ubuntu kernel:
326.524493] SQUASHFS error: Unable to read page, block 5f8ablee8, size 4dSf
Jun 9 16:55:46 ubuntu kernel:
326.524497] SQUASHFS error: Unable to read fragment cache entrry [5f8ab1e8]
Jun 9 16:55:46 ubuntu kernel:
326.524499]
SQUASHFS error: Unable to read page, block 5f8ableB, size 4dsf
Jun 9 16:55:46 ubuntu kernel:
326.524504] SQUASHFS error: Unable to read fragment cache entry [5f8ab1e8]
Jun 9 16:55:46 ubuntu kernel:
326.524506] SQUASHFS error: Unable to read page, bloock 5f8ab1e8, size 4d5f
9 16:55:46 ubuntu kernel:
Jun

---

### Post by cpet1992 on 2022-06-09
XDG RUNTIME_DIR (/run/user/999) is not owned by us (uid 9), but byy uid 999! (This could e.g. happen if you try to connect to a non-rroot PulseA
udio as a root user, over the native protocol. Don't do tthat.)
9 17:27:53 ubuntu ubiquity[18254]: debconffilter_done: ubi usersetup.(current: ubi-usersetup)
9 17:27:53 ubuntu ubiguity[18254]: Step_before - stepUserInfo
Dun
9 17:27:54 ubuntu rtk[t-daemon[2154]: Supervising 8 threads of 3processes of 1 users.
Jun
27144 owned by '999' RT at priority S.
9 17:27:54 ubuntu rtkit-daemon[2154]: Successfully made thread 27.155 of process
Jun
users.
17:27:54 ubuntu rtkit-daemon[2154]: Supervising 9 threads off 4 processes of
9
Jun
of 1 users.
9 17:27:54 ubuntu rtkit-daemon[2154]: Supervising9 threads of 4 processes
Jun

---

### Post by cpet1992 on 2022-06-09
~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family Desktop SATA Controller (IDE mode, ports 0-3) (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family Desktop SATA Controller (IDE mode, ports 4-5) (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GP107 [GeForce GTX 1050 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GP107GL High Definition Audio Controller (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

---

### Post by cpet1992 on 2022-06-09
$ lscpu
Architecture:            x86_64
  CPU op-mode(s):        32-bit, 64-bit
  Address sizes:         36 bits physical, 48 bits virtual
  Byte Order:            Little Endian
CPU(s):                  8
  On-line CPU(s) list:   0-7
Vendor ID:               GenuineIntel
  Model name:            Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz
    CPU family:          6
    Model:               42
    Thread(s) per core:  2
    Core(s) per socket:  4
    Socket(s):           1
    Stepping:            7
    CPU max MHz:         3800.0000
    CPU min MHz:         1600.0000
    BogoMIPS:            6783.98
    Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mc
                         a cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ht 
                         tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon p
                         ebs bts rep_good nopl xtopology nonstop_tsc cpuid aperf
                         mperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est t
                         m2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcn
                         t tsc_deadline_timer aes xsave avx lahf_lm epb pti tpr_
                         shadow vnmi flexpriority ept vpid xsaveopt dtherm ida a
                         rat pln pts
Virtualization features: 
  Virtualization:        VT-x
Caches (sum of all):     
  L1d:                   128 KiB (4 instances)
  L1i:                   128 KiB (4 instances)
  L2:                    1 MiB (4 instances)
  L3:                    8 MiB (1 instance)
NUMA:                    
  NUMA node(s):          1
  NUMA node0 CPU(s):     0-7
Vulnerabilities:         
  Itlb multihit:         KVM: Mitigation: VMX disabled
  L1tf:                  Mitigation; PTE Inversion; VMX conditional cache flushe
                         s, SMT vulnerable
  Mds:                   Vulnerable: Clear CPU buffers attempted, no microcode; 
                         SMT vulnerable
  Meltdown:              Mitigation; PTI
  Spec store bypass:     Vulnerable
  Spectre v1:            Mitigation; usercopy/swapgs barriers and __user pointer
                          sanitization
  Spectre v2:            Mitigation; Retpolines, STIBP disabled, RSB filling
  Srbds:                 Not affected
  Tsx async abort:       Not affected

---

### Post by cpet1992 on 2022-06-09
If you need any more information, please let me know. Thanks in advance

---

### Post by tea for one on 2022-06-09
Do you have data backups?
Is Ubuntu the only OS on your PC?

---

### Post by cpet1992 on 2022-06-09
No backups, and windows is on my ssd but I have a separate drive for Linux. Any other linux distro will install, but I really want ubuntu

---

### Post by tea for one on 2022-06-10
First priority is to back up your important personal data from both Windows and Linux.
Then double check that you can successfully boot Windows and that Windows is operating normally.

Which version of Windows?

---

### Post by yancek on 2022-06-10
>  No backups, and windows is on my ssd but I have a separate drive for Linux.

Could you clarify that statement as windows users often refer to partitions as 'derive'.  Windows is on your SSD and you are trying to install Ubuntu on a separate physical hard drive, correct?

In addition to the version of windows you are using, is windowst a UEFI or Legacy/CSM install?  You need to boot and install Ubuntu in the same mode as windows.
Are you installing Ubuntu to the same drive/partition(s) on which it was previously installed.

---

### Post by cpet1992 on 2022-06-10
> **tea for one said:**
> First priority is to back up your important personal data from both Windows and Linux.
Then double check that you can successfully boot Windows and that Windows is operating normally.

Which version of Windows?

Windows 10, it boots and runs flawlessly. The SSD that is used for Windows 10 will not be getting touched. Neither will its storage drive. 

Ubuntu 20.04.4 used to be installed to yet another HDD all of its own.

---

### Post by cpet1992 on 2022-06-10
> **yancek said:**
> Could you clarify that statement as windows users often refer to partitions as 'derive'.  Windows is on your SSD and you are trying to install Ubuntu on a separate physical hard drive, correct?

In addition to the version of windows you are using, is windowst a UEFI or Legacy/CSM install?  You need to boot and install Ubuntu in the same mode as windows.
Are you installing Ubuntu to the same drive/partition(s) on which it was previously installed.

Nope, I say what I mean. They each have their own physical device. Windows being super heavy gets the SSD and a HDD for storage.

Linux gets it own HDD on top of the other 2.

As I said before, I have tried it in UEFI and LEGACY modes, no joy it will not work.

I know I must be doing something wrong that I didn't do before, but I have no idea what it is.

---

### Post by cpet1992 on 2022-06-10
"Are you installing Ubuntu to the same drive/partition(s) on which it was previously installed."

No, it was completely wiped, but the physical device itself is the same.

---

### Post by ajgreeny on 2022-06-10
> **cpet1992 said:**
> "Are you installing Ubuntu to the same drive/partition(s) on which it was previously installed."

No, it was completely wiped, but the physical device itself is the same.
So is there anything at all on the drive that you're trying to use for this installation?

Maybe you need to check that your downloaded .iso file and the install medium (USB) is a good one and not corrupt in some way.

Assuming you can get the live USB install disk to a full Ubuntu system you can run command ```
sudo fdisk -l
``` from that and then copy back here the output that you get.
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by tea for one on 2022-06-10
> **cpet1992 said:**
> Nope, I say what I mean. They each have their own physical device. Windows being super heavy gets the SSD and a HDD for storage.
Linux gets it own HDD on top of the other 2.
As I said before, I have tried it in UEFI and LEGACY modes, no joy it will not work.
I know I must be doing something wrong that I didn't do before, but I have no idea what it is.
Version of Windows?
Is Windows installed in UEFI mode?

---

### Post by cpet1992 on 2022-06-10
Yes sorry, Windows 10 Pro, the bios on the PC I'm currently using has no UEFI settings anywhere. I don't think it is UEFI compatible.

---

### Post by cpet1992 on 2022-06-10
> **ajgreeny said:**
> So is there anything at all on the drive that you're trying to use for this installation?

Maybe you need to check that your downloaded .iso file and the install medium (USB) is a good one and not corrupt in some way.

Assuming you can get the live USB install disk to a full Ubuntu system you can run command ```
sudo fdisk -l
``` from that and then copy back here the output that you get.
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

I will get that done, thank you.

---

### Post by cpet1992 on 2022-06-10
> **ajgreeny said:**
> So is there anything at all on the drive that you're trying to use for this installation?

Maybe you need to check that your downloaded .iso file and the install medium (USB) is a good one and not corrupt in some way.

Assuming you can get the live USB install disk to a full Ubuntu system you can run command ```
sudo fdisk -l
``` from that and then copy back here the output that you get.
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

Here is what it returns:
```
Disk /dev/sdc: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: ST500DM002-1BD14
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 81E69926-085F-429F-88F1-6593C3BBA8EA

Device      Start       End   Sectors   Size Type
/dev/sdc1    2048    616447    614400   300M EFI System
/dev/sdc2  616448    649215     32768    16M Microsoft reserved
/dev/sdc3  649216 976773119 976123904 465.5G Microsoft basic data
```

I used DiskGenius to wipe it and then added a new partition(3) the primary being formatted in Fat32.

/dev/sdc3 is just 465.5GB of empty Fat32 space. Before that i ran 4 passes completely wiping the entire disk to make sure there was no left over data. Maybe I didn't do enough passes?

PLEASE SEE BELOW, I POSTED A NEW REPLY.

---

### Post by cpet1992 on 2022-06-10
> **cpet1992 said:**
> Here is what it returns:
```
Disk /dev/sdc: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: ST500DM002-1BD14
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 81E69926-085F-429F-88F1-6593C3BBA8EA

Device      Start       End   Sectors   Size Type
/dev/sdc1    2048    616447    614400   300M EFI System
/dev/sdc2  616448    649215     32768    16M Microsoft reserved
/dev/sdc3  649216 976773119 976123904 465.5G Microsoft basic data
```

I used DiskGenius to wipe it and then added a new partition(3) the primary being formatted in Fat32.

/dev/sdc3 is just 465.5GB of empty Fat32 space. Before that i ran 4 passes completely wiping the entire disk to make sure there was no left over data. Maybe I didn't do enough passes?

Also, this would be the 3rd or 4th installation media (USB) that I have created with balenaEtcher, each with a newly downloaded .ISO every time.

---

### Post by #&amp;thj^% on 2022-06-10
I was glad to see this>> "balenaEtcher" great tool.
But I've never heard of "DiskGenius "

---

### Post by cpet1992 on 2022-06-10
I agree, it's extremely user friendly. Right down to "This USB drive has a large capacity, are you sure you want to flash it?"
Excellence

---

### Post by yancek on 2022-06-10
You were asked to post the output of the fdisk -l command for members to view.  You indicated that windows was on a separate drive from the drive you want to put Ubuntu on yet the only information you posted from fdisk was for the windows drive.  Why is that?  The information needed is for the other drive.  Also, you indicated you had no UEFI setting yet your windows hard drive has an EFI partition??

---

### Post by cpet1992 on 2022-06-10
> **1fallen said:**
> "But I've never heard of "DiskGenius "

It's a great tool as well. It's a data recovery/rescue application for Windows. You can even boot DiskGenius from a usb drive if you have a PC that won't boot and the internal drive is corrupted to attempt data recovery. It's just incredibly useful. I actually just used it to recover the OS on my son's laptop. He did a number on it, but now he's happily running his OS of choice again with all of his data. He likes Linux Lite, the only operating system based on Ubuntu (heavily or not I don't know) that would install on either one of our computers. 

Here's a link to DiskGenius:

[https://www.diskgenius.com/download.php](https://www.diskgenius.com/download.php)


It's professional grade, so there are a ton of options for you to go through.

---

### Post by cpet1992 on 2022-06-10
> **yancek said:**
> You were asked to post the output of the fdisk -l command for members to view.  You indicated that windows was on a separate drive from the drive you want to put Ubuntu on yet the only information you posted from fdisk was for the windows drive.  Why is that?  The information needed is for the other drive.  Also, you indicated you had no UEFI setting yet your windows hard drive has an EFI partition??

That's incorrect.

The drive I did the command on is an empty drive. It does not have windows on it. The Windows 10 drive (the only version/installation of Windows on my machine) is on /dev/sdb ->>> an SSD 

I can show the output for all 3 drives if that will help?

____ALSO____

Yes it has an EFI partition, however I do not see ANY UEFI settings in the BIOS. It's not under Security, there's no Secure Boot option, There's no CSM option. I'm at a loss, if it is UEFI, then they don't allow you to change the settings.

---

### Post by tea for one on 2022-06-10
I'm a bit confused too.
In post 18, you show drive sdc with 3 partitions?
Is this the target drive?

---

### Post by cpet1992 on 2022-06-10
Game Storage for Windows 10-HDD:
```
Disk /dev/sda: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: ST500DM002-1BD14
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 06C690AA-1693-4077-88AB-3187C5665582

Device      Start       End   Sectors   Size Type
/dev/sda1    2048    616447    614400   300M EFI System
/dev/sda2  616448    649215     32768    16M Microsoft reserved
/dev/sda3  649216 976773134 976123919 465.5G Microsoft basic data
```

Windows 10 System Drive -- SSD:
```
Disk /dev/sdb: 223.57 GiB, 240057409536 bytes, 468862128 sectors
Disk model: WD easystore 240
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: BDDBE7B9-4256-4EA1-8EA4-C411483E8AF5

Device         Start       End   Sectors   Size Type
/dev/sdb1       2048    206847    204800   100M EFI System
/dev/sdb2     206848    239615     32768    16M Microsoft reserved
/dev/sdb3     239616 467819695 467580080   223G Microsoft basic data
/dev/sdb4  467820544 468862094   1041551 508.6M Windows recovery environment
```

Drive I want to install Ubuntu on -- Empty HDD:
```
Disk /dev/sdc: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: ST500DM002-1BD14
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 987B7649-33D6-4CBE-93A3-201AC94547A2
```

**NOTE: **_I went ahead and deleted the Fat32 filesystem off of /dev/sdc. So it is now completely unallocated._

---

### Post by cpet1992 on 2022-06-10
> **tea for one said:**
> I'm a bit confused too.
In post 18, you show drive sdc with 3 partitions?
Is this the target drive?

Yes, sdc is the drive I wanted to install Ubuntu on. If you check out my most recent post (before this one), you'll see that I have since completely deleted all the partitions on it and that it is now just all unallocated space.

It'll be in post number 26

---

### Post by tea for one on 2022-06-10
Have you booted into an Ubuntu live session or another distro?
While in a live session, please post the output from:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```

Also, please boot into Windows and show:-
System Information > System Summary > BIOS mode > UEFI (hopefully)?

---

### Post by cpet1992 on 2022-06-10
> **tea for one said:**
> Have you booted into an Ubuntu live session or another distro?
While in a live session, please post the output from:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```

Also, please boot into Windows and show:-
System Information > System Summary > BIOS mode > UEFI (hopefully)?

In Ubuntu Live:

```
ubuntu@ubuntu:~$ [ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
UEFI mode
```

Booting into Windows now.

Windows:

BIOS: UEFI

---

### Post by tea for one on 2022-06-10
> **cpet1992 said:**
> In Ubuntu Live:
```
ubuntu@ubuntu:~$ [ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
UEFI mode
```
Booting into Windows now.

Windows:
BIOS: UEFI

Splendid – Windows 10 in UEFI mode (as it should be)

Power off PC
De-activate, isolate (via UEFI settings) or physically remove the two Windows disks
(This is advisable to try and avoid future Windows boot problems - either OS can be booted via your UEFI one-time boot menu)
Boot into Ubuntu live session in UEFI mode (very important)
Only your target disk should be accessible
Your disk is already GPT
Allow the installer to create the partitions and install Ubuntu 22.04

Let’s see what happens……….hopefully success (fingers crossed)

---

### Post by cpet1992 on 2022-06-10
> **tea for one said:**
> Splendid – Windows 10 in UEFI mode (as it should be)

Power off PC
De-activate, isolate (via UEFI settings) or physically remove the two Windows disks
(This is advisable to try and avoid future Windows boot problems - either OS can be booted via your UEFI one-time boot menu)
Boot into Ubuntu live session in UEFI mode (very important)
Only your target disk should be accessible
Your disk is already GPT
Allow the installer to create the partitions and install Ubuntu 22.04

Let’s see what happens……….hopefully success (fingers crossed)


Will do this...

Here is some info just incase it is needed. Sorry for the spacing.

OS NAME: Microsoft Windows 10 Pro
Version: 10.0.19044 Build 19044
Other OS Description: N/A
OS Manufacturer: Microsoft Corporation
System Model: 3134C6U
System Type: x64-based PC
System SKU: To be filled by O.E.M
Processor: Intel(R) Core(TM) i7-2600 CPU @ 3.4GHz, 3401 Mhz, 4 Core(s), 8 Logical Processor(s)
BIOS Version/Date: LENOVO 9QKT37AUS, 2/14/2012
SMBIOS Version: 2.6
Embedded Controller Version: 255.255
BIOS Mode: UEFI
BaseBoard Manufacturer: LENOVO
BaseBoard Product: To be filled by O.E.M
BaseBoard Version: To be filled by O.E.M
Platform Role: Desktop
Secure Boot State: Unsupported
PCR7 Configuration: Binding Not Possible
Windows Directory: C:\Windows
System Directory: \Device\HarddiskVolume4
Locale: United States
Hardware Abstraction Layer: Version= "10.0.19041.1566"
User Name: [USERNAME PROTECTED]
Time Zone: Central Daylight Time
Installed Physical Memory (RAM): 8.00 GB
Total Physical Memory: 7.98 GB
Available Physical Memory: 5.04 GB
Total Virtual Memory: 20.0 GB
Available Virtual Memory: 15.2 GB
Page File Space: 12.0 GB
Page File: C:\pagefile.sys

---

### Post by cpet1992 on 2022-06-10
> **tea for one said:**
> Splendid – Windows 10 in UEFI mode (as it should be)

Power off PC
De-activate, isolate (via UEFI settings) or physically remove the two Windows disks
(This is advisable to try and avoid future Windows boot problems - either OS can be booted via your UEFI one-time boot menu)
Boot into Ubuntu live session in UEFI mode (very important)
Only your target disk should be accessible
Your disk is already GPT
Allow the installer to create the partitions and install Ubuntu 22.04

Let’s see what happens……….hopefully success (fingers crossed)

Well I tried it, and no joy. Exact same error

---

### Post by cpet1992 on 2022-06-10
I'm thinking something about the kernel changed.

---

### Post by tea for one on 2022-06-11
> **cpet1992 said:**
> Well I tried it, and no joy. Exact same error
That is very disappointing.
If it is convenient, can you run the boot-repair report without your two Windows drives attached.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Please choose 2nd option and pop the pastebin link in this thread.

---

### Post by cpet1992 on 2022-06-11
> **tea for one said:**
> That is very disappointing.
If it is convenient, can you run the boot-repair report without your two Windows drives attached.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Please choose 2nd option and pop the pastebin link in this thread.

Link:

[URL="https://paste.ubuntu.com/p/rJRqXTCPh9/"]https://paste.ubuntu.com/p/2n3r6N2D2t/


[/URL]

---

### Post by tea for one on 2022-06-11
Thank you for the boot-repair report.
There are some unexpected details as follows:-

[COLOR="#0000FF"]Line 6[/COLOR] - Windows 7/8/10/11/2012 is installed in the MBR of /dev/sdb.
I was not expecting this because Windows should be in UEFI mode.
This comment refers to an old-style mbr boot system
[COLOR="#0000FF"]
Line 9 and 17[/COLOR] - Your Linux drive has both Bios boot partition and EFI partition.
An Ubuntu installation in UEFI mode would not create a Bios boot partition.
You should have a minimum of two partitions EFI system partition and system partition (inc. /home)

[COLOR="#0000FF"]Line 40[/COLOR] - sdb2 is empty (may have been an earlier Bios boot partition?)

[COLOR="#0000FF"]Line 293[/COLOR] - Your Linux on sda3 is 32-bit, so it may be incompatible with your 64-bit UEFI firmware. You may want to install a 64-bit Linux instead 
This is a surprising comment. I thought that you were installing Ubuntu 22.04LTS which is 64-bit.

Before we go any further, please confirm that you can still boot Windows?
Also, can you detail the Linux system you are trying to install?

---

### Post by cpet1992 on 2022-06-11
> **tea for one said:**
> Thank you for the boot-repair report.
There are some unexpected details as follows:-

[COLOR="#0000FF"]Line 6[/COLOR] - Windows 7/8/10/11/2012 is installed in the MBR of /dev/sdb.
I was not expecting this because Windows should be in UEFI mode.
This comment refers to an old-style mbr boot system
[COLOR="#0000FF"]
Line 9 and 17[/COLOR] - Your Linux drive has both Bios boot partition and EFI partition.
An Ubuntu installation in UEFI mode would not create a Bios boot partition.
You should have a minimum of two partitions EFI system partition and system partition (inc. /home)

[COLOR="#0000FF"]Line 40[/COLOR] - sdb2 is empty (may have been an earlier Bios boot partition?)

[COLOR="#0000FF"]Line 293[/COLOR] - Your Linux on sda3 is 32-bit, so it may be incompatible with your 64-bit UEFI firmware. You may want to install a 64-bit Linux instead 
This is a surprising comment. I thought that you were installing Ubuntu 22.04LTS which is 64-bit.

Before we go any further, please confirm that you can still boot Windows?
Also, can you detail the Linux system you are trying to install?

Yes windows boots fine.

I'm trying to install Ubuntu 22.04 LTS

I'm not sure where all the others came from...

I just found out that my wife flipped a breaker this morning, and both HDDs were completely empty. (Yes even ALL THE WINDOWS DATA with the exception of the SSD which has Windows 10 Pro on it.) Everything else was lost. 

So I repartitioned both for fat32 and am reinstalling all the Windows games. I have a 2tb laptop HDD that my friend gave me. I will install that in my PC for installing Ubuntu on instead. Before attempting that though, I was thinking of booting the live image, and using terminal to "shred" the 2tb drive and try installing once all data is removed from it. What do you think?

NOTE: I should mention that the particular HDD I was trying to use, was the original HDD in this PC when I bought it.

---

### Post by tea for one on 2022-06-11
> **cpet1992 said:**
> I just found out that my wife flipped a breaker this morning
I do not understand, what is a breaker?
> **cpet1992 said:**
> So I repartitioned both for fat32 and am reinstalling all the Windows games. I have a 2tb laptop HDD that my friend gave me. I will install that in my PC for installing Ubuntu on instead. Before attempting that though, I was thinking of booting the live image, and using terminal to "shred" the 2tb drive and try installing once all data is removed from it. What do you think?
No need to shred anything. When you are in a live session, just use Gparted to create GPT.
Boot in UEFI mode
Remove all Windows drives
Let the installer create two partitions (EFI and System)

Do you have any idea about the 32-bit installation discovered by boot-repair?

---

### Post by #&amp;thj^% on 2022-06-11
> **tea for one said:**
> I do not understand, what is a breaker?


Just pop-ed in: A circuit breaker is an electrical switch designed to protect an electrical circuit from damage caused by overcurrent/overload or short circuit.

---

### Post by tea for one on 2022-06-11
@1fallen - Yes, circuit-breaker is easily understood. I was wrapped up in trying to help cpet1992 that my brain malfunctioned for a few seconds.
Back to normal now and waiting for a positive outcome.

---

### Post by cpet1992 on 2022-06-12
> **tea for one said:**
> I do not understand, what is a breaker?

No need to shred anything. When you are in a live session, just use Gparted to create GPT.
Boot in UEFI mode
Remove all Windows drives
Let the installer create two partitions (EFI and System)

Do you have any idea about the 32-bit installation discovered by boot-repair?

Not a clue. Though this PC was built originally in the early Windows 7 era. Is it possible that Windows 7 was 32 bit?

---

### Post by cpet1992 on 2022-06-12
[B]Perhaps I should tell you this PCs history

[/B]This PC started its life out at a local school, a Lenovo ThinkCentre M71E 3134 SFF Desktop.

Originally, it sported a Pentium G850 Dual-Core processor @ 2.9GHz and 4GB DDR3 RAM
For storage it came with a Seagate 500GB HDD @ 7,200 RPM @ ~ 100MB/s.

To say the least, it was not up to snuff.

Since then I have added a few components.

I'll list them here, just incase any specific component may interfere with Ubuntu:

CPU: intel Core i-7 2nd GEN 2600 4-Core, 8-Thread Processor @ 3.4GHz Base up to 3.8GHz Boost
MOBO: Stock Lenovo MOBO
RAM: 8GB DDR3 
GFX: EVGA GeForce GTX 1050Ti SC 4GB DDR5 Graphics Card
1x WD Blue EasyStore 240GB SSD (Windows 10 OS)
2x Seagate Barracuda 500GB 100MB/s HDDs (Storage) ***One brand new, one is OEM to PC***
1x Samsung 2.5in 2TB 100MB/s HDD (Used by a friend before it was given to me)

Hope this helps us find something. 

BTW thanks to everyone who has been trying to help, its much appreciated.

---

### Post by cpet1992 on 2022-06-12
> **tea for one said:**
> I do not understand, what is a breaker?

No need to shred anything. When you are in a live session, just use Gparted to create GPT.
Boot in UEFI mode
Remove all Windows drives
Let the installer create two partitions (EFI and System)

Do you have any idea about the 32-bit installation discovered by boot-repair?

Could you teach me how to do that? Whats GPT?

---

### Post by cpet1992 on 2022-06-12
I figured out what it was, and did that and tried it again same results.

The error that shows before the installer crashes is as follows:

```
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e.g. happen if you try to connect a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
```

---

### Post by cpet1992 on 2022-06-12
Ok, tried again and it shows errors like this:
```
ubuntu kernal: [  398.627667] SQUASHFS ERROR. unable to read page, block #######
```

---

### Post by tea for one on 2022-06-12
> **cpet1992 said:**
> I figured out what it was, and did that and tried it again same results.

The error that shows before the installer crashes is as follows:

```
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e.g. happen if you try to connect a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
```

Following a quick internet search, this appeared  [https://askubuntu.com/questions/1241795/xdg-runtime-dir-is-not-owned-by-us-uid-0](https://askubuntu.com/questions/1241795/xdg-runtime-dir-is-not-owned-by-us-uid-0)
Worth a try?

---

### Post by cpet1992 on 2022-06-12
> **tea for one said:**
> Following a quick internet search, this appeared  [https://askubuntu.com/questions/1241795/xdg-runtime-dir-is-not-owned-by-us-uid-0](https://askubuntu.com/questions/1241795/xdg-runtime-dir-is-not-owned-by-us-uid-0)
Worth a try?

Tried that. Nothing happened

---

### Post by tea for one on 2022-06-12
> **cpet1992 said:**
> Tried that. Nothing happened
By this, you mean you couldn't boot into a live session after adding acpi=off to grub?

---

### Post by cpet1992 on 2022-06-12
> **tea for one said:**
> By this, you mean you couldn't boot into a live session after adding acpi=off to grub?

No, it boots, but ubuntu installer still gives the same error and crashes

It won't do it on my son's laptop either. I don't understand what changed.

---

### Post by tea for one on 2022-06-12
In your original post, you mentioned that Ubuntu 20.04.4 was working OK.
Why don't you download the same version and see if the installation succeeds?

---

### Post by Bomack on 2022-06-13
> **cpet1992 said:**
> Hello, I used to have Ubuntu 20.04.4 on my PC, and it worked no problem. I did a reinstall (or tried) to have a fresh start. It came up with a terminal error: not owned by uid 0, but by uid 999! 

NOTHING works.

Please help.

Hi cpet,

Since 20.04.4 used to work but it no longer works on a fresh install, I'd like you to try this:

Download and try: [https://old-releases.ubuntu.com/releases/20.04.1/ubuntu-20.04-desktop-amd64.iso](https://old-releases.ubuntu.com/releases/20.04.1/ubuntu-20.04-desktop-amd64.iso)

This is the Official Original LTS Release of Ubuntu 20.04.

If this boots up to the Live Session (Try Ubuntu) then try installing it from there. However, I recommend that you DO NOT apply any updates from the Live Session prior to starting the installation.

Let me know if this works. :)

Bob

---

### Post by cpet1992 on 2022-06-13
> **Bomack said:**
> Hi cpet,

Since 20.04.4 used to work but it no longer works on a fresh install, I'd like you to try this:

Download and try: [https://old-releases.ubuntu.com/releases/20.04.1/ubuntu-20.04-desktop-amd64.iso](https://old-releases.ubuntu.com/releases/20.04.1/ubuntu-20.04-desktop-amd64.iso)

This is the Official Original LTS Release of Ubuntu 20.04.

If this boots up to the Live Session (Try Ubuntu) then try installing it from there. However, I recommend that you DO NOT apply any updates from the Live Session prior to starting the installation.

Let me know if this works. :)

Bob

I was wondering if that might work. I'll give it a go!



RESULTS:

It wont do anything, doesnt even boot to ask if you want to go into a live session or install. The screen just keeps trying to set the resolution over an over again and doesnt get anywhere.

---

### Post by cpet1992 on 2022-06-13
> **tea for one said:**
> In your original post, you mentioned that Ubuntu 20.04.4 was working OK.
Why don't you download the same version and see if the installation succeeds?

Great idea, I'm writing it to my usb right now



RESULTS:

It wont do anything, doesnt even boot to ask if you want to go into a live session or install. The screen just keeps trying to set the resolution over an over again and doesnt get anywhere.

---

### Post by tea for one on 2022-06-14
In post no.1, you mentioned that you had success with Linux Lite.
Which version?
The USB booted OK and you installed it?

---

### Post by sefaozc on 2022-06-14
Hi,

I presume you are using belenaEtcher to make a bootable usb. I strongly suggest you to use another program to make a bootable usb such as fedora media writer. 

Find another computer to run Fedora Media Writer (works both on Fedora and Windows).
Install Fedora Linux via that program. 
After the installation finished, download Ubuntu .iso file and make a Ubuntu installer usb via the same program (Fedora Media Writer preinstalled on Fedora Linux)

Btw, I recommend you tu use the automatic partitioning.

I hope it works.

Best regards,

---

### Post by cpet1992 on 2022-06-14
> **tea for one said:**
> In post no.1, you mentioned that you had success with Linux Lite.
Which version?
The USB booted OK and you installed it?

yes in fact it worked well. i just want ubuntu

---

### Post by cpet1992 on 2022-06-14
> **sefaozc said:**
> Hi,

I presume you are using belenaEtcher to make a bootable usb. I strongly suggest you to use another program to make a bootable usb such as fedora media writer. 

Find another computer to run Fedora Media Writer (works both on Fedora and Windows).
Install Fedora Linux via that program. 
After the installation finished, download Ubuntu .iso file and make a Ubuntu installer usb via the same program (Fedora Media Writer preinstalled on Fedora Linux)

Btw, I recommend you tu use the automatic partitioning.

I hope it works.

Best regards,
 Actually, ive tried several. even tried ventroy to boot directly from the iso. literally every os worked except ubuntu and ubuntu based os's except linux lite

infact. any os with that same installer, wont install. must be an error with that. does it work on your pc's?

---

### Post by cpet1992 on 2022-06-14
> **tea for one said:**
> In post no.1, you mentioned that you had success with Linux Lite.
Which version?
The USB booted OK and you installed it?

Linux Lite 6.0 64 Bit

---

### Post by Bomack on 2022-06-14
> **cpet1992 said:**
> I was wondering if that might work. I'll give it a go!



RESULTS:

It wont do anything, doesnt even boot to ask if you want to go into a live session or install. The screen just keeps trying to set the resolution over an over again and doesnt get anywhere.


Regarding your original 20.04 installation that WAS working: Was it originally a Fresh Install, or was it also an Upgrade from a previous version?

At this point I think I'd try testing an earlier LTS version just to see if the pc will accept it at all.

Also, if you haven't already done it, you might reset your Bios and then check your settings.

p.s. I also use Ventoy and it works just fine every time for me.

---

