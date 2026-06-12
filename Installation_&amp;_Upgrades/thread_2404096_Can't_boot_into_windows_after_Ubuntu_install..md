---
title: "Can't boot into windows after Ubuntu install."
date: 2018-10-20
forum: Installation &amp; Upgrades
---

### Post by matt110 on 2018-10-20
Hello,

I had a functioning W10/Ubuntu dual boot system and decided to install Kubuntu in replacement of Ubuntu 16.04. The system just boots straight into Kubuntu with no Grub options.
I have run a boot info script shown below.

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================


============================ Drive/Partition Info: =============================

no valid partition table found
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/nvme0n1                                                       
/dev/nvme0n1p1   E282D97C82D9559F                       ntfs       Recovery
/dev/nvme0n1p2   B6D9-E4A6                              vfat       
/dev/nvme0n1p3                                                     
/dev/nvme0n1p4   FA10DEB210DE755B                       ntfs       
/dev/nvme0n1p5   2f5b92bf-e823-4d44-b0e1-e3bdd16adced   ext4       
/dev/nvme0n1p6   74da5874-c508-42a1-a532-444bb5be6793   swap       
/dev/nvme0n1p7   05ebb6ec-431a-406e-ac26-ce92d5f41d84   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/nvme0n1p5   /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/nvme0n1p7   /home                    ext4       (rw,relatime,data=ordered)


```

Here is a Gparted screen.
[ATTACH=CONFIG]281388[/ATTACH]
Any help greatly appreciated.

---

### Post by yancek on 2018-10-20
I would suggest you get a more updated bootinfoscript which you can do at the site below.  Use the 2nd option to add a ppa in Kubuntu and after downloading it, run it by selecting the Create BootInfo Summary option and do NOT try to make any repairs.  When it finishes, it will give you a link to post here, do that.  The bootinfo you posted doesn't have enough information to tell much about your system other than that you have both Linux and windows partitions and an EFI partition.  Did you install Kubuntu UEFI?  

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by matt110 on 2018-10-21
hi thanks for the reply.

I delive I am using BIOS not uefi.
Here is the BootInfo Summary Link: [URL="http://paste.ubuntu.com/p/WxWkWDKHnZ"]http://paste.ubuntu.com/p/WxWkWDKHnZ
[/URL]

---

### Post by ajgreeny on 2018-10-21
I am not an expert in reading the Boot-Info script output but it looks to me as though your original Windows 10, and presumably also the Ubuntu you had previously, were both installed using UEFI, though it is now impossible to know anything about the previous Ubuntu system as that has gone, replaced with Kubuntu.

When you overwrote the Ubuntu and installed Kubuntu I assume that was using a USB install medium; did you boot that using the UEFI version or simply go to the first instance of the USB in the boot devices list, because it looks as if Windows 10 is in UEFI, but you are now using Kubuntu, as you thought, in legacy mode.

In theory you might still be able to boot to Windows but you will have to do that from the boot device list, not from grub.  Try hitting the key that brings up your boot priority device list and see what is offered. However, for ease of use it may still be easiest if you have npot used it much to reinstall Kubuntu, but this time in UEFI mode.  It may also be possible to change the Kubutnu mode to UEFI without reinstalling, but I regret I can not help with those possibilities so wait for more and better advice.

---

### Post by yancek on 2018-10-21
> /dev/nvme0n1p2   B6D9-E4A6                              vfat 

The above info was in your original bootinfo script and shows the EFI vfat partition.  You GParted image also explicityl shows an EFI partition on the drive.  The new boot repair output shows and EFI partition also.  Did you notice the messages indicating that you had run boot repair in Legacy mode?  You need to run it again in EFI mode (check their home page on how to do this), maybe disable Legacy in the BIOS as running it Legacy doesn't show any of the EFI files nor does it show any Grub files.

---

### Post by oldfred on 2018-10-21
Also Boot-Repair uses bootinfoscript as first part of report and bootinfoscript has not been updated to fully show the new NVMe drives.

Reboot in UEFI mode and run the full uninstall/reinstall of grub from advanced options. Do not run if in BIOS mode.

---

