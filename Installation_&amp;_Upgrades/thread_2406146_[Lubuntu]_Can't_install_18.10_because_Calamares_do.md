---
title: "[Lubuntu] Can't install 18.10 because Calamares does not detect my hard disk"
date: 2018-11-16
forum: Installation &amp; Upgrades
---

### Post by gaula92 on 2018-11-16
Hi there,

I have just tried to install Lubuntu 18.10 on a computer where previous Lubuntu versions (16.x, 17.x, even 18.04) install with zero problems.
However, the new installer (Calamares) fails at recognizing my hard disk. This is an UEFI system with Legacy (BIOS) support disabled, and the disk is partitioned using GPT.
So, all in all, nothing should prevent it from working.
In fact, I have installed Ubiquity on the Lubuntu 18.10 live USB, and it detects the hard disk as expected, can partition it, etc.
When I run Calamares, I see this warning:
```
13:56:13 [2]: WARNING: system is EFI but no EFI system partitions found. 
```

So, any advices are welcome. I really need to update Lubuntu on this machine, and these Calamares problems are a small hurdle I cant work around.
Please dont send me to 18.04, I already know its an LTS and all.

Thanks!

---

### Post by Dennis N on 2018-11-16
You need to create an EFI system partition on the disk - size about 100 mB, formatted FAT32, with boot flag set. Then try again.

---

### Post by gaula92 on 2018-11-16
> **Dennis N said:**
> You need to create an EFI system partition on the disk - size about 100 mB, formatted FAT32, with boot flag set. Then try again.

There's already an EFI system partition on my system. I clearly said 18.04 installs fine and runs in EFI mode.

```
lubuntu@lubuntu:~$ sudo fdisk /dev/sda

Welcome to fdisk (util-linux 2.32).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


Command (m for help): p
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A7324F66-CA73-4C6A-80F2-840531780A9E

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624 976771071 975720448 465.3G Linux filesystem


```

---

### Post by gaula92 on 2018-11-17
C'mon, no one can lend a hand here?

---

### Post by gaula92 on 2018-11-17
Hi there,

I'd like to get Lubuntu 18.10 installed on my system, but as you can see here, Calamares fails to detect my hard disk:
[https://ubuntuforums.org/showthread.php?t=2406146](https://ubuntuforums.org/showthread.php?t=2406146)

Since it doesn't seem to be anybody around who know what's going on and I REALLY need this done because I need this OS for daily work, I was wondering:
1- Is there a command-line installer like Debian has? (or had...) How is it called? Googled for it with no success.
2- Should the old Ubiquity installer still usable? It crashes when trying to create user (after file copying is complete).

Thanks!

---

### Post by wildmanne39 on 2018-11-17
Threads merged. Please do not post duplicates, it dilutes community effort.

If you do not receive a reply you may bump your thread once every twelve hours to keep it in few, it is the weekend and we are all volunteers with busy schedules, please be patient and try to be nice, I suspect you may be coming off a little rude.

---

### Post by 23dornot23d on 2018-11-17
I do not think many people will know what calamares is ........ but on searching for it ........... 

I came across this ..... [https://arcolinux.com/help-us-to-make-calamares-or-the-installer-better-and-help-yourself-and-others-in-the-process/](https://arcolinux.com/help-us-to-make-calamares-or-the-installer-better-and-help-yourself-and-others-in-the-process/)
( actually was looking for a calamares forum as that would be the place to ask the question )

[https://forums.linuxmint.com/viewtopic.php?t=277521](https://forums.linuxmint.com/viewtopic.php?t=277521)

Seems someone else had a similar problem ............ and it needed chroot into the system to update the grub .........

Hope this helps in some way ( is there a reason for using calamares )

---

### Post by Dennis N on 2018-11-17
From the display in post #3, it looks like you created partitions yourself using the "Manual Partitioning" option in Calamares? If you did, you need to specify where the EFI system partition is to be mounted. On the partitioning screen, select sda1, click the "Edit" button, and specify **/boot/efi **as the mount point. Than proceed with the rest of the installation and you should not get that error message.

---

### Post by gaula92 on 2018-11-18
@wildmanne39: Sorry if I sounded rude, really sorry. My english is not native and I wasn't aware it was sounding like that... It's not the first time it happens :eek:

@Dennis N: No, I did not partition the disk, Ubiquity did, simply told it to use entire disk as I always do, because Lubuntu is (was) my only OS. I can not indicate anything to Calamares because it's controls in the hard disk selection screen are totally unresponsive. I can not click anywhere.

@23doornot23d: That's not the same situation, as he doesn't get Calamares stuck on the hard disk selection screen, and he was trying to install on a MBR partitioned disk using UEFI, while mine is GPT using UEFI.

---

