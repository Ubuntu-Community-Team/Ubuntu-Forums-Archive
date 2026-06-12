---
title: "Installation of Ubuntu on second hard drive doesn't boot"
date: 2013-05-31
forum: Installation &amp; Upgrades
---

### Post by Overv on 2013-05-31
I have an existing 3 TB hard drive that I use for Windows files (non-OS related). I shrunk it with Disk Manager in Windows 7 to leave 128 GB of free space.

Then I booted the Ubuntu 13.04 live cd from my USB drive and selected the manual partitioning installation option. I selected the hard drive (which is apparently seen as my primary drive) and created partitions in the remaining free space as follows:

[http://imgur.com/a/mCO5P](http://imgur.com/a/mCO5P)

*(I don't know what's up with the sizes, it seems to subtract 1 MB from the size I specify)*

I then selected /dev/sda to install the bootloader in and started the installation process. It seemed to be successful and asked me at the end if I wanted to restart.

I restarted the PC and selected this hard drive from the BIOS boot menu, but it stops at "Loading Operating System". What am I doing wrong?

**Edit:** Also, here's some output from commands I tried:

```
> fdisk -l /dev/sda
Cannot open /dev/sda

> sudo grub-install --recheck --no-floppy --root-directory=/ /dev/sda
Path `/boot/grub` is not readable by GRUB on boot. Installation is impossible. Aborting.
```

**Edit 2:** I just ran boot repair and it asked me if sda is a removeable disk. I selected No, because it's an internal hard drive. Then it said that /boot was detected.

I clicked recommended repair and it gave me this:

"GPT detected. Please create a BIOS-boot partition (>1MB, unformatted filesystem, bios_grub_flag). This can be performed via tools such as Gparted. Then try again."

**Full boot info:** [http://paste.ubuntu.com/5720036/](http://paste.ubuntu.com/5720036/)

---

### Post by Overv on 2013-05-31
I decided to just delete all existing partitions. I think the problem was that it couldn't create the 1 MB boot partition.

---

### Post by fantab on 2013-06-01
HDD larger than 2TB needs and uses GUID Partition Table [GPT]. Your 3TB HDD, /dev/sda has GPT.
While your /dev/sdb is 'legacy' MBR.

Ubuntu/Linux can boot from GPT Disks in "legacy" BIOS Mode only if it has 1-2MB Partition as your first partition.

You should be able to install and run Ubuntu in 'legacy' BIOS mode just fine from GPT once you have 1 MB bios_grub. 

I think your computer is booting from /dev/sdb by default. You will have to change the BIOS boot order of your HDD to boot /dev/sda first.

---

