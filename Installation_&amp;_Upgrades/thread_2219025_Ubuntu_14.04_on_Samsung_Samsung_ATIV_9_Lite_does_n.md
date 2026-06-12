---
title: "Ubuntu 14.04 on Samsung Samsung ATIV 9 Lite does not boot"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by aridus on 2014-04-22
I have installed Ubuntu 14.04 on a Samsung Samsung ATIV 9 Lite ultrabook (128 GB SSD), replacing windows (see [http://ubuntuforums.org/showthread.php?t=2218299](http://ubuntuforums.org/showthread.php?t=2218299)). After installation the computer restarts successfully but if I then shut down it will not reboot (a system message appears indicating that all boot options have been tried). I can edit the boot options in the UEFI BIOS (secure boot on/off, fast boot on/off, UEFI OS, UEFI + CMS OS, and a few others) but, although I have tried various options, I am unable to boot the system. I have run the install several times to check but always with the same result. Following installation and the first restart I can use the system as long as I 'close' by shutting the lid (i.e. suspend) but not if I shut down and reboot. Herewith some details:

* /etc/fstab

# /etc/fstab: static file system information. 
# 
# Use 'blkid' to print the universally unique identifier for a 
# device; this may be used with UUID= as a more robust way to name devices 
# that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
# / was on /dev/sda2 during installation 
UUID=9798e825-b143-413a-901c-6ffa8c4f4ed4 /               ext4    errors=remount-ro 0       1 
# /boot/efi was on /dev/sda1 during installation 
UUID=C9D5-B2A5  /boot/efi       vfat    defaults        0       1 
# /home was on /dev/sda4 during installation 
UUID=d92fb0f9-b5fb-435c-bb89-6d7bb34c7073 /home           ext4    defaults        0       2 
# swap was on /dev/sda3 during installation 
UUID=a49fc487-0987-46a5-b4ad-055416191df2 none            swap    sw              0       0

Having done some reading I checked various things:

*Using 'grub-probe -t device /boot/grub' responds

/dev/sda2

*I tried 'sudo update-grub' and it responded 

Generating grub configuration file ... 
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported. 
Found linux image: /boot/vmlinuz-3.13.0-24-generic 
Found initrd image: /boot/initrd.img-3.13.0-24-generic 
Adding boot menu entry for EFI firmware configuration 
done

*Using 'sudo grub-install --recheck /dev/sda2' responded 
Installing for x86_64-efi platform. 
Installation finished. No error reported.

*Here is the output of 'sudo parted -l'

Model: ATA SAMSUNG MZMTD128 (scsi) 
Disk /dev/sda: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 

Number  Start   End     Size    File system     Name  Flags 
 1      1049kB  538MB   537MB   fat32                 boot 
 2      538MB   21.5GB  21.0GB  ext4 
 4      21.5GB  124GB   103GB   ext4 
 3      124GB   128GB   3698MB  linux-swap(v1) 

Model: TDK  (scsi) 
Disk /dev/sdc: 4005MB 
Sector size (logical/physical): 512B/512B 
Partition Table: msdos 

Number  Start   End     Size    Type     File system  Flags 
 1      31.7kB  4005MB  4004MB  primary  fat32        boot, lba 


I am stumped (I am not knowledgeable about Ubuntu but have gleaned that the above details may be relevant to somebody who may know better than me).

I would be grateful if anybody could suggest what is wrong with this installation and how I may rectify it (at the moment there is not data on the computer so I can do anything that is necessary to solve this problem without worrying about backups etc).

With grateful thanks, Martin

---

### Post by aridus on 2014-04-22
Herewith some more information to my original post. I used boot-repair to attempt to repair the boot. It appeared to do so and, upon reboot, the Grub menu appeared and I could boot into ubuntu 14.04. However, upon a shut down and reboot the same error message appeared (..all boot options have been tried...) and the grub menu did not appear. The output of  boot-repair is at [http://paste.ubuntu.com/7310052/](http://paste.ubuntu.com/7310052/)

If anybody has any ideas I would love to hear them!

With thanks.

---

### Post by aridus on 2014-04-25
No replies but no problem. I have resolved this issue now and provide it here in case anybody with the same problem finds their way to this thread. I had to do three things:

(1) During installation of Ubuntu, when choosing the 'Do something else' option, it is necessary to specify at the bottom not the disk (e.g. sda, as one would do for a computer with an older-style BIOS) but rather the efi boot partition (e.g., in my case, sda1).

(2) Disable secure boot, fast boot and all other options in the EFI BIOS (one can access this at boot, from the Samsung splash screen, by pressing and holding F2).

(3) I then used boot-repair ([http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)), booting it from a USB stick, to fix the boot (I did not need to use the advanced options).

---

### Post by oldfred on 2014-04-25
Because you have only one install you should not normally get a grub menu. It should just boot Ubuntu. But if shutdown is not normal it sets a flag and then grub menu will appear to give you option to run recovery mode if need be.

But it seems like you issue is more related to UEFI.

But where is boot of 000B coming from? And you still have a Windows entry in UEFI.
```
efibootmgr -v
BootCurrent: 000B
Timeout: 0 seconds
BootOrder: 0001,0009,000A,0000
Boot0000* Windows Boot Manager	Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...0................
Boot0001* ubuntu	HD(1,800,100000,b29af792-01d7-4b0a-8a5e-7de28893786d)File(EFIubuntushimx64.efi)
Boot0009* UEFI:  8.07	ACPI(a0341d0,0)PCI(12,2)USB(1,0)HD(1,e28,39e1d8,000f237c)..BO
Boot000A*  8.07	BIOS(5,0,00)..BO
```

       sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

