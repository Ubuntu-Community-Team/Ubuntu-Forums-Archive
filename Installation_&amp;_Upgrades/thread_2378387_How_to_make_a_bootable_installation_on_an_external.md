---
title: "How to make a bootable installation on an external SSD?"
date: 2017-11-22
forum: Installation &amp; Upgrades
---

### Post by lemmer on 2017-11-22
Hi,

after about a decade of partitioning and dual boot, I got a new computer, with Windows 10 Home. I don't know for sure, but I suppose it uses UEFI.

Well, I need to leave the Windows system untouched because I use it for some graphical suites, and I need Ubuntu for my programming (this months without it have been painful!).

I would love to have Ubuntu installed on an external SSD (I travel a lot and use it on the go, so it would be more robust than a HDD), but before purchasing I want to make sure it's actually doable.
I only found posts several years old. 
Can I install Ubuntu on an external SSD to boot via USB 3.0, and if yes, where can I find a tutorial? If not, what are my options? A flash drive is not viable because it's too slow.

My computer is an ultrabook, therefore I will not open it to unplug the internal SSD thus voiding the warranty.

Thank you in advance

---

### Post by ubfan1 on 2017-11-22
The basic problem is the lack of TRIM over USB3.  Everything you want is doable, with a little tweaking for the UEFI issues.  Install to the USB device, (regardless of what you specify for the location of the grub bootloader, it will get put onto the first disk's EFI partition in the /EFI/ubuntu directory.  Specify a 300M FAT32 partition on the USB for its EFI, and copy the internal disk's EFI partition over there (yea,even the Windows stuff, it's a good backup).  Now since the USB is considered a removable media, the acutal boot code run when you boot the device is /EFI/Boot/bootx64.efi (assuming a 64 boot, not 32).  The installer may not actually set that up correctly,so do it yourself -- copy /EFI/ubuntu/shimx64.efi and /EFI/ubuntu/grubx64.efi to /EFI/Boot (you may rename the existing bootx64.efi to bootx64.efi.sav if you want, it's probably just the Windows bootloader).  Then rename /EFI/Boot/shimx64.efi to /EFI/Boot/bootx64.efi.  That should be a bootable system by selecting the device at the EFI boot menu (some function key at power-up).  If the SSD in the USB encl. gets slow, maybe periodically remove it to an internal SATA connection on some other machine and run fstrim on it.

---

### Post by oldfred on 2017-11-22
I have installed multiple times to flash drives for UEFI boot. Functional, but writes especially installing is slow. But once application is in RAM it runs at same speed as any install.

Use gpt partitioning, I like to partition in advance. 
Only use Something Else install option.

System will boot from ESP from internal drive, but if you want to directly boot with UEFI or boot from other systems you must do the copy as discussed above in ubfan1's post. I like to do all that after install, but before rebooting as then partitions are more accessible. 

Some more info:
[https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration](https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration)

I just copy entire /EFI/ubuntu on internal drive's ESP to external drive's ESP twice. Once to /EFI/ubuntu and once to EFI/Boot. And then rename shimx64.efi to bootx64.efi.
 UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad

---

### Post by C.S.Cameron on 2017-11-22
My experience is that given lots of RAM Ubuntu on an external USB drive runs fast, even USB2.

---

### Post by lemmer on 2017-12-01
> **ubfan1 said:**
> The basic problem is the lack of TRIM over USB3.  Everything you want is doable, with a little tweaking for the UEFI issues.  Install to the USB device, (regardless of what you specify for the location of the grub bootloader, it will get put onto the first disk's EFI partition in the /EFI/ubuntu directory.  Specify a 300M FAT32 partition on the USB for its EFI, and copy the internal disk's EFI partition over there (yea,even the Windows stuff, it's a good backup).  Now since the USB is considered a removable media, the acutal boot code run when you boot the device is /EFI/Boot/bootx64.efi (assuming a 64 boot, not 32).  The installer may not actually set that up correctly,so do it yourself -- copy /EFI/ubuntu/shimx64.efi and /EFI/ubuntu/grubx64.efi to /EFI/Boot (you may rename the existing bootx64.efi to bootx64.efi.sav if you want, it's probably just the Windows bootloader).  Then rename /EFI/Boot/shimx64.efi to /EFI/Boot/bootx64.efi.  That should be a bootable system by selecting the device at the EFI boot menu (some function key at power-up).  If the SSD in the USB encl. gets slow, maybe periodically remove it to an internal SATA connection on some other machine and run fstrim on it.

Thank you. I don't understand the "install to the usb device" part. Should I use Win32DiskImager tool? Rufus? I used to use the cd-rom, but I haven't a cd drive now and I only have one usb 3.0 (the rest are usb-c) which will be occupied by the external ssd! However I do have a sd card slot and a 8gb sd card, but after having flashed the iso file (renamed to img) to it, it fails the "verify only" at 98%...

If I follow [this procedure ]("https://help.ubuntu.com/community/Installation/iso2usb") at the paragraph **For an UEFI only boot flash drive you need no installer** will it work? I don't get how putting an ISO on a FAT32 partition will give me a complete install... also I'd like to have my / in ext4!

Finally... how am I supposed to send those commands for copying the .efi files? From PowerShell? From Ubuntu running Live? From the installation process GUI? I am a total noob!

---

### Post by ubfan1 on 2017-12-01
I was referring to the SSD USB device.  The install media would also be on a USB stick, and assumed you could create it from Windows -- Rufus or unetbootin should work.  Boot the install stick, and install to the SSD, which then gets the ext4 root .   A UEFI install media (FAT32), contains all the bootloaders necessary, in the correct filesystem  locations to boot in UEFI mode, so you could mount the ISO and the FAT32 USB stick, and just copy all the file from the ISO to the stick.  Maybe put the boot flag on the the FAT partition, but nothing else should be needed.  Do the copy any way you are familiar with, any way you mentioned should work, they are just files.  Not sure what you mean with "renamed to img" -- I usually make SD card install media with a little USB reader, but using the SD card slot reader should be the same deal (with a different name), but I don't know how that would work under Windows.  I have no experience wth USBC, maybe they fixed the trim problem!

---

### Post by sudodus on 2017-12-01
> **lemmer said:**
> Hi,

after about a decade of partitioning and dual boot, I got a new computer, with Windows 10 Home. I don't know for sure, but I suppose it uses UEFI.

Well, I need to leave the Windows system untouched because I use it for some graphical suites, and I need Ubuntu for my programming (this months without it have been painful!).

I would love to have Ubuntu installed on an external SSD (I travel a lot and use it on the go, so it would be more robust than a HDD), but before purchasing I want to make sure it's actually doable.
I only found posts several years old. 
Can I install Ubuntu on an external SSD to boot via USB 3.0, and if yes, where can I find a tutorial? If not, what are my options? A flash drive is not viable because it's too slow.

My computer is an ultrabook, therefore I will not open it to unplug the internal SSD thus voiding the warranty.

Thank you in advance

Yes, it is possible, and there are newer instructions.

I suggest that you have a look at this link to AskUbuntu and links from it, I think they will be useful for you :-)

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

> **lemmer said:**
> Thank you. I don't understand the "install to the usb device" part. Should I use Win32DiskImager tool? Rufus? I used to use the cd-rom, but I haven't a cd drive now and I only have one usb 3.0 (the rest are usb-c) which will be occupied by the external ssd! However I do have a sd card slot and a 8gb sd card, but after having flashed the iso file (renamed to img) to it, it fails the "verify only" at 98%...

If I follow [this procedure ]("https://help.ubuntu.com/community/Installation/iso2usb") at the paragraph **For an UEFI only boot flash drive you need no installer** will it work? I don't get how putting an ISO on a FAT32 partition will give me a complete install... also I'd like to have my / in ext4!

Finally... how am I supposed to send those commands for copying the .efi files? From PowerShell? From Ubuntu running Live? From the installation process GUI? I am a total noob!

You can use several tools from Windows in order to create a USB boot pendrive, Win32DiskImager, Rufus, Unetbootin ... In this first step it is enough to create a live-only drive.

In the next step you boot from this live-only drive in order to install Ubuntu into the USB SSD drive (which is described in the link above and links from it).

**Edit:** Are you sure that unplugging the internal drive will void the guarantee? In that case, please check if the internal drive can be disabled via a UEFI/BIOS menu. It will make the installation to the SSD much easier.

---

### Post by oldfred on 2017-12-01
Do not confuse the installer which is normally a smaller flash drive which you use tools to create. Or just extract ISO to FAT32 formatted drive with boot flag. That is only an installer to allow you to create the full install on what ever drive you then want.

I copy files from ESP on internal drive to full install's ESP on flash drive, after install, but using the continue to test/use system in live mode. Full install mounts ESP with very limited permissions and is more difficult to see/use once booted into full install.
If only booting on one system, the having the .efi boot files on internal drive's ESP is not an issue.

---

### Post by lemmer on 2017-12-02
Alright, thank you everyone. I have quite an issue now but first let me sum up what happened before.

I used Win32DiskImager to burn the iso-renamed-to-img ubuntu file to a SD card. Writing was successful, verifying that not. Tried several times with no luck, even with other different SD cards and with the .ISO extension. md5sum of the original iso file is correct. 
I then performed the same with Rufus, but my computer won't allow boot from sd card. I managed to get a usb-c to usb-A adapter (to 2.0 speed!) because the stores around didn't have anything. 

I live tried ubuntu, flashed on a usb stick using rufus, I mounted my internal SSD.
On the external SSD I copied the EFI partition of the internal SSD by using GParted.
I subsequently launched the Ubuntu Installer from the Live and selected the Mount alongside Windows, with encryption, on the external SSD.
**Since I couldn't unplug the internal SSD and my UEFI/BIOS won't let me disable it, I found that keeping it mounted on Live while installing Ubuntu will prevent any change to that internal SSD.**
Installing was successful, I am now in live trying to perform what ubfan1 told me in the first answer. **Problem is: I cannot find shimx64 and grubx64 anywhere on my usb stick or external SSD. There's no /EFI/ubuntu folder either. What can I do?**

EDIT: this is an output
```
ubuntu@ubuntu:~$ sudo parted -l
Model: Lexar JumpDrive (scsi)
Disk /dev/sda: 7877MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  7877MB  7876MB  fat32        Microsoft Basic Data  msftdata


Model: SanDisk SDSSDA240G (scsi)
Disk /dev/sdb: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  316MB  315MB  fat32        EFI                   msftdata
 2      336MB   839MB  503MB  fat32        EFI System Partition  boot, esp
 3      839MB   240GB  239GB  ext4


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 2147MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  2147MB  2147MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/nvme0n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  274MB  273MB   fat32        EFI system partition          boot, esp
 2      274MB   290MB  16.8MB               Microsoft reserved partition  msftres
 3      290MB   497GB  497GB   ntfs         Basic data partition          msftdata
 4      497GB   499GB  1884MB  ntfs                                       hidden, diag
 5      499GB   512GB  12.7GB  ntfs         Basic data partition          hidden, msftdata


```

EDIT.2: by opening the external ssd (sandisk 240 gb) with gparted I could see this:
```
/dev/sdc1 is a fat32 partition, size 300 MiB, the one I copied from the internal SSD before the installation, flags msftdata, there's a key icon near /dev/sdc1
unallocated 19 MiB (where does this come from? Maybe encryption?)
/dev/sdc2 fat32, size 479.99 MiB, of which 980.5 KiB are used, flags boot,esp it's my ESP, created by the installer
after /dev/sdc3 which comprises my root and home (encrypted), there are 12.08 unallocated MiB. Are they due to encryption?
```

EDIT 3: If I unplug the flash drive and boot from the external ssd it works, and the boot menu allows me to select to boot windows from the nvme internal storage. However if I do that I get an error that says that files have been changed and I should plug in a recovery stick. It let's me enter the UEFI settings, from which I can reaccess grub and boot ubuntu. 
If I unplug everything and just boot Windows, grub is loaded with "minimal BASH-like editing supported". If i enter the exit command then Windows will boot.

How do I get a situation where if nothing is plugged in, Windows will boot directly, and if I do plug in the external SSD, grub will allow me to choose which system to boot and actually let me boot Windows (even if I use the disk only for Ubuntu actually)

---

### Post by ubfan1 on 2017-12-02
The UEFI bootloaders may be found  on the install media USB in /EFI/BOOT, with names BOOTx64.EFI  grubx64.efi (shimx64.efi has already been renamed to BOOTx64.efi).  Just copy those files onto the SSD's EFI of the same directory (so if you mount the EFI at /mnt/foo, the copy will be to /mnt/foo/EFI/BOOT).  With an encrypted root, you probably need an unencrypted boot, ext4 filesystem, but I'm unfamiliar with the details of setting that up.  Mounting the internal disk seems to be a really good trick, I'll remember that since it's far easier than unplugging it. You can set up the boot order to boot the external SSD before the internal disk, and when that external disk is not present, have the UEFI boot order put Windows before shim/grub.  Don't worry about any /EFI/ubuntu directories on the internal disk, they won't interfere with a Windows boot.  What might need changing is the boot order to put Windows after the external SSD, and before the internal grub/shim, which you can alter with efibootmgr (or just delete the internal grub/shim entry).
The other item needed in the EFI is a grub.cfg file.  A full one may be used, but then you'd have to edit/replace it after every kernel update, so better to use a stub which pulls in the maintained grub.cfg file from the  /boot/grub directory (and that's another problem with an encrypted root, not sure how that works).  Maybe leave off the encryption for now until you get things working. Get the UUID below for the  root with  the sudo blkid command, and alter the disk/partition to be the correct gpt?
===Example grub.cfg
search.fs_uuid <your UUID Here> root hd1,gpt2  
set prefix=($root)/boot/grub
configfile $prefix/grub.cfg

---

### Post by oldfred on 2017-12-02
I think you have again mixed installer and its creation with an actual install and its creation.

The installer is often just one FAT32 formatted flash drive. 
It can be a DVD, or if already using Ubuntu can be in a partition on a drive. But difficult to install from an installer to same device as you have to unmount and only have installer in RAM. And if any issue, you end up partially overwriting installer on drive you are installing into and have to start all over.

While UEFI spec does say you can have more than one ESP, I have yet to see a system that works with two. So you can have multiple FAT32 partitions, only one should have boot flag, if using gparted or similar tools that use boot flag to make partition ESP - efi system partition.
You now show two ESPs???

The Ubuntu full drive encryption uses LVM which is an advanced partitioning (Logical Volumes). Unless you must have full drive encryption, better to not use LVM as it requires even more understanding and different tools to manage it. Start with a standard install. Later you can reinstall with encryption. There also is encryption of just /home or you can just encrypt a data partition.

---

### Post by lemmer on 2017-12-02
> **ubfan1 said:**
> The UEFI bootloaders may be found  on the install media USB in /EFI/BOOT, with names BOOTx64.EFI  grubx64.efi (shimx64.efi has already been renamed to BOOTx64.efi).  Just copy those files onto the SSD's EFI of the same directory (so if you mount the EFI at /mnt/foo, the copy will be to /mnt/foo/EFI/BOOT).  With an encrypted root, you probably need an unencrypted boot, ext4 filesystem, but I'm unfamiliar with the details of setting that up.  Mounting the internal disk seems to be a really good trick, I'll remember that since it's far easier than unplugging it. You can set up the boot order to boot the external SSD before the internal disk, and when that external disk is not present, have the UEFI boot order put Windows before shim/grub.  Don't worry about any /EFI/ubuntu directories on the internal disk, they won't interfere with a Windows boot.  What might need changing is the boot order to put Windows after the external SSD, and before the internal grub/shim, which you can alter with efibootmgr (or just delete the internal grub/shim entry).
The other item needed in the EFI is a grub.cfg file.  A full one may be used, but then you'd have to edit/replace it after every kernel update, so better to use a stub which pulls in the maintained grub.cfg file from the  /boot/grub directory (and that's another problem with an encrypted root, not sure how that works).  Maybe leave off the encryption for now until you get things working. Get the UUID below for the  root with  the sudo blkid command, and alter the disk/partition to be the correct gpt?
===Example grub.cfg
search.fs_uuid <your UUID Here> root hd1,gpt2  
set prefix=($root)/boot/grub
configfile $prefix/grub.cfg

It turned out that CUDA 8.0, which I need to run Tensorflow, only supports Ubuntu 16.04, so I will redo the whole process with Ubuntu 16.04 and this time I will manually partition the disk in order to separate / and home and encrypt only the latter. I will then try to change boot order, I remember having put Windows in the last position some days ago.

---

### Post by lemmer on 2017-12-02
> **oldfred said:**
> I think you have again mixed installer and its creation with an actual install and its creation.

The installer is often just one FAT32 formatted flash drive. 
It can be a DVD, or if already using Ubuntu can be in a partition on a drive. But difficult to install from an installer to same device as you have to unmount and only have installer in RAM. And if any issue, you end up partially overwriting installer on drive you are installing into and have to start all over.

While UEFI spec does say you can have more than one ESP, I have yet to see a system that works with two. So you can have multiple FAT32 partitions, only one should have boot flag, if using gparted or similar tools that use boot flag to make partition ESP - efi system partition.
You now show two ESPs???

The Ubuntu full drive encryption uses LVM which is an advanced partitioning (Logical Volumes). Unless you must have full drive encryption, better to not use LVM as it requires even more understanding and different tools to manage it. Start with a standard install. Later you can reinstall with encryption. There also is encryption of just /home or you can just encrypt a data partition.

Yeah I think the fact that I have the 2 ESPs is due to the fact that before installing I performed a copy of the internal SSD ESP to the external SSD using Gparted from Live. Thus when I installed Ubuntu it added its own ESP, tagged boot, esp, and changed the copy of the Windows one to flair msconfig or something and encrypted that one as well. 

I have to redo everything using Ubuntu 16.04 instead of 17.10, maybe I'll try encrypt only the home partition?

---

