---
title: "SATA and USB disks switch addresses after install?"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by pjfarley3 on 2007-03-11
I used the "alternate install" i386 CD to install ubuntu 6.10 on a USB external drive.  During install, the USB drive (WD 120G) is seen as /dev/sda.  I manually partitioned (with gparted prior to ubuntu install) the drive so that the 3 primaries are /boot, swap, and / (57M, 2G, 20G).  There is also a large extended with 12 logical partitions, not relevant here.

During install partitioning step, I manually specify /dev/sda1 as /boot and /dev/sda4 as root.  /dev/sda3 is the swap partition, and /dev/sda2 is the extended partition.  The physical order of the partitions on the drive is sda1, sda3, sda4, sda2.

After (seemingly) successful install is done, reboot gets grub menu, and the boot of the "regular" kernel hangs forever.  A reboot to the recovery-mode kernel reveals that the USB and internal SATA drives have been changed, as follows:

During install:

External USB is /dev/sda
internal SATA is /dev/sdb

After reboot:

External USB is /dev/sdd
Internal SATA is /dev/sdc

I used recovery mode (sed) to modify /boot/grub/device.map to change sda to sdd, and /etc/fstab the same change plus change sdb to sdc.  However, reboot still hangs, with only the message "Starting up:" in the Alt-F1 screen (no other text in any of the other Alt-Fx screens).

HW config is Dell 8400, 3.2Ghz P4, 1G RAM, 160G SATA internal, AHA-2930CU SCSI adapter (Jaz-2G and ZIP-250), external USB HDD (WD 120G).

TIA for any info/url/RTFM you can provide.

Peter

P.S. -- Recovery mode boots to (initramfs) with message "/dev/sda1 does not exist!", but at that point I am able to mount /dev/sdd1 as /boot and /dev/sdd4 as /.  That's how I was able to update grub/device.map and fstab.

---

### Post by dcstar on 2007-03-11
> **pjfarley3 said:**
> 
.......
TIA for any info/url/RTFM you can provide.

Peter

P.S. -- Recovery mode boots to (initramfs) with message "/dev/sda1 does not exist!", but at that point I am able to mount /dev/sdd1 as /boot and /dev/sdd4 as /.  That's how I was able to update grub/device.map and fstab.

I think you need to use the Grub command line to determine which drives Grub sees as Drive 0 and Drive 1, and then perhaps alter the menu.lst file to reflect the correct designations for the correct drive.

You should do a forum/web search for the specific commands on how to get this info out of Grub.

---

### Post by pjfarley3 on 2007-03-12
OK, I will see what device grub thinks is hd0 when I get home tonight.  However, I have already tried changing grub's "device.map" file to tell it to use /dev/sdd as (hd0), and also changed /etc/fstab to match, and that did not appear to help.

I'll post what I find later.  Thanks for the advice.

Peter

---

### Post by pjfarley3 on 2007-03-12
> **pjfarley3 said:**
> OK, I will see what device grub thinks is hd0 when I get home tonight.  However, I have already tried changing grub's "device.map" file to tell it to use /dev/sdd as (hd0), and also changed /etc/fstab to match, and that did not appear to help.

I'll post what I find later.  Thanks for the advice.

Peter

No joy, I can't seem to get grub to execute, neither from ubuntu recovery mode nor from rescue mode on the alternate CD.  I come closest using rescue mode from the alternate cd, grub starts probing for disks but then gets "error loading terminal type bterm" or something similar to that.  I tried changing the TERM variable to vt100, but then every line overwrote the other near the top of the screen (I'm guessing that grub is trying to do curses screen handling or something and the minimal shell doesn't support it).

I'm going to get the LiveCD and see if that gives me more capability to debug the problem.  I've seen other posts where the info from "fdisk -l" was requested, so I will see if I can get that info too.

Thanks for trying to help, I'll be back when I have more info.

Peter

---

### Post by pjfarley3 on 2007-03-15
Well, I finally have a working ubuntu 6.10 system running.  The problem is well documented, it just took me a long time to find the right thread.

This page has a load of good info and links, it helped me finally get going:

[http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")

The problrm, to boil it down, is that the install and grub see the disks in a different order than when you boot from your grub root to the "real" system.  And different distribution's install or rescue disks see them differently, too.

Here is what I cound about how my machine's disks are seen:
[FONT="Courier New"]
Device.......ubuntu.....grub.......FC6..........ubuntu
Type.........610 CD.....on boot....RescueCD......booted
---------....------.....-------....--------......------    
SATA 160G....sdb........hd1........sdc...........sda
Jaz 2G.......sdc........hd2........sda...........sdb
ZIP-250......sdd........hd3........sdb...........sdc
USB 120G.....sda........hd0........sdd...........sdd
[/FONT]

My Dell 8400 has SATA on the MB (up to 4 drives) but only 1 SATA drive is installed.  Then I have an Adaptec 2930CU PCI card with attached Jaz and ZIP drives at LUN 4 and 5 respectively.  Then I have an external USB 2.0 WD IDE drive.

BIOS boot order was not changed during this process, it was always:

CDROM
USB
SATA

ubuntu is installed on the USB drive, partition 1 for /boot, 3 for swap and 4 for root.  Partition 2 is extended, with a bunch of logical FAT32 and FAT drives archived from earlier machines.

THe two optical drives were seen as /dev/hda and /dev/hdb everywhere, as far as I could tell.

HOW I GOT IT TO WORK:

After installing from the Alternate CD to the USB drive, I booted the FC6 RescueCD, which then allows me to manually mount the ubuntu root (/dev/sdd4 to FC6) and /boot (/dev/sdd1 to FC6).  Then I use sed to change /boot/grub/device.map to change sda to sdd:

mount /dev/sdd4 /mnt/sysimage
mount /dev/sdd1 /mnt/sysimage/boot
cd /mnt/sysimage/boot/grub
sed 's/sda/sdd/g' < device.map > device.map.sdd
mv device.map device.map.sda
cp -a device.map.sdd device.map

The grub menu.lst already has (hd0) everywhere it is needed, but the comments all say "/dev/sda" instead of "/dev/sdd", so do the same trick for menu.lst:

sed 's/sda/sdd/g' < menu.lst > menu.lst.sdd
mv menu.lst menu.lst.sda
cp -a menu.lst.sdd menu.lst

Now /etc/fstab has to be changed, but there were too many changes to make just with sed, so I used nano to make the changes.  The ubuntu installer has set up /etc/fstab so reflect the disks as the installer saw them, but they have to be arranged the way the booted ubuntu will see them instead.  All of these changes needed to be made in my fstab:

sda ==> sdd
sdb ==> sda
sdc ==> sdb
sdd ==> sdc

ubuntu 6.10 still won't mount the SATA drive (neither the vfat partition that Dell puts there for recovery nor the ntfs WinXP partition), but I'll deal with that later.

I tried using the rescue mode on the ubuntu alternate CD and also tried modifying these files from the ubuntu LiveCD, but the alternate CD rescue couldn't mount the ubuntu partitions and the LiveCD couldn't write to them -- "permission denied".  So I had to use the FC6 RescueCD, which got me a running system.

YMMV, and I hope this helps someone else.

Regards,

Peter

---

