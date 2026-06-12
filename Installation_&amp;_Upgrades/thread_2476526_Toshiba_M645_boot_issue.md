---
title: "Toshiba M645 boot issue"
date: 2022-06-28
forum: Installation &amp; Upgrades
---

### Post by wmbarrow on 2022-06-28
here is the boot repair info = [https://paste.ubuntu.com/p/Ttw4Xcjmk2/](https://paste.ubuntu.com/p/Ttw4Xcjmk2/)
I have tried changing everything in the Bios to try and get a boot but unable to achieve a boot.
On this laptop, a boot from usb using non legacy mode doesn't work so not able to click the repair button required by boot-repair.
Any help would be greatly appreciated.
Thanks,

---

### Post by yancek on 2022-06-29
Did you read and/or try the suggestion in boot repair to reboot the USB in Legacy mode?  If so, what happened?  Do you have any UEFI options in the BIOS firmware?  How old is this computer?

Your boot repair output at the very top shows you have Grub installed in the MBR which means you have a Legacy install..  Line 11 shows GPT disk so you need the unformatted BIOS Boot partition, in your case sda1.  You also have an EFI partition on sda2 (beginning on line 28).  You use either/or, not both.  If you want a Legacy install on a GPT disk you need the BIOS Boot partition (sda1) and the EFI partition (sda2) is useless.  If you want an EFI install which is recommended on GPT disks, you need the EFI partition and the BIOS Boot partition is useless.

If you want an EFI install, you need to have UEFI enabled in the BIOS and you need to boot the USB on which you have boot repair in UEFI mode to make that repair.   You indicate as I read it, that you cannot do this.  Do you not have any UEFI option in the BIOS firmware?  Line 70 of boot repair indicates the hardware seems UEFI compatible??

---

### Post by wmbarrow on 2022-06-29
I do not have a UEFI option in the BIOS so does that mean I simply remove sda2 partition?

---

### Post by tea for one on 2022-06-29
Can you provide any details about how you have an EFI partition (ESP) yet you do not have a UEFI option in your firmware?

The boot-repair report states in [COLOR="#0000FF"]Line 70[/COLOR] that [COLOR="#0000FF"]The firmware seems EFI-compatible[/COLOR]

First of all, if you are convinced that you do not have UEFI firmware, then you should be able to boot the OS in Legacy mode without difficulty.
However, somehow you also have an ESP?

Did you try to install Ubuntu more than once?

---

### Post by wmbarrow on 2022-06-29
This model Toshiba simply doesn't have UEFI but for some reason the installer thinks it does. Here is another post that calls out this issue on that particular Laptop as well ([https://ubuntuforums.org/showthread.php?t=1977023](https://ubuntuforums.org/showthread.php?t=1977023)).
I did try to install it more than once. I've tried like 3 or 4 times.

---

### Post by tea for one on 2022-06-29
> **wmbarrow said:**
> This model Toshiba simply doesn't have UEFI but for some reason the installer thinks it does. Here is another post that calls out this issue on that particular Laptop as well ([https://ubuntuforums.org/showthread.php?t=1977023](https://ubuntuforums.org/showthread.php?t=1977023)).
I did try to install it more than once. I've tried like 3 or 4 times.

Not only the installer thinks that you have UEFI but also boot-repair?
Anyway, assuming that you have saved any/all  personal data, why not remove the EFI partition and see if it boots in Legacy mode?

Alternatively, re-install in Legacy mode with msdos partition table but check that you have booted in Legacy mode with this command:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```

---

### Post by yancek on 2022-06-29
> I do not have a UEFI option in the BIOS so does that mean I simply remove sda2 partition? 		 

			 			Did you read and/or try the suggestion in boot repair to reboot the USB in Legacy mode?  Could you do that and try the repair.  If you have no UEFI options then sda2, the EFI partition is not used. or needed.  I would verify the ability to boot in Legacy mode before deleting it.

---

### Post by oldfred on 2022-06-29
It looks like system is from approx 2011.
In 2012Microsoft required vendors to only install Windows 8 in UEFI boot mode to gpt partitioned drives.
To start conversion to UEFI, some vendors started to use UEFI with last production of Windows 7.
Often that UEFI was buggy & needed updates and Linux often had to make changes to work around some of the bugs.
Many settled for BIOS installs which still should work without issue, but if drive is gpt, you must have the bios_grub partition for grub to install.


You show mount of ESP - efi system partition in fstab, so last install was in UEFI boot mode.
And then you have to boot install in UEFI mode.
Does f12 show an "ubuntu" boot option?
This shows the details where UEFI may just say ubuntu (must be UEFI boot). This is not shown in report as you booted in BIOS/Legacy/CSM mode.
sudo efibootmgr -v

---

### Post by wmbarrow on 2022-06-29
I checked and the usb live version is in legacy mode but the installer still wants to install ESP. I'm still at a loss for installing this.

---

### Post by oldfred on 2022-06-29
Have not done any BIOS installs recently.
But have seen where BIOS installer adds an ESP. I assume since most systems are really UEFI, it makes it easier to convert to UEFI if an ESP exists.
But you have UEFI boot files, so had to have installed in UEFI boot mode, otherwise ESP would be blank.

---

### Post by tea for one on 2022-06-29
I've just experimented with a Legacy installation of Ubuntu 22.04 on a UEFI capable PC.
Three partitions created automatically:-
```
test@test-NUC6CAYH:~$ sudo parted -l
[sudo] password for test: 
Model: ST980811 A (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  2097kB  1049kB                                     bios_grub
 2      2097kB  540MB   538MB   fat32        EFI System Partition  boot, esp
 3      540MB   80.0GB  79.5GB  ext4
```
 
The installer also put the efi files into the ESP

```
sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

```
I wonder if the installer, together with boot-repair, is suitably sophisticated to detect a UEFI PC even when a Legacy installation was performed.

Back to the OP:-
My legacy install did not boot immediately because the disk did not appear in the one-time boot menu.
I had to fiddle around to make the disk appear.
Power off 2/3 times and still missing but it eventually appeared and booted sluggishly.

@wmbarrow - Does your disk appear in the Toshiba boot menu?

---

### Post by wmbarrow on 2022-06-29
After reading other stuff on the Internet, I simply decided to use version 18.04.6 and upgrade it. Seemed like the easiest solution.
Thanks for attempting to assist.

---

