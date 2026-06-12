---
title: "boot-repair failed after incomplete shim-signed package upgrade"
date: 2019-02-22
forum: Installation &amp; Upgrades
---

### Post by rollinrob on 2019-02-22
Hi!
Yesterday I upgraded the "shim-signed" package on my Ubuntu 16.04.5 server, which failed and left me with a broken system that won't boot again. So I booted an Ubuntu 16.04.5 live stick, installed [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") and started a "recommended repair", which unfortunately also left me with an error and the following message:
```
An error occurred during the repair.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!
```

I don't really know how to proceed now as I don't know how GRUB and the whole boot mechanism works. Could anyone please help me? I saved all the information boot-repair gave to me (Boot-Info and log) and can provide parts or all of it if that would help. I will attach the first section of the Boot-Info as this looks like it would tell people who know what they are doing a lot about the system ;)
The server has two HDDs and (temporarily) an USB stick attached.

Thanks in advance!

Rob



Boot-Info:
```

  Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img, but core.img can not be found at 
    this location.
 => No known boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /Boot/bootx64.efi 
                       /ubuntu/shimx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/mmx64.efi 
                       /EFI/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

sda3: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

sdc1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /dev/sdc1 is already mounted or /mnt/BootInfo/sdc1 busy

sdc2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sdc2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc2 starts at sector 9828. According to the info in 
                       the boot sector, sdc2 has 0 sectors.
    Mounting failed:   mount: /dev/sdc1 is already mounted or /mnt/BootInfo/sdc1 busy
mount: /dev/sdc2 is already mounted or /mnt/BootInfo/sdc2 busy

robserver-vg-root: _____________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.5 LTS
    Boot files:        /etc/fstab

robserver-vg-swap_1: ___________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

```

---

### Post by oldfred on 2019-02-22
Please use code tags if posting terminal output.
You can easily add code tags with forum's advanced Editor and # icon.

Better still, Post link to full Summary Report from Boot-Repair.

Is your system also encrypted? If so you need to decrypted it before running Boot-Repair.
You have LVM - logical volume type install. 

Are you booting in UEFI boot mode from UEFI, you show a very old grub BIOS boot in sdb which will not work.
If shim is installed, it should boot with UEFI Secure boot on or off, but if you updated UEFI, then you may have reverted to defaults in UEFI. Check your settings, you may want to turn off UEFI Secure Boot.

---

### Post by rollinrob on 2019-02-23
Thanks for the quick answer and editor hints!

My system is not encrypted, but Secure boot is enabled in UEFI and you are also right about the LVM install. I did not change anything in my UEFI, only upgraded the shim-signed package in Ubuntu.

Should I try switching off secure boot and run boot-repair again or can this make the problem worse?

---

### Post by oldfred on 2019-02-23
I would try with UEFI Secure Boot off.

---

### Post by ubfan1 on 2019-02-23
Your EFI partition looks damaged -- Everything should be under /EFI.  I see /Boot and /ubuntu there.  In /EFI/Boot, you should have a copy of grubx64.efi, along with the bootx64.efi

---

### Post by rollinrob on 2019-02-23
I disabled Secure Boot in UEFI and started boot-repair recommended repair again, but it did the same steps as before and exited with an error again.  The Boot-Info is available at [http://paste.ubuntu.com/p/vWhXWBgF5j/](http://paste.ubuntu.com/p/vWhXWBgF5j/)  How do I proceed now? Boot-repair tells me to "Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!", how do I do this?

---

### Post by oldfred on 2019-02-23
It says no error on grub install, it looks like error is related to sdc, which is your live installer. If you use dd or one of the the installers that uses dd, then your flash drive is not a normal partitioned drive, but a hybrid DVD/flash drive configuration. Then standard partition tools will not see it correctly.

If you press escape right after UEFI screen, do you get grub menu? If fast boot is on in UEFI, you may not have time to press escape. Fast boot assumes no changes to configuration and does not take time to scan system and write what hardware you have to drive for operating system, it just starts boot immediately.

---

### Post by rollinrob on 2019-02-24
You were right, the normal GRUB (version 2.02~beta2-36ubuntu3.20) showed up if I just started the machine without pressing any key. I selected the normal "Ubuntu" option. There was no screen output for about two hours, I guess a file system check was performed. Afterwards Ubuntu went into maintenance mode, because there were some file system errors which I fixed by running fsck manually. Then I rebooted and now Ubuntu is running again.

Thank you for your support!

As I now have Secure Boot disabled, is it save to keep it that way?

---

