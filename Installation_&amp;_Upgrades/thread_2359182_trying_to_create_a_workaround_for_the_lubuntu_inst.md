---
title: "trying to create a workaround for the lubuntu installer UEFI"
date: 2017-04-21
forum: Installation &amp; Upgrades
---

### Post by eatpancakes on 2017-04-21
I read a lot of documentation about UEFI after failing to install from USB to USB with every distro I tried. I understand every distro is different. this thread is specific to my experiences with the lubuntu 16.04 installer booted in UEFI either directly or from the lubuntu UEFI live USB created on rufus with windows. hardware is asus Z97-E with soft raid 0 (windows not in use) and linux UEFI USB. there were additional problems installing from the live USB desktop environment related to kernel automatically mounting things connected to USB. I forced unmount of the target install medium USB 8GB in terminal before using GPARTED gui. gparted has an error after scanning all the drives that partition can not be outside of partition? I assumed this was related to motherboard soft raid showing 3 devices for only 2 raid 0 SSD. I don't want to touch the SSD at all so I click the ignore button. I am running lubuntu live from a 16GB USB. all usb storage is usb 2.0. after unmounting the USB 8GB I deleted the partitions. then gparted told me to reboot before doing anything else so I reboot back into the live USB UEFI 16GB. this time the 8GB is not mounted. now I have gparted running and I create GPT on my 8GB device SDE. I create 300mb ESP in FAT32 after the first 1MB. I set flags BOOT and ESP in gparted. I create the remaining 7.3GB EXT4. I reboot into the 16GB UEFI directly to the UEFI lubuntu installer no desktop. I set the bootloader to my ESP FAT32 partition. I set the ext4 partition to mount point /    I choose to NOT format the ext4 to ext4 journaled. I do the graphical installation. it hangs the same way every time. note that I did not set a specific GUID or UUID. I tried no labels or partition names and I tried making my own labels and partition names. I read about placing the UUID in the label but I am not sure from the lubuntu UEFI documentation if this is required. I don't know if there are additional requirements from my motherboard manufacturer. so in summary I think the only way to get a working install of lubuntu booting natively in UEFI is to do a EFI install and start manually building all the required boot loaders from the lubuntu UEFI bootloader that does work after using rufus to make the ISO to UEFI USB. I think maybe the boot loaders can be changed completely without needing any different files on the EXT4 partition? should I simply DD my ext4 from a working installed EFI lubuntu installation? then edit the UEFI boot loader to point to the boot loader in ext4? does the lubuntu team want to work with me to create working UEFI support in the lubuntu graphical installer for Z97? here are pictures where the install gets stuck in an infinite loop.

tty7

[IMG]https://c1.staticflickr.com/3/2931/34048054081_83fe3243b9_b.jpg[/IMG]

this is tty1

[IMG]https://c1.staticflickr.com/3/2918/34138600876_d79001a198_b.jpg[/IMG]

---

### Post by oldfred on 2017-04-21
Not sure where your error is occurring.

But grub has to install to ESP on sda and with your RAID 0, it may not be seeing that correctly.
Not sure in your case how to make it work. 
You can always do a BIOS install, just also need bios_grub partition. And Boot-Repair normally can uninstall grub-pc and install grub-efi-amd64, but it is just running grub commands in background & grub may still want to install to sda's ESP, or fail if you do not have one.
Another alternative may be server install as that sees RAID better. Still issue that external drives only boot from /EFI/Boot/bootx64.efi which grub does not create except with total manual install of grub to external device. 

It is a real hassle to install UEFI to external drive. I have regularly installed to flash drives and it still will not let you specify install grub boot loader to sdb.
I change that on partitioning screen with Something Else install. And watching install, it even says installing to sdb. But always overwrites my main working install's ESP on sda. (Quickly learned to back that up.)

Even if ports are USB2, better to use USB3 flash drives. 
I found about 10% faster on my old BIOS system with only USB2 ports. And then compatible with newer USB3 ports if you also have them or will in future.

---

### Post by eatpancakes on 2017-04-21
I don't know if this matters but my intel raid controller on the motherboard is not SDA. it is SDD1 raid 0 efi partition, NTFS partition SDD2 raid 0 NTFS partition only. this also looks like gparted is not returning correct information since a raid 0 stripped array would be impossible to read individually and if it was reading it anyway it would contain the interlaced stripes on both drives. maybe the raid controller avoids 0 striping the EFI partition only? it does not look like the ESP flag is set on the raid 0 array but I also think this is garbage data in linux from the raid controller so I don't trust it either way. I actually don't want to make a permanent dual booting machine. or anyway if I did make changes permanent I would want that entire uefi boot loader OS menu on the USB drive without windows being modified at all. the way I understand it, I would eventually need to install the raid driver software in linux to support an OS select menu started from grub. that goal is secondary to me getting a 8GB USB drive to boot natively from the menu in the bios setup screen. my mother board remembers the last UEFI device that was booted via the bios setup screen for next boot. this is the perfect solution because it does NOT modify the windows install at all. no chance of damaging windows. it is reversible simply by removing the USB 8GB drive or by entering the bios setup screen. it dual boots just as good as msdos boot menu. it can be modified or scripted from linux both locally or remotely. its UEFI! so I understand I could do what is being suggested but I would like to develop the tools and techniques to do what I want to do. thanks for your help though as it does get me closer to the answer.

---

### Post by oldfred on 2017-04-21
If RAID is sdd, what drive is sda?

sudo parted -l

---

### Post by eatpancakes on 2017-04-21
you were correct. the two SSD in raid 0 are SDA and SDB. I think maybe I was looking at the 500GB WD external USB and thinking it was the raid 0 emulated drive but I was mistaken. strange that there is no SDC. some of the distros enumerated them as SDA SDA1 SDB SDB1.

```
lubuntu@lubuntu:~$ sudo parted -l

Error: Can't have a partition outside the disk!
Ignore/Cancel? i  

Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary               boot
 2      106MB   500GB  500GB  primary


Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start  End    Size   Type     File system  Flags
 1      4096B  250GB  250GB  primary  ntfs         boot


Model: WD 5000AAD External (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name                  Flags
 1      20.5kB  210MB  210MB  fat32        EFI System Partition  boot, esp
 2      211MB   500GB  500GB  ntfs         Basic data partition  msftdata


Model: SanDisk Cruzer Glide (scsi)
Disk /dev/sde: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  16.0GB  16.0GB  fat32        Microsoft Basic Data  msftdata


Model: Unknown (unknown)
Disk /dev/zram7: 519MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0.00B  519MB  519MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram5: 519MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0.00B  519MB  519MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram3: 519MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0.00B  519MB  519MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram1: 519MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0.00B  519MB  519MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram6: 519MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0.00B  519MB  519MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram4: 519MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0.00B  519MB  519MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram2: 519MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0.00B  519MB  519MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram0: 519MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0.00B  519MB  519MB  linux-swap(v1)



```

perhaps looking at my RAID 0 array as a place to install a boot loader  is a bit off topic as I am strongly against making changes to the  windows machine (SDA SDB). I really want to learn how UEFI works so I  can make changes to the live USB image that would effectively create a  patched installer. failing that I would like to know how to do the work  around with editing partitions and boot loaders manually to make it  work. if succesful, this lubuntu after it is installed to USB will be  UEFI, persistant, no swap, no ram disk, portable. I plan to use GEDA,  GCC, GIMP, PYTHON, PERL, SSH, GLSL HACKER, APACHE, and all the tools  from Kali. not wanting to build all these packages from source or go  through outdated or broken package managers, I decided I should  definitely use a debian or ubuntu flavor distro. manjaro and void run  great but they don't have all the up to date pre installed and/or pre-compiled apps. this is  why I am choosing lubuntu. this is why I want to help fix it not just  for me but for everybody. making my own distro seems a bit short sighted  since we all know that distro makers come and go. distros that have one  person behind them will eventually loose upstream updates when that  person is gone. maybe we can find out what exactly is breaking the  lubuntu UEFI install? I am happy to do any more tests that you need from me.  how much different is the ubuntu 16.04 graphical installer from the  lubuntu 16.04 graphical installer? does the ubuntu installer have features that the lubuntu installer does not?

---

### Post by oldfred on 2017-04-21
You can directly install grub to external drive.
I have done that for UEFI boot of just my ISO using grub2s loopmount.
I have used that for install ISO, repair ISO or something I want a quick test with. And where flash drive is 8 or 16GB.
With my larger flash drives I do a full install and system manages part of grub, but I add my own entries to 40_custom and turn off os-prober as too many installs on sda & sdb take forever to process.

You probably can do a full install in BIOS mode and then manually install grub-efi-amd64. The disadvantage is that you have to manually maintain your own grub.cfg to boot. And just about have to understand a bit more about UEFI booting.

       UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive) 
            ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive) 
    
On my flash drives I typically include both the ESP for UEFI boot and a bios_grub. Then I can convert install from UEFI to BIOS if desired. My old system was BIOS only and the had ESP for future use.

I saved these commands, not sure now if they all were mine, or copied from someone else.
 sudo grub-install --target=x86_64-efi --boot-directory=/mnt/sdb1/EFI/BOOT --efi-directory=/mnt/sdb1 --removable
mounted the USB EFI partition at /media/test and I installed grub with
sudo grub-install --target=x86_64-efi --efi-directory=/media/test --bootloader-id=grub --removable --recheck --debug
sudo mount -t vfat /dev/sdb1 /mnt -o uid=1000,gid=1000,umask=022
sudo grub-install --removable --boot-directory=/mnt/boot --efi-directory=/mnt/EFI/BOOT /dev/sdb

grub.cfg in efi partition with correct UUID & hdX,gptY partition. If directly booting not chainloading, hd0 is correct as boot drive is always hd0
search.fs_uuid a60289d6-c308-44f1-9ce6-85db3482ff32 root hd1,gpt1  
set prefix=($root)/boot/grub
configfile $prefix/grub.cfg

---

### Post by eatpancakes on 2017-04-22
oldfred thank you for doing all the research. your links are very helpful. this is exactly what I was looking for so I can learn how everything works. I wish I would have posted last night that **I got it working using some very low tech methods.** maybe I would have saved you some time. what I did was I used rufus in windows to DD the lubuntu 16.04 iso to the 16GB flash. I disconnected the SATA and USB cables for all the big NTFS drives. then I booted the 16GB in live UEFI so I could DD zeros to the 8GB. the lubuntu graphical installer was getting stuck because it has different methods for the "erase everything" option or the "something else" option. regardless if I have no partition table or if I setup the required UEFI partitions on the 8GB drive, the "something else" option will always get stuck. probably because of left over stuff that was not completely erased on the 8GB after using gparted to delete the partition table. DD zeros fixed it. then I rebooted to the 16GB UEFI directly to the lubuntu graphical installer. this time I selected "erase everything" then I selected SDB (8GB). I opted to install non-free plugins and codecs. I opted out of download updates during install to rule out any more variables. however I did have an internet connection during install and it did connect to the repos. [B]I was able to create a working UEFI installed OS on the target 8GB using the graphical installer that was provided without the need for modification.
[/B]
 the best part is that with full USB support in UEFI on this asus z97 it actually shuts down properly so that the usb ports don't fail in windows on first boot. on the asus forums there is a known bug that requires booting the windows OS twice in a row to regain functional usb ports from within windows OS. I also had to swap the two DVI cables to get the primary display on the left side. my monitors are different resolutions and refresh rates so there was no way to do a software setup of "monitors" gui from the lubuntu desktop without creating an unusable system. I could start editing conf files for xorg compiz or whatever is cool in 2017 but I decided to wait till I tried simpler methods. windows retained the left display right display settings regardless of ports used on the nvidia GTX 960 because it remembers the display not the port. linux has half the graphics settings remembering the display and the other half remembering the ports. I had to change my hardware to fix linux but windows is able to configure itself perfectly even when I change hardware. I noticed that the two biggest problems have fixes that depends on the user being educated about the limitations and bugs of free software. now I have two new bugs that are perhaps off topic to this thread but I will tell you anyway. I took critical security updates on my new lubuntu installed system that caused an error message about major system problems. this is possibly related to SDB enumerating as something else now that I have 3 more NTFS drives physically connected? or possibly there is another reason the update makes the system unstable? the second new bug is that there is no swap and no ram disk or maybe it is because there is a swap file hiding on my ext4 partition. I need to investigate but I don't think a system with 8GB DDR3 should be as slow as it is if it is using RAM for both swap and RAM. this also my fault for not taking the time to setup ram and swap like I know I should. I think it is probably a very common hardware setup that should already have a popular working preferred method of ram and swap from the people that make the distro/installer. the installers for most distros suggest creating a swap partition even if you have 5mb/s write on your disk but you have more than enough 8GB physical ram. the installer should be smarter than that. obviously the USB is the WRONG place to put anything that functions like ram. this is not a laptop therefor does not need low power modes like hibernate. the installer should already know I am not using a laptop.

in summary,** there should be info in the man pages for the lubuntu graphical installer that suggest a zero'd target install disk with the erase everything option if the user has intentions of booting the installer in UEFI to create a UEFI installed system on another target USB drive.** "something else" is not a working method for UEFI install. I did have network connected during the UEFI install so maybe it would be good if someone can test the same thing without network. put that info in the man pages also.

---

### Post by oldfred on 2017-04-22
Version 17.04 is doing away with swap partition and using swap file.

I find I have to make some settings in fstab to reduce writes to help speed system somewhat.
        change the fstab so that everything gets mounted with noatime. 
    Do not know now with swap file if tune2fs for swap still works or not.
You also can turn journal off. Better to use ext4 with journal off than ext2. Only suggested for smaller partitions as journal helps fsck if large partition.

 USB settings to help speed & life
[https://ubuntuforums.org/showthread.php?t=2350851&p=13600375#post13600375](https://ubuntuforums.org/showthread.php?t=2350851&p=13600375#post13600375)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites) 

You also do some of the same changes as SSD, its just trim is not supported with flash drives.
[https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Limit-the-write-actions-of-Firefox](https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Limit-the-write-actions-of-Firefox)

Some also with SSD create fstab entries for tmpfs. Not sure if you want to write a 4GB DVD you then need 4GB in tmpfs?

 No disk writes to tmpfs
tmpfs   /tmp    tmpfs   defaults,noatime,mode=1777      0       0
Making Ubuntu Fast using RAM (updated and simplified)
[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)

---

### Post by eatpancakes on 2017-04-22
thank you! best moderator ever!

---

### Post by oldfred on 2017-04-22
Glad to help. 

But next time I am in town, I expect you to share your pancakes. :)

---

### Post by eatpancakes on 2017-04-23
UPDATE: rufus in windows was causing problems. or maybe I was using rufus wrong. rufus has bugs. if you use rufus in DD mode with most distros in .ISO the result will be a mostly working live USB but that live USB will have a broken installer. the same is true if you have a damaged partition table or flag mismatch. I would need to test this twice to confirm but it looks like using rufus in win 7 to write an iso to usb in BIOS + MBR for UEFI + BIOS actually uses the ISO9960 but it can not setup the partition table, partitions and flags correctly if there is some weird pre-existing partition table. it may even be installing redundant UEFI  MBR. my bios boot menu shows 3 identical UEFI entries for one device but only one EFI/BIOS. if you try to boot the fake UEFI partitions from the bios menu you will be returned to the bios menu after 1 second black screen. then it dissipaters from the menu since it has no bootloader present only a valid UEFI partition. I finally fixed my problem by using rufus to create a half working live USB Ubuntu Mate 17.04 then from there I could DD zeros to the target install USB to prepare the drive for rufus later. rebooted to windows, used rufus in BIOS + MBR for UEFI + BIOS with Ubuntu Mate 17.04 .iso in ISO mode. this did create a proper working ISO9960 file system for the new live USB. I used this perfect ISO9960 live USB to do the UEFI install from UEFI! all the bugs related to power management, fast boot, fast shutdown, shutdown errors, shutdown triggering the double reboot windows no USB bug, all fixed! all the bugs related to updates crashing the system have been fixed. the installer scripts don't crash. I want to apologize for blaming the ubuntu installer scripts as being buggy. it was rufus, windows, bad flags on used USB drives that were hanging around. it would probably work fine with a new USB drive out of the box or just do what I did ping pong your way through the two drives till you get what you need. you do not need to worry about unplugging windows disks, the installer will ask what device to use for the erase everything option.

to confirm and show off what a working live USB of Ubuntu Mate 17.04 and  permanent install of Ubuntu Mate 17.04 USB actually look like in real  life here is sudo parted -l.

```
ubuntu-mate@ubuntu-mate:~$ sudo parted -l
Model: SanDisk Gaming Xbox 360 (scsi)
Disk /dev/sdc: 8036MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8036MB  8035MB  primary  fat32        boot, lba


Model: SanDisk Cruzer Glide (scsi)
Disk /dev/sdd: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   16.0GB  15.5GB  ext4

```

if you use rufus in GPT UEFI you will get a partition for ESP and a partition labelled "APPLE". don't waste your time with all that. the dual mode UEFI+non-UEFI works great on Z97.

---

### Post by eatpancakes on 2017-04-23
it is also super fast now with the live USB compared to before but that I can not understand.

---

