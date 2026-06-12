---
title: "Using an added drive to convert to RAID1 on a running sytem"
date: 2017-02-05
forum: Installation &amp; Upgrades
---

### Post by artist-wavenet on 2017-02-05
I need to setup RAID1 (mirror) on a running system. Currently Linux 16.04 is running on sda. A new hard drive that is identical to sda has been installed and is identified in the OS as sdb. My goal is to use sda and sdb together in a RAID1 configuration. To do this I followed the instructions at:
[https://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04](https://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04)

In these instructions I ran into trouble on this fdisk command:
[INDENT]
Hex code (type L to list codes): <-- fd
[/INDENT]

This command got me the error:


[INDENT]Type of partition 1 is unchanged: EFI System.
[/INDENT]
[INDENT][/INDENT]

It appears the instructions on this web page fail for me because I have an EFI file system. What do I need to do?

---

