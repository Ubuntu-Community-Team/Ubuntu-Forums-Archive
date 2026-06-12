---
title: "Lack of space in new 16.04 partition. How to add space?"
date: 2017-04-17
forum: Installation &amp; Upgrades
---

### Post by bthomson100 on 2017-04-17
I've installed Ubuntu 16.04.2 "over" Ubuntu 14, but the partition it went onto (sda7) doesn't have much space - only about 13 GB, with now only 3.7 GB free. The previous partition where Ubuntu 14 was installed (sda5) has 231 GB and 62 GB free.

How can I either reinstall 16 onto sda5 or transfer the empty space on sda5 to sda7?

I had a terrible time installing Ubuntu 16 and am reluctant to waste another week solving this problem.

Bob Thomson
Ottawa, Canada

---

### Post by oldfred on 2017-04-17
Did you use an auto install option or Something Else?
Do you just have the standard install of / (root) and swap? Or a separate /home or other partitions?

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by bthomson100 on 2017-04-17
> **oldfred said:**
> 

 Did you use an auto install option or Something Else

I created a boot USB key with a downloaded ISO file. ubuntu-mate-16.04.2-desktop-i386.iso
I booted from that and installed it following the instructions, trying to retain the dual Windows 7 / Ubuntu boot option at the beginning. There were a lot of things I didn't understand and one was about deleting all the files on sda5 which I didn't want to do even though I had backed up a lot of the important stuff.

> Do you just have the standard install of / (root) and swap? Or a separate /home or other partitions?

This is what I have::

```
bobt@bobt-AOD270:~$ sudo -s fdisk -l
[sudo] password for bobt: 
Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x0f767e94

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            2048  27265023  27262976    13G 27 Hidden NTFS WinRE
/dev/sda2  *     27265024  27469823    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda3        27469824 124823984  97354161  46.4G  7 HPFS/NTFS/exFAT
/dev/sda4       124825598 625141759 500316162 238.6G  5 Extended
/dev/sda5       124825600 583381320 458555721 218.7G 83 Linux
/dev/sda6       623071232 625141759   2070528  1011M 82 Linux swap / Solaris
/dev/sda7       583383040 620992511  37609472    18G 83 Linux
/dev/sda8       620994560 623065087   2070528  1011M 82 Linux swap / Solaris
```

The old home and bobt folders are still on sda5 and there are new ones on sda7, the new Ubuntu 16 partition.

I don't know what you mean about 
"the standard install of / (root) and swap? Or a separate /home or other partitions?"
Obviously I'm very much a newbie to command level fiddling with operating systems.

> May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[>https://help.ubuntu.com/community/Boot-Info]("https://help.ubuntu.com/community/Boot-Info") and:
[>https://sourceforge.net/p/boot-repair/home/Home/]("https://sourceforge.net/p/boot-repair/home/Home/")

I've downloaded the Sourceforge iso file <boot-repair-disk-32bit.iso> but feel intimidated by the sample screen shots there as I have no idea what boot, GRUB, MBR and all those other names, parameters, etc. do and fear I'll lose access to my computer again for another week, as I just did in uploading Ubuntu 16.

Bob

---

### Post by oldfred on 2017-04-17
The  Boot-Repair ISO is getting old.
Much easier just to use your Ubuntu live installer and add the ppa. Second set of instructions.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Are you running 32 bit Ubuntu for a reason?
Unless you system is over 10 years old or has less than 2GB of RAM, you probably should be using the 64 bit version.

It looks like you just used one of the auto install options that just creates new partitions.
Whenever you want to reuse existing partitions, you should use Something Else install option.
Then you choose (change button) which partition you want to use/reuse. It will normally reformat & erase all old data, so if you have something you want to save you must have that backed up. But then you have those backups anyway?

 Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

