---
title: "Installing via GRUB"
date: 2018-05-08
forum: Installation &amp; Upgrades
---

### Post by fparri on 2018-05-08
Hello,

I would like to update my Linux Mint box to the new 18.04 Ubuntu LTS. My PC has problems with USB and CD-ROM booting, so I succesfully tried booting the Ubuntu ISO stored on my / partition, via GRUB.

My question is: would it be possibile to store the ISO on a Windows 10 NTFS partition and have GRUB boot it, so that I can then proceed installing it on my Linux partitions?

I hope I was clear enough.

Fingers crossed,
F

---

### Post by yancek on 2018-05-08
> would it be possibile to store the ISO on a Windows 10 NTFS partition  and have GRUB boot it, so that I can then proceed installing it on my  Linux partitions?

Yes.  You may have problems if you are installing to the same physical hard drive.  If you see a message telling you that there are partitions mounted and asking to unmount them from the drive you are installing from you will have problems.  You won't be able to unmount all the partitions on that drive as you will be using one to boot from.   I just did this but it was installing Ubuntu 18.04 to an external drive booted from a partition on an internal drive.  I first tried to boot from and install to the same hard drive and got that message and my minimal efforts to get around it failed.  I know I was able to do this in the past so I'm not sure what changed.  If you try this, make notes of what happens if you get errrors and post, someone might be able to help.

---

### Post by oldfred on 2018-05-08
[URL="https://help.ubuntu.com/community/Grub2/ISOBoot"]https://help.ubuntu.com/community/Grub2/ISOBoot
[/URL]
 Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive) 

I find getting drive,partition & path correct major issues. When I plug in a flash drive, my drive as seen by UEFI/BIOS/grub changes from hd0 to hd1. As this is before Ubuntu has mounted system, paths also are different. It is default on drive, not as mounted once booted.

I find I have to use the toram and unmount the isodevice.


 # Required as /isodevice usually mounts to a partition and installer does not correctly unmount
sudo umount -lrf /isodevice
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1155216](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1155216)
Says to use toram boot parameter 

A while back they added .efi to the vmlinuz, but with 18.04 they have removed it again. So check examples.
/vmlinuz.efi is now

I have a separate partition with ISO, sda5, but not always hd0. 
```
menuentry "Ubuntu 18.04 Bionic amd64" {
    set isofile="/ubuntu-18.04-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd0,5)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile toram
    initrd (loop)/casper/initrd.lz
}


```

I have created a FAT32 UEFI bootable flash drive with just grub and put ISO into that one partition.

---

### Post by rsteinmetz70112 on 2018-05-08
Why not use the standard network upgrade?

---

### Post by fparri on 2018-05-09
Thank you, I was able to boot Ubuntu Mate ISO from my Windows 10 partition, yesterday. Since the partition I am booting the ISO from and the one I will be installing to share the same Hard Disk, I will be probably need OldFred tips. I will let you know once I proceed clean-installing (I need to backup some files before that).

---

### Post by fparri on 2018-05-09
That's absolutely my case. Thanks for the tips! I will let you know as soon as I try installing 18.04 :)

---

### Post by oldfred on 2018-05-09
The issue with one drive and only booting it, becomes, if you do not have a bootable system, the only way to fix it is to boot a repair disk or possibly move drive to another similar working system.

---

### Post by fparri on 2018-05-09
I see. You mean if something goes wrong, right?

---

### Post by yancek on 2018-05-09
When booting an iso to install, I generally see a message indicating that partitions on different drives are mounted also saying that I may not be able to create, delete or resize a partition and asking if I want the installer to try to unmount the partitions.  My experience with this is that selecting No generally works and the install proceeds.  Not sure where you are planning to install Ubuntu but, if your intention is to install over Mint which you are booting from and the install has problems and fails you will not be able to boot the installer again.  Simpler to create another Linux formatted partition to install to then later use the current Mint partition as a data partition.

---

### Post by fparri on 2018-05-09
I see. Thanks for the tip. Actually, I would use GRUB to boot the Ubuntu ISO from my windows 10 partition, so the Linux Mint Partition shouldn't be mounted. That said, it's probably better not to risk. Thanks a lot :)

---

### Post by yancek on 2018-05-09
> Thanks for the tip. Actually, I would use GRUB to boot the Ubuntu ISO  from my windows 10 partition, so the Linux Mint Partition shouldn't be  mounted. That said, it's probably better not to risk. Thanks a lot :smile:

The point is to NOT install to the partition on which the current Mint exists as that will overwrite all of the files needed to boot and if your Ubuntu install fails, you won't have any simple way to boot.  Create another partition to install Ubuntu to and when that works, format the Mint partition to use for data.

---

