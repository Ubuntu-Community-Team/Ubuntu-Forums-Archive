---
title: "dual boot no longer working correctly"
date: 2023-09-25
forum: Installation &amp; Upgrades
---

### Post by mikelev on 2023-09-25
I'm new to posting here, please forgive me if this is not the correct place.

I had an Ubuntu / Windows dual boot system that was working well until I tried to set up SSD external drive to boot and run Ubuntu. I made sure to add the BOOT info to the /dev/sdg of the SSD drive so as not to upset the current boot loader, but it seems to have upset it anyway.
I can no longer boot up and run Ubuntu unless the SSD is connected. If I disconnect it and try to run Ubuntu, it stops on the #grub prompt.  However, if I boot up and do nothing, Windows will load.

I've tried disconnecting the external SSD after booting up on my original Ubuntu on the PC, and then running grub-install, but that hasn't fixed the problem.

How can I restore the original grub state so as to have it work normally as a dual-boot when the external SSD is disconnected?

I have two NVMe drives installed and Ubuntu and the EFI that I use are on nvmen1p1 drive.

Here's the relevant contents of the pastebin:

Thank you so much if you're able to help me with this.

```
nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

nvme0n1p2: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 23.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

nvme0n1p3: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

nvme0n1p4: _____________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

nvme1n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi

nvme1n1p2: _____________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

nvme1n1p3: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8 or 10
    Boot files:        /Windows/System32/winload.exe

nvme1n1p4: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

nvme1n1p5: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:
```

---

### Post by tea for one on 2023-09-25
> **mikelev said:**
> I have two NVMe drives installed and Ubuntu and the EFI that I use are on nvmen1p1 drive.
I think that you mean nvme0n1p1.

Anyway, try this:-
Attach your external disk and boot into the Ubuntu installation on your internal disk (nvme0n1)
Safely remove your external disk
Open a terminal and enter
```
sudo grub-install /dev/nvme0n1
```
If it reports success, then
```
sudo update-grub
```
Close terminal
Reboot without external disk

Any joy?

---

### Post by mikelev on 2023-09-25
Thanks for the suggestion:
I tried installing on /dev/nvme0n1 as you suggested, but received an error message: "error: cannot find EFI directory".

So then I tried again on each of /dev/nvme1n1 and /dev/nvme0n1p2 but received the same error message again.

---

### Post by oldfred on 2023-09-25
What is efi entry in fstab. That is the default location to reinstall grub into on major updates.
I found changing it, I had to reboot as even the normal mount -s did not fully reset mount of ESP.

Post these:
lsblk -f
cat /etc/fstab

If using external drive, I prefer to have ESP with boot files.
But Ubuntu's Ubiquity installer with 22.04 and before and still in flavors only installs to ESP on "first" drive. First drive is defined by UEFI/BIOS as it is before boot & mount of partitions.
Very of Ubiquity bug:
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

---

### Post by MAFoElffen on 2023-09-25
If usig the Ubuntu 22.04 Desktop Installer (ubiquity), a way to avoid that in the future if you are installing a second version of Linux that uses Grub2, use try, open a terminal and startup the installer via
```

sudo ubiquity -b

```
The Calamares installer has a drop down option in the partitoner that says "no bootloader". Not sure if the other installer have equivalent options.
  
But as oldfred noted, and what I notice, is that the UEFI BIOS on your computer is not finding the EFI partition on the other drive. Noted when you unplugged the USB drive, it still didn't find it. That indicates to me, that you need to go into your BIOS and change where that is looking for that first drive, to boot from. That setting in BIOS seems to be set wrong. At least, that is what I would check first.

---

### Post by mikelev on 2023-09-30
Thanks very much for your help, Tea for One :)   I've been travelling so couldn't reply earlier.
I tried your suggestions but  it still gave an error. So I played around a bit more, deleting the grub and reinstalling -- and after about the 2nd or 3rd time, it worked!
So now it's back to normal, and I can boot up on the external SSD as well.  I appreciate the suggestions.

---

