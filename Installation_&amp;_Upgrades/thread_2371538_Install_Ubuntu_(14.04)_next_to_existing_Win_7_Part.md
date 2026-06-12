---
title: "Install Ubuntu (14.04) next to existing Win 7 Partition, is dual-boot possible?"
date: 2017-09-15
forum: Installation &amp; Upgrades
---

### Post by ikehaze on 2017-09-15
Hi,

I've just installed Ubuntu 14.04 LTS next to an existing Win 7. 
In the process I created 2 new partitions: one smaller SWAP partition and  a EXT4 partition for the Ubuntu OS.

Now, when I start my computer, it will directly boot into Ubuntu, without offering me a choice to either boot Ubuntu or  the still existent  Windows 7 OS. What I actually want is the dual-boot option, where during the startup I get to choose whether I want to start one or the other. What can I do to achieve this??

I urgently need to access my Win 7 OS, because that's where all my main programs and data are stored. It's my main OS so to speak! 

My computer: HP Probook 440 G3. As far as I can tell it uses an UEFI based boot, but I'm not completely sure. When I put: 

[B][FONT=courier new][ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 

[/FONT][/B]it tells me: 

[B][FONT=courier new]Legacy boot on HDD
[/FONT][/B]
Maybe Ubuntu is installed in BIOS mode? I'm confused.[B][FONT=courier new]
[/FONT][/B]

---

### Post by DAB4970 on 2017-09-15
Yes, dual boot is possible.  I don't recommend it, unless each OS is on separate HDD.  It's been a few years since I last had a dual boot config.  Your issue has to do with Grub.  Try either of these 2 links:

[https://askubuntu.com/questions/210914/grub-does-not-show-a-windows-8-option-after-dual-boot](https://askubuntu.com/questions/210914/grub-does-not-show-a-windows-8-option-after-dual-boot)

[https://askubuntu.com/questions/128233/windows-7-and-ubuntu-12-04-dual-boot-grub-not-showing](https://askubuntu.com/questions/128233/windows-7-and-ubuntu-12-04-dual-boot-grub-not-showing)

---

### Post by oldfred on 2017-09-16
Most Windows 7 installs were/are BIOS/MBR configuration.

Have you run this?
sudo update-grub

If that does not add Windows to grub menu run this:
       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by efflandt on 2017-09-16
Can you access your Windows partition(s) from Linux ("+ Other Locations" in file manager)? Linux will refuse to mount Windows partitions marked as dirty (that need Windows chkdsk run on them) or if Windows was in hibernation. Do Windows partitions still show up if in a terminal window you do "sudo parted -l" (blindly carefully enter your normal user password when sudo requests it).

Did you originally have unallocated space on the drive? Or if you needed to make space on the drive, did you use Windows' own Disk Management to shrink its partition then reboot to make sure that was all working before installing Ubuntu?

I have Win7 and 14.04 on my hard drive. But Windows was using 3 partitions (sda1 utility, sda2 Recovery, sda3 OS) actually booting from sda2. So I originally shrunk Win7's OS partition with its own tools, and installed Ubuntu 14.04 on primary partition sda4 with no swap (I had 8 GB RAM and now have 16 GB). Originally there was an issue of some Windows programs storing data in what they thought was an unused part of the MBR, but that would interfere with grub2 which was larger than the Win MBR. I think that has been fixed by grub2 avoiding using part of the MBR that known programs used. But another issue is that occasionally certain Win7 updates will fail if Windows cannot reboot itself with its own MBR. So I installed grub on my primary Linux partition sda4 and set the boot flag to that partition. If a Win7 update fails, I can switch the boot flag to sda2 (using live/install system, or I also have newer Ubuntu on SSD sdb1) and try the Windows update again.

When I bought an MSI gaming laptop in 2013 while I could still get Win7, its BIOS was capable of UEFI, but their laptops with Win7 had BIOS that defaulted to legacy BIOS, and with Win8 or newer had different BIOS that defaulted to UEFI. I had a Lenovo all-in-one at work that came with Win8.1, but actually used legacy BIOS with msdos partitions.

The reason my Linux partitions are so big is that I do Steam gaming.```
~$ sudo parted -l
Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  57.6MB  57.5MB  primary  fat32        diag
 2      57.6MB  12.7GB  12.6GB  primary  ntfs
 3      12.7GB  549GB   537GB   primary  ntfs
 4      549GB   1000GB  451GB   primary  ext4         boot


Model: ATA Crucial_CT512M55 (scsi)
Disk /dev/sdb: 512GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  512GB  512GB  primary  ext4         boot


~$ sudo blkid
/dev/sda1: UUID="EED2-7775" TYPE="vfat" PARTUUID="2fb1db22-01"
/dev/sda2: LABEL="RECOVERY" UUID="E6CAD622CAD5EF35" TYPE="ntfs" PARTUUID="2fb1db22-02"
/dev/sda3: LABEL="OS" UUID="6440DA0C40D9E538" TYPE="ntfs" PARTUUID="2fb1db22-03"
/dev/sda4: UUID="b226357c-b349-498a-8bba-1ea7bed78d43" TYPE="ext4" PTTYPE="dos" PARTUUID="2fb1db22-04"
/dev/sdb1: UUID="6787eaaf-0994-4467-897b-538f5c624731" TYPE="ext4" PARTUUID="7e78a7d3-01"
```I can actually boot anything from either drive by itself depending upon which I set in BIOS as the boot drive. So ideally if you could use a separate drive for Linux, you would use "Other" during the partitioning part of install, and assuming that it is using legacy BIOS with msdos partitions, could use the drop down list to install grub to 2nd drive, leaving Windows drive untouched, and set 2nd drive as boot drive.

---

### Post by Bucky Ball on 2017-09-16
> **DAB4970 said:**
> Yes, dual boot is possible.  I don't recommend it, unless each OS is on separate HDD.

I've haven't dual-booted any other way than with both OSs on the same drive since I've been using Linux. Not an issue if you get it right (and have a reliable backup before proceeding!). ;)

This is particurly relevant when it comes to running with one SSD. They're faster than a HDD so you want the OSs on the SSD, not the HDD. This setup, OSs on the SSD and data storage on the HDD, is common.

Both on same drive or on separate drives. Either way works, so whatever suits.

---

