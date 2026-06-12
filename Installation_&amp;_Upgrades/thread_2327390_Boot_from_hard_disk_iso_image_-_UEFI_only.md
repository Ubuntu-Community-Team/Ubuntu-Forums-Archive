---
title: "Boot from hard disk iso image - UEFI only"
date: 2016-06-10
forum: Installation &amp; Upgrades
---

### Post by getut2 on 2016-06-10
I have some ECS Liva X2 mini PC's that have 32GB eMMC disks in them that I am trying to set up as hardened remote desktop machines. As part of the hardening, I plan to run the system from a static ISO located on the hard drive. There are plenty of tutorials out there to get an Ubuntu iso booting from grub2 on a machine.

The Liva X2 is presenting me with some problems though.

Problem 1: I can only get Ubuntu 16.04 to see the eMMC drive if I boot the system in UEFI mode. If I boot it in legacy mode, the Ubuntu live USB can't see the eMMC disk.

Problem 2: I'm having trouble getting grub to see the iso images.All the searches I do for this show setting up grub to find ISO's on traditional hard drives on machines with BIOS. I've seen some indication that it might work with UUID's and see a grub line that starts with the command "search" to get it to use UUID instead of partition numbering (I can find no docs on how grub would number an eMMC partition). But even if I DID get this working with UUID, I would prefer to use partition numbering because I am going to be imaging this setup over 100 times. I don't want to have to change all the UUID's. I'd rather just use plain partition numbers. But regardless, I haven't even gotten this to work with UUID's.

Basically I have the system configured like this:

/dev/mmcblk0p1 = /boot/efi
/dev/mmcblk0p2 = /
/dev/mmcblk0p3 = <extra partition I mount as needed>
/dev/mmcblk0p4 = swap

I have 3 bootable installs (if everything was working right) on the machine. 
1) I have a real, native install that was installed from USB disk in the traditional way that is using partitions 1, 2 and 4 in the normal way. I plan to password protect this boot entry in grub and remove its default boot state. I may also just purposely bork this install and remove it completely after I get grub booting to the 2 ISO's below.
2) I have an ISO image dropped in the root of partition 2
3) I have an ISO image dropped in the root of partition 3

Please help me get this booting.

---

### Post by oldfred on 2016-06-10
My entries in grub for my UEFI system are no different than entries in my older BIOS based system.
Issues are drive & path. I often have drive issues if not same drive as boot drive as using device and adding a flash drive or not can change drive order.
And boot drive is always hd0, and with UEFI boot drive is always sda and then hd0.

```
menuentry " " {
set root= 
}

menuentry 'Live ISOs on SSD' {
configfile (hd0,3)/ISO/livecdimage.cfg
} 

menuentry 'Live ISOs on HDD' {
configfile (hd1,3)/ISO_b/livecdimage.cfg} 

menuentry " " {
set root= 
}

```

I have entries before & after so I had space lines, I also use configfile entry to a script in the ISO partition/folder. I always would forget to run sudo update-grub when changing ISO. But with configfile I can just edit script when updating ISO. I have two ISO folders, one on sda & one on sdb, so I can install to each (other) drive. But found issues and had to change boot parameters to include toram

```
# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs' {
# configfile (hd1,3)/iso/livecdimage.cfg
#} 
# Add iso names to livecdimage.cfg
#for i in `ls *.iso`;do echo "# "$i>>livecdimage.cfg; done;

menuentry "Ubuntu 16.10 yakkety Daily amd64" {
    set isofile="/ISO/yakkety-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd0,3)$isofile 
    linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile toram
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 16.04 xenial amd64" {
    set isofile="/ISO/ubuntu-16.04-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd0,3)$isofile 
    linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile toram
    initrd (loop)/casper/initrd.lz
}


```

My /ISO folder is in partition 3 on sda. That usually works, but my sdb may be hd1 or hd2 and I often have to try each when booting.

       This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

---

