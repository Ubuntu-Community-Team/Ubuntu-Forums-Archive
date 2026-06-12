---
title: "Cannot boot or install Ubuntu 11.10 from USB pen drive Kingston Data Traveler G3"
date: 2012-03-10
forum: Installation &amp; Upgrades
---

### Post by Vpc on 2012-03-10
I've tried installing 11.10 from my Kingston Data Traveler (8GB), fat32, after following the instructions here [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
after using a bootable USB created in Windows and then using one created in Ubuntu. I've given the removable drives the highest priority in the BIOS but it just skips to the hard drive. I am able to access the USB drive via the hard drive so it's functioning. I am trying to install 11.10 on a home Desktop with no internet connection. (I was unable to connect to wired internet after installing of Ubuntu 10.04.04 using an older 4GB Kingston USB pen drive after a new Intel DP67DE micro ATX motherboard installed. After trying all the instructions online from various sites, seems the D Link DGE-530T PCI adapter version C1 & onboard Intel 82579 may not be compatible with 10.04 and the only PCI express slot is being used for a video card.)

Why won't the USB work? Was the Ubuntu 11.10 iso corrupted?

---

### Post by 2F4U on 2012-03-11
First of all, verify the checksum of the downloaded iso file:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

How did you install the iso on the usb drive, from which OS and what program did you use?

---

### Post by oldfred on 2012-03-11
Is system set to BIOS or UEFI?

Are you trying to use USB3? Try the USB2 ports. There seem to have been issues booting with many USB3 ports even though they are supposed to be backwards compatible.

---

### Post by Vpc on 2012-03-11
> **2F4U said:**
> First of all, verify the checksum of the downloaded iso file:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

How did you install the iso on the usb drive, from which OS and what program did you use?

Yeah I made sure I checked with md5sum before burning a new download of the iso onto a CD ROM yesterday. I will try my usb key later with this iso. I downloaded the iso from Windows. I used the pendrivelinux.com software recommended in step 2 of Ubuntu's download website in my first post when installing it on my usb drive in Windows, but the version I installed using Ubuntu's Startup Disk Creator had the same problem.

> **oldfred said:**
> Is system set to BIOS or UEFI?

Are you trying to use USB3? Try the USB2 ports. There seem to have been issues booting with many USB3 ports even though they are supposed to be backwards compatible.

BIOS. Was not using USB3 ports. Someone told me that some usb pen drives are not bootable and I also saw this comment online somewhere. I called Kingston's technical support and the rep said they don't support bootability or 3rd party software and weren't able to confirm if it's true that some usb drives are bootable and some are not. Does anyone know if this is a rumor or factual? The rep said he thought that something had changed in the G3 model from the older model of their pen drive (which I bought in 2010) to cause this but there must be some usb experts who know if it's true some pen drives are not bootable.

---

### Post by oldfred on 2012-03-11
I have used both Kingston and Microcenter USB flash drives. But I have a full install in my 16GB Kingston and it run 12.04 now. 
Some have had issues with different flash drives and the different flash drive installers.

```
fred@fred-LT-A105:~$ sudo parted /dev/sdb unit s print
Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 31375360s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End        Size       File system  Name          Flags
 1      2048s      4095s      2048s                   KingstonData  bios_grub
 2      4096s      14749695s  14745600s  ext4
 3      14749696s  29327359s  14577664s  ext4
 4      29327360s  31373311s  2045952s   ntfs


```

Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I actually now only use grub2's boot loader to directly loop mount ISOs for installing either from a hard drive or flash drive.

---

### Post by Rex Bouwense on 2012-03-11
You probably have already checked this but some computers recognize some flash or pen drives as another hard drive.  My Kingston flash drive is recognized as a hard drive and to boot from it I have to change the order of "hard drives" in the BIOS so the flash drive is the first to boot.  This may be your case as well.

---

### Post by Vpc on 2012-03-12
> **Rex Bouwense said:**
> You probably have already checked this but some computers recognize some flash or pen drives as another hard drive.  My Kingston flash drive is recognized as a hard drive and to boot from it I have to change the order of "hard drives" in the BIOS so the flash drive is the first to boot.  This may be your case as well.

Yes that fixed it. I didn't really bother to look because I thought I could just get the CD anyways and then heard about some USB drives not being bootable. I think that might only happen if the USB drive has software on it from the manufacturer that interferes with booting. The G3 doesn't come with any software.

---

