---
title: "MultiBootUSB problems booting"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by SuperFreak on 2013-10-18
I am trying to use MultiBootUSB [https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk]("https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk"). I have created the USB with isos but when I try booting from the USB I get this error message:

Missing Operating System
Error: Invalid Arch 
Independent ELF Magic
Grub Rescue>



I have tried booting in UEFI mode and BIOS mode

---

### Post by SuperFreak on 2013-10-19
OK I tried preparing a YUMI USB disk (according to directions [Here]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/"))
and get the same error message on Boot. I tried using the YUMI to rebuild SySLinux to no avail. My UEFI Bios gives me two boot options either USB: Patriot Mem PMap or UEFI: Patriot Mem PMap I have tried both and they won't work. Fast Boot is disabled and legacy USB is enabled

Is this problem related to UEFI?

---

### Post by oldfred on 2013-10-19
Invalid elf is often grub in MBR (or efi?) is different version than grub in partition, so files do not match.
Missing kernel is where path or mount in boot stanza is not correct. I have several flash drives and also hard drive versions and when I copy grub from one to another sometimes get that error when I have not correctly updated grub boot stanza.

Do not have UEFI, so have not tried from that. But you should be able to create a UEFI bootable grub and add boot stanza the same way. I do use BIOS but have partitioned my newer flash drives with gpt and that has worked.

So with UEFI you would need gpt partitioning on flash drive, with an efi partition.
       sudo grub-install --target=x86_64-efi --boot-directory=/mnt/sdb1/EFI/BOOT --efi-directory=/mnt/sdb1 --removable

You should also be able to copy signed versions.
 Bootable UEFI USB Key 
[http://ubuntuforums.org/showthread.php?t=2015019](http://ubuntuforums.org/showthread.php?t=2015019)
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
If you are unable to launch UEFI Shell from the firmware directly using any of the above mentioned methods, create a FAT32 USB pen drive with Shell.efi copied as (USB)/efi/boot/bootx64.efi . This USB should come up in the firmware boot menu. Launching this option will launch the UEFI Shell for you.
Manually copy efi files to efi partition on flash drive. Toshiba Satellite S855-5378
[http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515](http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515)
On the Ubuntu filessystem, you should have the signed versions of the following: /usr/lib/shm/shim.efi.signed, /usr/lic/grub/x86_64-efi-signed/grubx64.efi.signed, and /usr/lib/grub/x86_64-efi-signed/gcdx64.efi.signed. 
Copy them all onto the USB stick .../EFI/ubuntu directory without the ".signed" extension. 
Then copy and rename the shim.efi to the USB .../EFI/Boot/bootx64.efi. 
Also copy the grubx64.efi to the EFI/Boot/grubx64.efi. 
There should be the working grub.cfg in the USB .../EFI/ubuntu/grub.cfg

---

### Post by SuperFreak on 2013-10-19
> So with UEFI you would need gpt partitioning on flash drive, with an efi partition.
sudo grub-install --target=x86_64-efi --boot-directory=/mnt/sdb1/EFI/BOOT --efi-directory=/mnt/sdb1 --removable

Thanks, just before you posted this I was setting the USB partition in gpt mode from msdos. It didn't work still presumably because I didn't put the EFI partition in. So I have created a small unallocated space of 355 MB in the USB (sdd). What would I format that to FAT32? And then use the command you listed replacing sdb1 with sdd2?

---

### Post by oldfred on 2013-10-19
the UEFI spec says it is supposed to be first and formatted FAT32, but FAT16 allowed for removeable devices. So format to FAT32 with gparted and set boot flag to make it the efi or ESP partition.
Windows often have efi partition second or third so it must not be a strict requirement to be first.

---

### Post by SuperFreak on 2013-10-19
Just tried it (see attach.) but got same error message. I  will try all over again with EFI in first partition. Do I need to put something into that partition (ie as your command in post #3 suggested with the sudo command?)

---

### Post by oldfred on 2013-10-19
You do have to have efi boot files in the efi partition to boot. 

I created a new USB flash drive, but do not have UEFI, but used gpt and created both an efi partition for future use and a bios-grub partition for current use. You can only boot one way or the other and I am not sure if you can have grub boot either way or install both grub-efi and grub-pc.  The Ubuntu live installer uses grub for efi boot and syslinux for BIOS boot. About half is for install and other half for data.

```
Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              40       976,895       976,856 EFI System partition
/dev/sdb2         976,896       978,943         2,048 BIOS Boot partition
/dev/sdb3         978,944    29,650,943    28,672,000 Data partition (Windows/Linux)
/dev/sdb4      29,650,944    60,532,735    30,881,792 Data partition (Windows/Linux)

```

---

### Post by SuperFreak on 2013-10-19
Would Boot Repair put the EFI file in place?
I will have a look at the thread you linked but there is a great deal of material so it may take some time

---

### Post by SuperFreak on 2013-10-19
Found this on a [Win 8 thread ]("http://community.futuremark.com/forum/showthread.php?171201-YUMI-(bootable-USB-creator)-and-Windows-8-problems")which explains why I can't get it to work
> I emailed the people at pendrivelinux.com and they told me that YUMI doesnt support booting from UEFI systems, so there it is the problem. Is a compatibility issue. Hope this helps to other people.

---

### Post by oldfred on 2013-10-19
Does yummi not use grub2, that would be why they do not work with UEFI. 

But that does not stop you from creating your own, just more work.

---

### Post by SuperFreak on 2013-10-19
From [YUMI web site]("YUMI uses syslinux to boot extracted distributions stored on the USB device, and reverts to using grub to Boot Multiple ISO files from USB, if necessary.") >  YUMI uses syslinux to boot extracted distributions stored on the USB device, and reverts to using grub to Boot Multiple ISO files from USB, if necessary.
I am not sure if I have the ability to make it work. Does Boot Repair have the capability to fix this?


OldFred I tried [THIS]("http://ubuntuforums.org/showthread.php?t=1288604") which was a link on one of your threads. It will boot to GRUB using those instructions but there is a very limited number of ISOs available

---

### Post by oldfred on 2013-10-20
If you want to boot in BIOS mode with grub2 that is relatively easy, it is just the new UEFI part that I do not know.

I still use gpt partitioned flash drive, I even have an efi partition on my flash drive as I want new system soon, but have to have the bios_grub partition to boot with BIOS. Example above in post #7. 

I then just install grub2 to flash drive, copy or create my old grub.cfg with any loopmount bootable ISO. Some so not loopmount. 

       Multiple-Boot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
Examples:
Label partition - if label is grub2 & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
Newer versions automount with $USER name also, this one labeled MC4GB
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
Install grub2 2.00 boot loader to gpt partitioned flash drive from Raring (it used media/fred as mount)
mount and label is PreciseInstaller and flash is sde. Note space before /dev/sde
sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde
This will create a grub.cfg or you can just copy your own grub.cfg into /boot/grub
sudo grub-mkconfig -o /media/fred/PreciseInstaller/boot/grub/grub.cfg
Only if Linux formatted, easier with wide open permissions. 777 otherwise not normally suggested.
sudo chmod 777 -R /media/fred/PreciseInstaller/boot

If you directly boot a flash drive it will be sda and in grub hd0. If you have the efi & bios_grub partitions, then it may not be hd0,1, but hd0,3 or whatever partition number your iso folder is.

      
 This will boot an ISO from a hard drive. with hard drive you may have different drive & partition settings, but otherwise the examples  are the same.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by SuperFreak on 2013-10-20
Thanks for your help. I am a bit hesitant to try this but will keep this thread as reference should I give it a go

---

### Post by SuperFreak on 2013-11-04
Found [Easy2Boot]("http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1")
It seems to work with UEFI and Linux and has over 100 ISOs(both Windows and Linux ISOs) that will work with it. I am testing it out now. Looks promising and is relatively easy to install on a USB key

edit: Most of the isos work fine, but a few of those listed on the site needed to be updated to more recent or 64 bit versions (Eg Gparted, UBCD)
This will become a very useful tool to keep on hand for emergency disc repair software and keeping different distros and versions of Lnux

---

