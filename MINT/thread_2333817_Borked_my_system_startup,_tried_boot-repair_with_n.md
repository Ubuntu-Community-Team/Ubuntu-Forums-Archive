---
title: "Borked my system startup, tried boot-repair with no luck, need help"
date: 2016-08-13
forum: MINT
---

### Post by ggeorg3 on 2016-08-13
Hi all,

Hoping you can help with this.

I messed up my system after trying to install freebsd (to replace a windows 7 partition) as secondary OS to dual boot along with ubuntu 16.04.1 (my daily use OS)

I read that boot-repair might repair the damage but it didn't. It did create a log file [http://paste2.org/0ZKVyndN](http://paste2.org/0ZKVyndN) but I'm unsure what to do next.

Can someone walk me through what I need to do to repair or undo this mess?

Thank you,
George

---

### Post by ajgreeny on 2016-08-13
Thread moved to BSD which is possibly more appropriate for your problem.

It looks as if you have managed to wipe everything from your 1TB disk as far as I can see as it does not have a valid partition table shown in that output from boot-info script.
```
=================== parted -l:

Model: ATA TOSHIBA DT01ACA1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags:
```
That is the only hard disk shown so I presume it is the only one in the machine.

Unfortunately I do not know freebsd nor its installer so I have no idea what has gone wrong here.  If you have backups of your personal files you can, of course, reinstall whatever OS you want

---

### Post by bishka2 on 2016-08-13
[COLOR=#000000]So I nuked Windows and went with Mint, live cd etc but everytime I get this

*The 'grub-efi-amd64-signed' package failed to install into /target/.  Without the GRUB boot loader, the installed system will not boot*.[/COLOR]

HAve tried all. legacy, uefi etc

killing me!

[http://paste2.org/vGUCdUMU](http://paste2.org/vGUCdUMU)

---

### Post by ajgreeny on 2016-08-14
*Thread now moved from **BSD** to **MINT**.* which is more appropriate for the problem.

It looks as if you chose to use LVM partitioning but I know absolutely nothing about how to manage them so I regret that I will have to leave this to others.

---

