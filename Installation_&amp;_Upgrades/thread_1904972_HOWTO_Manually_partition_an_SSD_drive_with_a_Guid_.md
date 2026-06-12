---
title: "HOWTO: Manually partition an SSD drive with a Guid Partition Table (GPT)"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by danellisuk on 2012-01-05
This is a simple guide for installing a new SSD drive using a Guid Partition Table.  I thought I would share my result after doing this for the first time today.  Useful information on the subject was obtained from the Arch Linux wiki.

I choose not to put a swap partition on my new SSD drive.  I can either go without (as my machine has plenty of RAM), or I can manually put the swap partition on a traditional rotary disk (if I want my system to be able to hibernate).

To keep things simple, unplug any additional drives leaving just the SSD attached and boot from either a USB stick or live CD.  You don't want to accidentally wipe any other drives.  Your SSD should then be */dev/sda*.

First install gdisk which is like fdisk but for managing GPT disk layouts.

 **sudo apt-get install gdisk**

Run gdisk and specify the drive to manage.

 **sudo gdisk /dev/sda**

The following is a transcript of the operation to create three partitions (with the elements you need to type in bold).  The first partition is a special "Bios boot partition", which is required by grub to install itself in, (note the special code *ef02*).  The second is a small boot partition for the kernel.  The third is the root partition which will use the remaining space.

[FONT="Courier New"]Command (? for help): **o *<enter>***
This option deletes all partitions and creates a new protective MBR.
Proceed? (Y/N): **y *<enter>***

Command (? for help): **n *<enter>***
Partition number (1-128, default 1): ***<enter>***
First sector (34-30093806, default = 34) or {+-}size{KMGTP}: ***<enter>***
Information: Moved requested sector from 34 to 2048 in
order to align on 2048-sector boundaries.
Use 'l' on the experts' menu to adjust alignment
Last sector (2048-30093806, default = 30093806) or {+-}size{KMGTP}: **+1M *<enter>***
Current type is 'Linux/Windows data'
Hex code or GUID (L to show codes, Enter = 0700): **ef02 *<enter>***
Changed type of partition to 'BIOS boot partition'

Command (? for help): **n *<enter>***
Partition number (2-128, default 2): ***<enter>***
First sector (34-30093806, default = 4096) or {+-}size{KMGTP}: ***<enter>***
Last sector (4096-30093806, default = 30093806) or {+-}size{KMGTP}: **+500M *<enter>***
Current type is 'Linux/Windows data'
Hex code or GUID (L to show codes, Enter = 0700): ***<enter>***
Changed type of partition to 'Linux/Windows data'

Command (? for help): **n *<enter>***
Partition number (3-128, default 3): ***<enter>***
First sector (34-30093806, default = 1028096) or {+-}size{KMGTP}: ***<enter>***
Last sector (1028096-30093806, default = 30093806) or {+-}size{KMGTP}: ***<enter>***
Current type is 'Linux/Windows data'
Hex code or GUID (L to show codes, Enter = 0700): ***<enter>***
Changed type of partition to 'Linux/Windows data'

Command (? for help): **w *<enter>***

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING PARTITIONS!!

Do you want to proceed, possibly destroying your data? (Y/N): **y *<enter>***[/FONT]

Finally when installing Ubuntu select custom partitioning and map the following:

sda2 to be used as /boot
sda3 to be used as /

The grub boot loader can be installed to /dev/sda.

Notice how sda1 is not mapped to anything here.  However, it will be used by grub.  Without the special "Bios boot partition", grub installation will fail.

---

