---
title: "Preparing external SDD for Ubuntu; balenaEtcher combines both partitions"
date: 2021-12-05
forum: Installation &amp; Upgrades
---

### Post by ankersoe on 2021-12-05
Hi,

I checked if there's been an issue with this, but couldn't find anything on it. Honestly, I'm literally at a loss for words here not knowing how to phrase my issue. I'm Danish.

The issues are the following. Since I wish to install Ubuntu on E: and do something else with F:, I'm gonna list the steps that I think need to be solved for me to end with an Ubuntu installation. Make sense?

1: Creating two partitions in Windows on my brand new 512gb intenso ssd makes them not register in BalenaEtcher or Rufus as separate partitions.

2: Making a bootable USB in BalenaEtcher causes both partitions to be listed together, wiping the entire drive. E:;F:

3: The ssd is not detected when booting from the created bootable USB.

---

### Post by oldfred on 2021-12-05
No idea what E: or F: may be.
Microsoft confuses "drives" and partitions. An E: "drive" may be a partition on first drive or a partition on the 4th drive. 

What brand/model system? 
What video card/chip?

Have you updated UEFI and SSD firmware to latest available from vendor.
Is Windows fast start up off?
Have you installed AHCI driver into Windows and changed UEFI settings to AHCI, most systems seem to default to RAID even with one drive.

More details & links in my signature below.

---

### Post by tea for one on 2021-12-05
First of all - Windows has an old-fashioned habit of not distinguishing exactly between drives and partitions?
E: and F:  - are they separate drives?

It looks like you want to keep Windows intact and install Ubuntu on an external SSD?

Here are some general pointers (not all will apply) :-

Backup your data
Both systems in UEFI mode with GPT
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

_UEFI settings_

Disable Secure Boot
Disable Fast Boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems)
[https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500](https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500)
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology)
Disable Optane memory and storage

[U]Windows 10
[/U]
Backup your data
Turn off Bitlocker 
Do not have any drives encrypted during Ubuntu installation process
Disable Fast Start Up i.e. Windows is not hibernating
Some Windows updates turn on hibernation automatically
Disable applications which manage Intel Optane memory & storage
Disk must be GPT
Install Windows 10 in UEFI mode
Check via System Information > System Summary > BIOS mode > UEFI
Windows will have  an EFI partition (needed by Ubuntu later)
Use Windows (Disk Management) tools to reduce Windows partition size and create free space
Reboot Windows to allow chkdsk to run
Windows may need AHCI driver
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)
[https://softwarekeep.com/help-center/how-to-download-standard-sata-ahci-controller-driver-on-windows-10](https://softwarekeep.com/help-center/how-to-download-standard-sata-ahci-controller-driver-on-windows-10)

[U]Existing Windows and then Ubuntu on Separate Disks
[/U]
De-activate, isolate via UEFI settings or disconnect/physically remove existing Windows OS drive so that only the target drive is accessible
Boot Ubuntu live and check that you are in UEFI mode
Open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Create GPT on your target disk using gparted
Open gparted > Device > Create Partition Table > Select gpt
Allow the installer to automatically create the necessary partitions (or your preferred configuration)
Double check that an EFI partition will be created
Boot each system independently via UEFI boot screen (ideal not cumbersome)
Boot priority can be controlled by UEFI
Each OS should be installed in UEFI mode with GPT
Each drive should have EFI partition
Each drive should have boot manager (Windows Boot Manager and Grub for Ubuntu)
Ensure that you have different UUIDs for each OS (if both Linux)
De-activate, disconnect, isolate or physically remove one drive so that you can check if the other boots independently (and vice versa)

---

### Post by yancek on 2021-12-05
It isn't really clear what you are trying to do.  Rufus and BelenaEtcher are both software programs designed to create a bootable usb for the purpose of instaslling an operating system.

> Since I wish to install Ubuntu on E: and do something else with F: 

No, stop right there.  You can't do that and expect it to work.  Windows does not assign drive letters ( E or F or whatever) to non-windows partitions.  You can't install a Linux OS to a non-Linux filesystem which E or F would have to be.  You need to do some basic reading on the difference between Linux and windows drive/partition naming conventions.  As indicated above, the windows drive letters are pretty meaningless as they can refer to an entire drive or to a partition on a drive and they don't differentiate or indicate on which drive it might be.  THe C:\ drive letter used in windows for the primary OS partition is a carry over from systems used in the 1970's when computers came with 2 floppy drives (A:\  and B:\) thus the first hard drive would be C"\.

I would suggest you do an online search for linux device/partition naming conventions and read through a few of those pages to get at least a basic understanding.

---

