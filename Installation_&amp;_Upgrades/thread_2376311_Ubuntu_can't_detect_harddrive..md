---
title: "Ubuntu can't detect harddrive."
date: 2017-11-01
forum: Installation &amp; Upgrades
---

### Post by joakia on 2017-11-01
I have a MSI laptop lying around, and I want to install Ubuntu.
The computer has 2 drives, one SSD, and one HDD. The SSD contains Win10, and the The HDD has/had Mint on it (how I installed it back in the day I can't recall:oops:). I would like to keep Win10 on the SSD, and have Ubuntu on the HDD.

I downloaded the latest distro from the official site, and used YUMI to mount the ISO on a USB-stick.
I boot the computer and get into Ubuntu. The problem is when trying to install, Ubuntu detects only one storage media, the USB-drive it's sitting on.
If I pull the drive out, Ubuntu doesn't detect any drives, and says it requires xx gb to install, and i have 0.0 gb available.

I tried running GParted from another USB-stick, and it detects the harddrive.
As I said it had Mint on it, and I thought that may be the problem, so I wiped everything on the HDD, so all the space was unallocated. Then I set up 4Gb as swap, and the rest as ext4 (seemed like a good idea from reading around online).
Reboot with Ubuntu, and same problem, still only detects the USB-drive. I've now tried setting up the HDD with GParted as ext4, ntfs and fat32 and in no case can Ubuntu detect the drive.
I figure I'm doing something wrong in the partitioning setup, as I obviously managed to install and run Mint at one point in history. In GParted, the drive is listed as /dev/sda.

I'd really appreciate if someone could tell me exactly how to partition the drive using GParted to be able to install Ubuntu.

Maybe not related but: during boot, I need to enter the BIOS and set the boot something from UEFI with CSM (writing this by memory, may not be accurate) to LEGACY. 
Not doing this causes Win10 to load, even if I have the Ubuntu USB-drive plugged in, and load order in BIOS set to load USB before SSD.

---

### Post by ajgreeny on 2017-11-01
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and may give us a lot more useful info on which to base any recommendations.

---

### Post by oldfred on 2017-11-01
If Windows is in UEFI boot mode, you only want Ubuntu in UEFI boot mode.
And for UEFI you need gpt partitioning, not the 35 year old BIOS/MBR or legacy configuration.

You do have to select UEFI boot from UEFI. And may have to have UEFI Secure boot off, and turn on allow USB boot.
Also drives must be in AHCI boot mode. If Windows drive is not, you have to first install the ACHI drivers to Windows.

Some other MSI systems, often issues are common by brand and if Intel or AMD, so these fixes may also apply.
 MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)

---

### Post by joakia on 2017-11-02
The link is [http://paste.ubuntu.com/25870724](http://paste.ubuntu.com/25870724).

---

### Post by oldfred on 2017-11-02
It shows an sda drive, but it is DOS or MBR partitioned but no partitions at all are shown?
It is not showing any Windows install?

You also show you may have UEFI Secure Boot on.
And you booted Ubuntu installer in BIOS boot mode.

Best then to turn off UEFI Secure Boot in UEFI. 
And boot USB flash drive in UEFI boot mode.

You said MSI system had two drives, are you sure it was not one drive with two partitions.
Windows calls partitions "drives" so it may be two actual drives each with one partition or two partitions on one actual drive.
Linux uses sda, sdb, sdc etc for drives and number after for partitions like sda1, sda2, sdb1 etc.

---

### Post by joakia on 2017-11-02
From the receipt of my purchase:
"[COLOR=#111111][FONT=&amp]Hard Drive: Super RAID 4 256GB SSD (PCIE Gen3 x4) [128GB *2] + 1TB (SATA) 7200rpm"
I tried holding shift as I rebooted Windows in order to get into UEFI setup. This brought me to the same BIOS/UEFI (not sure what to call it at this point) as pressing delete during boot. Tried setting drives to AHCI mode and rebooting. This only resulted in returning to the BIOS/UEFI, and not loading windows. Returning the setting to normal led me to boot straight to Windows. I'm now investigating how to install AHCI drivers. 
I have double checked, and secure boot is off, and boot from USB is set to enabled.

How do I boot my flash/Ubuntu installer drive in UEFI boot mode? Is it a setting in the setup of the flash drive itself?[/FONT][/COLOR]

---

### Post by oldfred on 2017-11-02
Not sure of your drive, but it says it really is 128GB times 2 on SSD & then also hard drive?
Is it using BIOS RAID or FakeRAID then?

With Linux usually recommended not to use proprietary RAID configurations.
I do not know RAID, but normal desktop installs do not have all the RAID drivers that are available.

       [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04 and later.
15.04 or later now uses mdadm to support intel fakeraids 
User who installed fakeRAID
How to install Ubuntu 14.04 in software fakeraid RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)

Some with FakeRAID systems, back up install and break the RAID converting system to two drives.
Those with RAID 0 have to back up system as part is on one drive and part on other drive, alternating stripes. 
Those with RAID 1 can just break RAID (but still need backup) as data is copied to each drive.

 [http://askubuntu.com/questions/660023/how-to-install-ubuntu-14-04-64-bit-with-a-dual-boot-raid-1-partition-on-an-uefi](http://askubuntu.com/questions/660023/how-to-install-ubuntu-14-04-64-bit-with-a-dual-boot-raid-1-partition-on-an-uefi)
Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

Often the dual SSD with RAID 0 are meant as gaming systems to be very fast, but then all data on SSD in RAID 0 needs really good backups or is data that does not have to be saved at all.

See also comment here on another RAID SSD system:
[https://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04](https://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04)

---

### Post by joakia on 2017-11-02
I attached some images of some of the BIOS/UEFI settings. 
What I don't understand is how I could install Linux Mint at one point, but I can't install Ubuntu.

---

### Post by oldfred on 2017-11-02
It looks like RAID 0 or a system designed for gaming.

If you break the RAID it will destroy Windows as RAID is striped (alternating stripes). 
Not sure how you do alternating stripes with SSD as they are totally different configuration.
And most find SSD fast enough, the RAID 0 was more for hard drives and did give faster response. 
The even newer NVMe drivers are even faster still.

I upgraded to a SATA SSD. I do find booting & loading new application to be very fast. But once in RAM, Linux caches everything. And RAM is orders of magnitude faster than a drive.
So if you have lots of RAM, you only use drive for loading data or saving data.
My SSD did not make my typing any faster, nor my Internet any faster.

Not sure if server version will install as it has more RAID drivers, then you can add the desktop of your choice. If you do not choose to add server software like database, Internet or other server software, you will end up with the same configuration as a desktop install.

---

### Post by joakia on 2017-11-02
The SSD is the one with Win10 on it. I don't want to touch that. The HDD is the one I want to install Ubuntu on, and as far as I can see it's not part of the RAID that Win10 is on.

---

### Post by oldfred on 2017-11-02
Do you have separate settings in UEFI for SSD as RAID, but set HDD as AHCI?

---

### Post by joakia on 2017-11-02
Yes, the SSD is RAID0, and the HDD is AHCI.

---

### Post by oldfred on 2017-11-02
Your UEFI boot screen shows UEFI boot on USB as first choice. 
So you should be able to boot USB flash drive in UEFI boot mode.
If not then it may be flash drive, ISO, or installer you used to install/extract ISO to flash drive.
Many with issues redo one or several of those and it then works. But not sure if just not done correctly first time or actual issue with flash drive or installer.

       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 
    
 Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 

      
 pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
USB flash drives Pendrive lifetime sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

---

### Post by joakia on 2017-11-02
Hey, it worked! I managed to boot Ubuntu from the USB in UEFI-mode. However, there are no drives showing up in the install menu of Ubuntu (see attached screenshot)..

---

### Post by oldfred on 2017-11-03
Is your sda seen as RAID, so then it will not show.
Does changing combo box at bottom to sdb show those partitions.

But UEFI install with Ubuntu will want to install grub to ESP on sda.And if not seen will be another issue to fix.

---

