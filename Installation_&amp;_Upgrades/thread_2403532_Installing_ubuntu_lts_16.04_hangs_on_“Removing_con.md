---
title: "Installing ubuntu lts 16.04 hangs on “Removing conflicting operating system files”"
date: 2018-10-12
forum: Installation &amp; Upgrades
---

### Post by novavis on 2018-10-12
I know this error message has already been discussed in the past, but I believe my hanging is caused by something else, because I don't have a separate /home partition.

I am trying to install ubuntu 16 lts on an external usb hard drive of 1 terabyte, using a usb stick on which I burnt the iso, which boots fine. I've been trying partitioning it so:

[LIST]
[*]/dev/sdc1 a swap (8G)
[*]/dev/sdc2 a boot partition (ext2, 500M)
[*]/dev/sdc3 the main partition with the remaining space (ext4)
[/LIST]
I use an hp notebook, 8G ram, intel core i5.
The drive is usually /dev/sdc, and I mark it as the device for boot loader installation. The installer on default wants to use /dev/sda5 (the efi partition on the hard drive of my notebook, which I don't want to be touched) so I always select it, click "change" and "Do not use this partition".
At first I get a message about the fact that I haven't marked for formatting /dev/sdc2, the /boot partition so I could lose some files (Obviously not a problem since it's empty) But I also get:

[LIST]
[*][INDENT][I][FONT=inherit]If you continue, the changes listed below will be written to the disks. Otherwise, you will be able to make further changes manually.[/FONT]
[FONT=inherit]The following partitions are going to be formatted: partition #3 of SCSI5 (0,0,0) (sdc) as swap

[/FONT][/I]
[/INDENT]

[*][INDENT][I][FONT=inherit]The attempt to mount a file system with type vfat in SCSI1 (0,0,0), partition #5 (sda) at /boot/efi failed.[/FONT]
[FONT=inherit]You may resume partitioning from the partitioning menu.

[/FONT][/I]
[/INDENT]
[/LIST]
These messages appear gradually, in the meantime I can continue entering the timezone, user and password. Then, on the last window, it hangs on "Removing conflicting operating system files".
I've searched online for this problem and all the results I've found seemed to be caused by the /home partition, which I don't have.
I also don't get why it tried to mount /dev/sda5.
Anyway, do you have any ideas about how to fix this issue? Would it be useful if I posted /var/log/syslog, /var/log/partman or other logs?

---

