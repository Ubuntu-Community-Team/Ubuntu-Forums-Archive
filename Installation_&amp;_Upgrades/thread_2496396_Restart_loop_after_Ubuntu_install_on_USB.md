---
title: "Restart loop after Ubuntu install on USB"
date: 2024-03-26
forum: Installation &amp; Upgrades
---

### Post by amolimjo on 2024-03-26
My laptop has become unusable, please help.

I tried installing Ubuntu for the first time on a USB stick to run from any computer.

Here are the steps I took:

1. downloaded Ubuntu from web on Windows and transferred to USB1 using Rufus
2. boot into Ubuntu test from live USB1
3. checked that Windows EFI partition (separate SSD) was flagged as msftdata (the guide I followed stated it should be changed from EFI to mfstdata, but it was already this way)
4. ran install ubuntu to USB2 (clean drive, 332MB EFI partition and rest of 16GB Ext4, mount point ’/’
5. after successful install changed main OS EFI partition flag to EFI (I suspect this might be the issue, as it was msftdata when I started?)
6. restarted computer

This is the situation now:

- when USB2 with newly installed Ubuntu is inserted it boots(?) but gets stuck on the loading screen (Ubuntu logo), however I can enter Ubuntu recovery mode
- can’t access Ubuntu downloaded with Rufus on from USB1 (to that way see what might be wrong)
- cant boot into Windows 10 (OS on my SSD), removed the drive from the computer and all other issues persist. Does this mean my BIOS is damaged? Is there any way to fix that (laptop is Samsung NP530U3C)
- stuck in restart loop (can’t enter BIOS)

Done so far: unplugged the CMOS battery, but problems persists. Only way to exit restart loop seems to be using USB2. I tried replacing the esp&boot flags with msftdata with parted, but it was not possible (no idea why). When I run dmesg | grep ”EFI v” I get efi: EFI v2.3.1 by Phoenix Technologies Ltd., so I assume it boots in EFI/UEFI (atleast the Ubuntu).

Let me know if more information is needed. Unfortunately my knowledge is none when it comes to recovery.

Thank you for the help! Even if I can just get Windows back running I’m more than happy.

’’’
root@LA-5303C:*# sudo parted -1s
Model: ATA C250BX100SSD1 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:
Number Start End Size Type Filesys Flags
1   32,8KB 249GB 249GB primary ntfs 
2   249GB  250GB 609MB primary ntfs

Model: ATA SanDisk SSD 1100 (scsi)
Disk /dev/sdb: 24,0G
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:
Number Start End Size Type Filesys Flags
1 1049KB 20,8GB 20,8GB primary
2 20,8GB 24GB   3221MB primary     irst

Model: Kingston DataTraveler 3.0 (scsi)
Disk: /dev/sdc: 15,5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:
Number Start End Size Type Filesys Flags
1 1049kB 332MB 331MB primary fat32 boot,esp 
2 332MB 15,5GB 15,1GB primary ext4
’’’

---

### Post by yancek on 2024-03-26
You did not link to the site where you got your info.  EFI partitions should be vfat or fat filesystems.  You neglected to indicate which release of Ubuntu you used?  You show a 250GB drive which is a Legacy (msdos) install of windows and there is no sign of EFI.  The only sign of EFI is on the Kingston drive which I expect is the installer?  Were you trying to install Ubuntu to the 24GB Sandisk?  A bit small but might work.  You don't have an EFI partition on that drive nor do you have any Linux filesystems on your partition.

What is your goal, windows on the larger drive and Ubuntu on the small one?

The Partition tables on all 3 drives are msdos which would indicate a Legacy install be used although it is possible to do an EFI install of Ubuntu on that drive.  Did you boot the Ubuntu installer in EFI or Legacy mode.  Installing Ubuntu as an EFI sysem on a separate drive should be able to boot a Legacy install of windows if windows is on another drive, at least that is my experience.  There is nothing in your  parted output indicating a Linux filesystem partition on the 24GB drive.

---

### Post by amolimjo on 2024-03-26
Hi, thanks for the comments.

Here are the instructions I followed: [https://itsfoss.com/intsall-ubuntu-on-usb/](https://itsfoss.com/intsall-ubuntu-on-usb/). The goal was to install Ubuntu on a USB bootable drive, that I could plug into any computer to simply test the OS, but keep using my laptop as normal with Windows 10 from the 250GB SSD.

I messed up, as I thought the default boot would be EFI, not legacy and still followed the instructions. Now I’m unsure, as I can’t access the BIOS, but Ubuntu can boot into Recovery mode with the install on USB2 Kingston drive. 

I did the install from live Ubuntu on USB1 running 22.04.4 LTS test mode. The same version was installed on the USB2 Kingston drive. 

The Sandisk drive is a built in storage on my laptop that, to my knowledge, is not used at all. Could this one be causing problems?

Basically, I want to fix or find the reason to why I can’t access BIOS, boot into Windows 10 and then I can come back to reinstall Ubuntu correctly on the USB. However, the only way to interact with the laptop at all is Ubuntu recovery mode through the USB install.

---

### Post by tea for one on 2024-03-26
> **amolimjo said:**
> Basically, I want to fix or find the reason to why I can’t access BIOS, boot into Windows 10 and then I can come back to reinstall Ubuntu correctly on the USB. However, the only way to interact with the laptop at all is Ubuntu recovery mode through the USB install.
Advanced options > Recovery mode > Press Enter (for maintenance after text has stopped scrolling)
Or there may be a window with "Drop to Root Shell prompt" (depends on the version)
You should have a root prompt 
Try the following command
```
systemctl reboot --firmware-setup
```

---

### Post by tea for one on 2024-03-26
```
Model: ATA SanDisk SSD 1100 (scsi)
Disk /dev/sdb: 24,0G
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:
Number Start End Size Type Filesys Flags
1 1049KB 20,8GB 20,8GB primary
2 20,8GB 24GB 3221MB primary [COLOR="#0000FF"]irst[/COLOR]
```
Is this disk an Optane device ([COLOR="#0000FF"]I[/COLOR]ntel [COLOR="#0000FF"]R[/COLOR]apid [COLOR="#0000FF"]S[/COLOR]torage [COLOR="#0000FF"]T[/COLOR]echnology)?

---

### Post by amolimjo on 2024-03-26
When I run this I get the output:

”Cannot indicate to EFI to boot into setup mode: Firmware does not support boot into firmware”

Regarding the 24GB drive, it does seem to be configured that way, but it’s not intel hardware. To be honest I’m not sure and never even noticed the drive until i fiddled around with the USBs in gparted.

---

### Post by tea for one on 2024-03-26
This next suggestion is 99% successful
Boot into a "Try Ubuntu" live session using your Ubuntu installer USB1 (made by Rufus)
Open a terminal and enter
```
sudo systemctl reboot --firmware-setup
```

---

### Post by amolimjo on 2024-03-26
Problem is, I can’t boot into anything except the USB2 Ubuntu install (which doesn’t boot properly, but at least works in recovery mode). It simply gets stuck in a restart loop if I don’t have USB2 inserted. I tried with USB1 live Ubuntu, Windows 10 on main drive, fresh windows install, but nothing works.

---

### Post by tea for one on 2024-03-27
Using USB2 via recovery mode, can you reach the Ubuntu desktop and open Firefox?

---

### Post by amolimjo on 2024-03-27
No, I can only boot into recovery mode. I get stuck on Ubuntu logo screen when trying to boot normally. Please read the original post.

---

### Post by tea for one on 2024-03-27
I did read the original post - there is no need to be irritated by my question.
Recovery mode allows you to repair broken packages and reach a working desktop (assuming your PC is not unduly compromised)

I'll leave you in peace now.

---

### Post by oldfred on 2024-03-27
Windows only installs in old BIOS mode to MBR(msdos) partitioned drives.
So Windows install was BIOS. You then boot from MBR. And boot flag must be on the NTFS partition with boot files. It would not be an ESP - efi system partition.
If you can change boot flags on Windows back to boot & as mfstdata, then I would expect Windows to boot if system is set to boot in old BIOS mode.
Some systems require user to change UEFI/BIOS settings to correct mode UEFI or BIOS, some auto switch based on boot in UEFI/BIOS one time boot menu.

Microsoft required vendors to install in UEFI boot mode to gpt partitioned drives in 2012 with release of Windows 8.
So any system that can support Ubuntu which would have to be newer than 10 years old, is UEFI based.
Did you install Windows yourself in old BIOS/MBR configuration?
Or is system so old that BIOS/MBR was original install, upgraded to Windows 10. If so a lighter weight flavor of Ubuntu will work much better.

---

