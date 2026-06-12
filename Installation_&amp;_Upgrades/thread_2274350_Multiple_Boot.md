---
title: "Multiple Boot"
date: 2015-04-19
forum: Installation &amp; Upgrades
---

### Post by ian85 on 2015-04-19
What is a program so i can boot multiple operating systems on one flash drive. I've already tried YUMI multiboot, XBooot, and another multiboot and they don't work.
thanks

---

### Post by yancek on 2015-04-19
I seriously doubt that you will find anything.  Some of the software you mentioned does work on some distributions.  There are too many differences in various Linux distributions and changes are constantly being made with new releases.  It's not possible for a "one size fits all" to work without a tremendous amount of work.  Obviously, no one who has the knowledge and skills to do this is interested or it would be available.

You can do it manually but the methods will vary depending upon which Linux you want.  With Ubuntu and it's derivatives, you can simply install Grub to the MBR of a flash drive with all the boot files on either a boot or / partition, copy the iso file of all the Ubuntus you want to the flash drive and create a grub.cfg file with appropriate entries.  Many non-Ubuntu Linux systems cannot be booted as iso files but can be booted as Live CDs if extracted.

If you are willing and or interested I can give you further information.  I used a 16GB flash drive with this method to install over 20 Linux Utilities/operating systems.  If you want something that will work with a few mouse clicks, good luck.  Reasons this won' work explained in the first paragraph.

---

### Post by ian85 on 2015-04-19
that would be great i am looking to boot probably less than ten for now but i will add more when i find more I like. I have a 16gb flash drive.

---

### Post by oldfred on 2015-04-20
Before most of the multi-boot scripts were created, I just used grub2 to boot ISO. But ISO has to be configured for grub2's loop mount.

Is system UEFI or BIOS? Configuration of flash drive and install of grub is different. I now use gpt partitioning whether UEFI or BIOS and have both efi & bios_grub partitions.

       This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

This user created a system that boots with both UEFI & BIOS using grub, but updates get out of sync and cause issues.
       Bootable UEFI USB Key
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[http://ubuntuforums.org/showthread.php?t=2015019](http://ubuntuforums.org/showthread.php?t=2015019)

---

### Post by yancek on 2015-04-20
The links posted by oldfred give some good detailed information.  Probably the simplest thing to do is to format the flash as FAT32 although you can also use a Linux (ext2,3,4) filesystem.  Run sudo fdisk -l if you are unsure of the device name for the flash (sdb, sdc,etc) and then mount the partition at a mount point you create and install Grub to the partition and mbr:  

sudo grub-install --root-directory=/media/iso /dev/sdb 

In the above example, you would need a directory name iso created under /media and the flash would be sdb, change as appropriate.  You would need to create a grub.cfg file in the /boot/grub directory on the flash drive.  Below is a very simple sample entry to boot the Bodhi Linux iso.  This entry should work as should the different entries shown in the links posted above for Ubuntu and derivatives.  The second entry is for LXLE which does not boot the iso but has the iso file loop mounted on your primary Linux system and then copied to the partition on the flash drive.  Many Linux distros will not boot directly from an iso file so loop mounting them and then copying them to the flash with a proper boot entry should work.


> # Sample GRUB configuration file
insmod biosdisk
insmod pc
insmod gpt
insmod part_msdos

# Boot automatically after 30 secs.
set timeout=30

# By default, boot the first entry.
set default=0

# Fallback to the second entry.
set fallback=1
set gfxpayload=1024x768x16, 1024x768

  set menu_color_normal=red/black
  set menu_color_highlight=magenta/black

menuentry "bodhi-2.4.0" {
    loopback loop /bodhi-2.4.0-32.iso
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/bodhi-2.4.0-32.iso quiet splash --
    initrd (loop)/casper/initrd.gz
}

menuentry "LXLE" {
    linux /casper/vmlinuz boot=casper  quiet splash --
    initrd /casper/initrd.gz
}

---

### Post by ian85 on 2015-04-21
Yumi created a multiboot pendrive linux program has anybody heard if that works or knows anything about that?

---

### Post by oldfred on 2015-04-21
Is your system UEFI or CSM? Or an older BIOS only system?
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

I have many scripts in my notes that others have suggested, Yumi is one of them. Never used it myself. I prefer using grub2.  Or those scripts that use grub2 as then you can use the grub2 instructions to manually update or change ISO you boot.

---

