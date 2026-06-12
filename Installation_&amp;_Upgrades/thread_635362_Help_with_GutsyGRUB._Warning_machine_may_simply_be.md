---
title: "Help with Gutsy/GRUB. Warning: machine may simply be cursed"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by Kanuck54 on 2007-12-08
First things first, the hardware:

Asus A8N SLI-Deluxe (Socket 939), onboard components disabled except SATA and IEEE-1394
AMD Athlon 64 3000+ (1.8 GHz, 90 nm)
2 x 512 MB OCZ PC-3200 DDR400 Premier
Antec SP-500 power supply (500 W)
PowerColor ATI Radeon X800 GT 256 MB on PCI Express, no PCI cards
4 x 200 GB Maxtor DiamondMax 10 SATA hard drives
Standard PS2 keyboard

I'm using Ubuntu 7.10 server edition, AMD64.

(Edit: my prior memory issues seem to be resolved, so forget that part.)

**My goal:** to have this box running as an Ubuntu server with uShare, serving media from a software RAID-5 array.

It took me quite some time to figure out the partitioning and work around some Ubuntu installer quirks and some personal knowledge gaps, but eventually I reached a stage where things look like this when I proceed with the Ubuntu install:

```

RAID0 device #0 - 13.6 GB Software RAID device
      #1  13.6 GB   F ext3       /
RAID5 device #1 - 600.0 GB Software RAID device
      #1 600.0 GB   f xfs        /var
RAID0 device #2 - 2.1 GB Software RAID device
      #1   2.1 GB   f swap       swap
SCSI1 (0,0,0) (sda) - 203.9 GB ATA Maxtor 6L200S0
      #1 primary    3.4 GB B K raid
      #2 primary  200.0 GB   K raid
      #3 primary  526.4 MB   K raid
SCSI2 (0,0,0) (sdb) - 203.9 GB ATA Maxtor 6L200S0
      #1 primary    3.4 GB B K raid
      #2 primary  200.0 GB   K raid
      #3 primary  526.4 MB   K raid
SCSI3 (0,0,0) (sdc) - 203.9 GB ATA Maxtor 6L200S0
      #1 primary    3.4 GB B K raid
      #2 primary  200.0 GB   K raid
      #3 primary  526.4 MB   K raid
SCSI4 (0,0,0) (sdd) - 203.9 GB ATA Maxtor 6L200S0
      #1 primary    3.4 GB B K raid
      #2 primary  200.0 GB   K raid
      #3 primary  526.4 MB   K raid

```First concern: if I'm manually zeroing the superblock on each partition used in the RAID array, and then manually reinitializing the partition table on each hard drive, and then restarting the machine to run the Ubuntu installer, why is it still detecting an existing filesystem on RAID device 0 (an ext3 filesystem) that needs to be overwritten? Is it just detecting the ext3 file table from the previous install attempt? I just want to ensure there isn't something beyond zeroing the superblocks and then blanking the partition tables I need to be doing.

Regardless, I press on. Installation goes fine until it reaches GRUB, at which point it dies. [FONT=monospace]Executing 'grub-install (hd0)' failed. This is a fatal error.[/FONT] Can't install LILO to /dev/md0, either. [FONT=monospace]Running "/sbin/lilo" failed with error code "1".[/FONT]

I can go to the shell, [FONT=monospace]cd /target[/FONT], [FONT=monospace]ls[/FONT] and see the file system; unfortunately there's no ability to configure grub from the server CD shell, so as per [this guide]("https://help.ubuntu.com/community/Installation/FileServerWithRAID#head-b7f1ec96d06eb6d2abc4f0696b8bcf4795371467"), I figure I'll just go ahead and download and burn a copy of the Gutsy Live CD, boot from that, and configure GRUB manually.

So after finishing the installation, I burn the Live CD on my MacBook, and reboot to it. I get the menu, and choose to boot Ubuntu; and my monitor shuts off and 2 of the 3 LEDs on my keyboard start flashing (I now understand this means a kernel panic).

So I reboot to the CD again, and choose to verify the CD; nope. Kernel panic. In fact, aside from MemTest86+, this isn't a Live CD, it's a kernel panic CD.

Still wondering if I just had a bad burn, I go ahead and burn the Live CD again, this time with disc verification. No dice; the Live CD is simply a no-go.

So I'm stuck. I apparently install successfully every time, but can't boot; I can't even boot the Live CD to try manually configuring GRUB; I have no idea what to do next. I am stuck good.

---

### Post by Kanuck54 on 2007-12-08
Okay, so my memory problems have vanished, but nothing else has improved. Still getting the Live CD kernel panic.

---

### Post by evolving_monkey on 2007-12-08
x

---

### Post by lha on 2007-12-09
> **Kanuck54 said:**
> 
Regardless, I press on. Installation goes fine until it reaches GRUB, at which point it dies. [FONT=monospace]Executing 'grub-install (hd0)' failed. This is a fatal error.[/FONT] Can't install LILO to /dev/md0, either. [FONT=monospace]Running "/sbin/lilo" failed with error code "1".[/FONT]

I can go to the shell, [FONT=monospace]cd /target[/FONT], [FONT=monospace]ls[/FONT] and see the file system; unfortunately there's no ability to configure grub from the server CD shell, so as per [this guide]("https://help.ubuntu.com/community/Installation/FileServerWithRAID#head-b7f1ec96d06eb6d2abc4f0696b8bcf4795371467"), I figure I'll just go ahead and download and burn a copy of the Gutsy Live CD, boot from that, and configure GRUB manually.

So after finishing the installation, I burn the Live CD on my MacBook, and reboot to it. I get the menu, and choose to boot Ubuntu; and my monitor shuts off and 2 of the 3 LEDs on my keyboard start flashing (I now understand this means a kernel panic).

So I reboot to the CD again, and choose to verify the CD; nope. Kernel panic. In fact, aside from MemTest86+, this isn't a Live CD, it's a kernel panic CD.

Still wondering if I just had a bad burn, I go ahead and burn the Live CD again, this time with disc verification. No dice; the Live CD is simply a no-go.

So I'm stuck. I apparently install successfully every time, but can't boot; I can't even boot the Live CD to try manually configuring GRUB; I have no idea what to do next. I am stuck good.

If memory serves, grub cannot boot from raid0 device. Use raid1 instead. If you really want to have / on raid0, you should create a /boot partition that is not on raid0.

Have you checked that the .iso you downloaded is good? (Do the m5sums match?)

---

### Post by Kanuck54 on 2007-12-09
Yep, the ISOs were indeed good; 7.10's Live CD is simply a no-go with my setup. I downloaded and burned a 6.06 Live CD, and it booted fine. (I'd bet the Radeon is the issue; looking around, it seems Gutsy's Live CD is causing all kinds of havoc for Radeon owners who were fine with older versions.)

I did realize the system wasn't likely to boot from RAID 0 (it would be lovely if they told you that anywhere!), so I figured out a way to switch my configuration to RAID 1 and even work in redundancy for the system itself—I was never too concerned about it, but if Ubuntu's going to *force* me to mirror my system files in order to take advantage of RAID, I may as well do it.

I changed the partition setup so my system was located on a RAID 1. This is the configuration now:


```

RAID1 device #0 - 2.0 GB Software RAID device
      #1   2.0 GB   F ext3       /
RAID1 device #1 - 2.0 GB Software RAID device
      #1   2.0 GB   F ext3       /var
RAID5 device #2 - 604.2 GB Software RAID device
      #1 604.2 GB   f xfs        /var/media
RAID0 device #3 - 2.1 GB Software RAID device
      #1   2.1 GB   f swap       swap
SCSI1 (0,0,0) (sda) - 203.9 GB ATA Maxtor 6L200S0
      #1 primary    2.0 GB B K raid
      #2 primary  201.4 GB   K raid
      #3 primary  526.4 MB   K raid
SCSI2 (0,0,0) (sdb) - 203.9 GB ATA Maxtor 6L200S0
      #1 primary    2.0 GB B K raid
      #2 primary  201.4 GB   K raid
      #3 primary  526.4 MB   K raid
SCSI3 (0,0,0) (sdc) - 203.9 GB ATA Maxtor 6L200S0
      #1 primary    2.0 GB   K raid
      #2 primary  201.4 GB   K raid
      #3 primary  526.4 MB   K raid
SCSI4 (0,0,0) (sdd) - 203.9 GB ATA Maxtor 6L200S0
      #1 primary    2.0 GB   K raid
      #2 primary  201.4 GB   K raid
      #3 primary  526.4 MB   K raid

```

Which partitions make up which arrays:

```

/dev/md0 => /dev/sda1, /dev/sdb1
/dev/md1 => /dev/sdc1, /dev/sdd1
/dev/md2 => /dev/sda2, /dev/sdb2, /dev/sdc2, /dev/sdd2
/dev/md3 => /dev/sda3, /dev/sdb3, /dev/sdc3, /dev/sdd3

```

Now the installer informed me GRUB installed successfully, and offered me a reboot. I obliged... still nothing.

It took quite a bit of fiddling around to realize /dev/sda, whose MBR contained the loading instructions, was in fact hard drive 4 in my BIOS. And my BIOS will apparently only try to boot the first hard drive it's got listed in its boot order. Knowing this, I manually select drive 3 or drive 4 and finally—finally!—managed to boot.

So I went ahead and reversed the order of the hard drives in my BIOS. I guess that means going to the extra effort of [installing GRUB into the MBR of both bootable hard drives](https://help.ubuntu.com/community/Installation/FileServerWithRAID#head-b7f1ec96d06eb6d2abc4f0696b8bcf4795371467) will be for naught though, since my BIOS will simply fail at boot if /dev/sda dies. Crappy.

I also encountered filesystem errors on /, so I had to boot to the 6.06 Live CD, mount and [font="monospace"]fsck[/font]. Luckily it worked fine.

So, I guess the lessons are:

[list]
[*]Radeon + Ubuntu 7.10 Live CD = no go. Use 6.06.
[*]The Ubuntu installer sucks at software RAID. You need to be aware that / and /boot must not be on RAID 0 or RAID 5 volumes. And between installation attempts, you need to boot into a shell; [font="monospace"]mount[/font] to check if any multidisk devices are already mounted and [font="monospace"]umount /dev/md0[/font] for each of them, or if there are none mounted, [font="monospace"]modprobe md[/font] to load the multidisk module; then follow these instructions for [removing a multidisk array with mdadm and zeroing the superblock of each one](http://ubuntuforums.org/showpost.php?p=2459683&postcount=2). And then you need to [font="monospace"]fdisk /dev/sda[/font] for each of your physical drives, blank the partition table with [font="monospace"]o[/font], and write the changes with [font="monospace"]w[/font]. And then restart the system.
[*]Some BIOSes will only boot from the first optical drive or first hard drive listed in the boot order, even if they allow you to list more.
[*]This computer is effing haunted, and should only be used by masochists.
[/list]

Here's hoping this is a helpful post for somebody out there. Anybody who's willing can feel free to write up any of these problems for the community docs, and contact me if you need more info.

---

