---
title: "Reviving Windows boot in dual hard disk UEFI steup"
date: 2020-03-16
forum: Installation &amp; Upgrades
---

### Post by misbug on 2020-03-16
Hi. A quick disclaimer before I start: *I haven't had to dual boot windows in 15 years and I'm pretty novice about it. So please take my description of the situation with a grain of salt.*

I have two separate hard disks /dev/nvme0n1 which I used for Ubuntu 19.10 and /dev/sda a solid sate for Windows 10. The way I installed was following [this askubuntu.com]("https://askubuntu.com/a/843649/103884") question. Summary: installing windows, then ubuntu with *efi*, *swap*, and / partitions. After that I was able to easily login to my Ubuntu.

However, my windows installation is nowhere to be seen. "sudo parted -l" 

```

Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 
    
 Number  Start   End     Size    File system  Name                          Flags
  1      1049kB  17,8MB  16,8MB               Microsoft reserved partition  msftres
  2      17,8MB  256GB   256GB   ntfs         Basic data partition          msftdata
    
    
Model: Samsung SSD 960 EVO 250GB (nvme)
Disk /dev/nvme0n1: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 
    
Number  Start   End     Size    File system     Name  Flags
 1      1049kB  650MB   649MB   fat32                 boot, esp
 2      650MB   20,6GB  20,0GB  linux-swap(v1)
 3      20,6GB  250GB   229GB   ext4

```

I assume "gpt" partition tells me both are in EFI mode... 

os-prober returns nothing and efibootmgr returns:
```

    BootCurrent: 0003
    Timeout: 1 seconds
    BootOrder: 0003,0008,0009,0001,0002
    Boot0001  UEFI: IP4 Intel(R) Ethernet Connection (2) I219-V
    Boot0002  UEFI: IP6 Intel(R) Ethernet Connection (2) I219-V
    Boot0003* ubuntu
    Boot0008* UEFI: IP4 Intel(R) Ethernet Connection (2) I219-V
    Boot0009* UEFI: IP6 Intel(R) Ethernet Connection (2) I219-V

```

In "/boot/efi/EFI/" I have the following (no WINDOWS)
```

    .
    &#9500;&#9472;&#9472; BOOT
    &#9474;   &#9500;&#9472;&#9472; BOOTX64.EFI
    &#9474;   &#9500;&#9472;&#9472; fbx64.efi
    &#9474;   &#9492;&#9472;&#9472; mmx64.efi
    &#9492;&#9472;&#9472; ubuntu
        &#9500;&#9472;&#9472; BOOTX64.CSV
        &#9500;&#9472;&#9472; grub.cfg
        &#9500;&#9472;&#9472; grubx64.efi
        &#9500;&#9472;&#9472; mmx64.efi
        &#9492;&#9472;&#9472; shimx64.efi

```
By inspecting "/boot/grub/grub.cfg" visually (I cannot bring up the grub menu in during the boot), there seems to be menuentry and submenu for Ubuntu options but no mention of windows.

Can you think of anyway that I can bring back that windows stuff without reinstalling everything?

---

### Post by dragonfly41 on 2020-03-16
Having jumped through many hoops myself to arrive at a stable triple boot configuration I suggest departing from the main road to add rEFInd to your boot filesystem.

That is, you will see /boot/efi/EFI/refind and the others will be untouched.
You can always revert to using the alternatives.

[https://www.rodsbooks.com/refind/installing.html](https://www.rodsbooks.com/refind/installing.html)


[COLOR=#000000]$ sudo apt-add-repository ppa:rodsmith/refind[/COLOR]
[COLOR=#000000]$ sudo apt-get update[/COLOR]
[COLOR=#000000]$ sudo apt-get install refind

If rEFInd does not find Windows and Ubuntu boot loaders then we can take it from there.

Refer also to optional settings in /boot/efi/EFI/refind/refind.conf.[/COLOR]

---

### Post by P-I H on 2020-03-16
I tried in more than one day to install W10 pro on the ssd in a computer with Ubuntu 19.10 on a 500 GB NVme, Ubuntu 20.04 on a 250GB NVme and an unformatted 250 GB ssd.
This didn't work. Had to install w10 on the 250 GB NVme and Ubuntu 20.04 on the ssd.
More in this link:
[https://ubuntuforums.org/showthread.php?t=2438673](https://ubuntuforums.org/showthread.php?t=2438673)

---

### Post by yancek on 2020-03-16
You indicate your first step was installing windows 10.  After doing that, did you successfully reboot into windows 10 prior to attempting to install Ubuntu?

> However, my windows installation is nowhere to be seen. "sudo parted -l"  

??Your parted output clearly showss that sda is solely windows??  Windows on a GPT drive which is the case here, means it needs to be UEFI and according to the info you posted, there are no UEFI entries for windows.  I would have expected the windows installer to detect a GPT drive and create the EFI partition for an EFI system but apparently not.  I've only installed windows 10 one time and it was on a Legacy/msdos drive so???  My understanding is that Grub2 UEFI will not boot a windows Legacy install so you need windows EFI.  You might  try creating an EFI partition on the windows drive to keep the drives separate and copying the EFI files for windows there.  I've no idea if this is possible on windows or how to do it if it is.  You might try a windows forum on how to do this.  Post 6 at the link below seems to expalin this process.  Briefly reviewing the page, I hope you are patient and have time on your hands.  Good luck!

 [https://www.tenforums.com/general-support/91745-how-make-efi-win10-boot-instruction-efi-partition.html](https://www.tenforums.com/general-support/91745-how-make-efi-win10-boot-instruction-efi-partition.html)

---

### Post by oldfred on 2020-03-16
Windows puts boot partition on default drive. So it may have put ESP on drive you reformatted for Ubuntu?
But it still should have had an UEFI boot entry, even if obsoleted by reformat of ESP.

Can you turn off drive in UEFI drive settings. New systems do not need physical disconnection, but have settings to deactivate a drive in UEFI. Then with only one drive seen, your install will be totally on that drive.

---

### Post by misbug on 2020-03-16
> **oldfred said:**
> Windows puts boot partition on default drive. So it may have put ESP on drive you reformatted for Ubuntu?
But it still should have had an UEFI boot entry, even if obsoleted by reformat of ESP.

Can you turn off drive in UEFI drive settings. New systems do not need physical disconnection, but have settings to deactivate a drive in UEFI. Then with only one drive seen, your install will be totally on that drive.

Based on your suggestion I did a  test: I restarted the machine and from the BIOS disabled the Ubuntu disk from the boot sequence. But then I notice that the Windows hard drive is not even in the boot options. Continued any way but the system didn't boot. BTW, that hard disk does appear during the system post. I'm lost!

---

### Post by oldfred on 2020-03-16
Boot order is separate from hardware settings on drives. 
See this example from my Asus
Screenshot # 3. Advanced mode, Storage configuration, can set to disabled
[https://ubuntuforums.org/showthread.php?t=2258575&page=2](https://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by misbug on 2020-03-19
I solved my problem, not in the way that I wanted to, but solved nonetheless.

First I installed refind as suggested by dragonfly41 (thanks a lot). It did not solve the problem, however, I found it much easier to work with compared to grub.

After that, I [COLOR=#000000]did what [/COLOR][COLOR=#000000]oldfred (thanks a lot) suggested regarding deactivating the disk via the BIOS. I couldn't do it via the BIOS, however, I physically disconnected the drive, booted the system using a Windows 10 live usb. Trying to fix the boot via Windows troubleshoot didn't work. So I did what I had to: Installed the a new copy of windows while the Ubuntu disk is physically detached. Once the installation finished, I disabled the "fast startup" from windows power setting (some suggest that it causes some problems). 

Then connected the ubuntu disk back, booted to ubuntu, did a os-prober and updated the refind. And voila, it is fixed. 

In a way, I'm upset that I couldn't solve the issue (or rather, understand the problem) but I have both OS and happy about it. Thank you all for the support.
[/COLOR]

---

