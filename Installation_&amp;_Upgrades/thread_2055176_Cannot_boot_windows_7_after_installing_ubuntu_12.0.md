---
title: "Cannot boot windows 7 after installing ubuntu 12.04"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by Mortuis0 on 2012-09-08
Hi,

I've just bought a G75 ASUS laptop with a preinstalled win7 in it. I then tried to installed ubuntu 12.04 64 bits and it crashed at first. Nothing would boot on my computer by then. I then downloaded a new image, finished the installation of ubuntu (and GRUB) and ubuntu booted perfectly. In the grub menu, when I try to boot on windows 7, I have the message "Invalid EFI file path",  same when I try to boot on the windows recovery partition.

I have 2 physical HDD in my laptop. Here is the output of "sudo fdisk -l" :

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x527cd163

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   500118191   250059095+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xbbc58b91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   732547071   366272512    7  HPFS/NTFS/exFAT
/dev/sdb2       732549118  1465147391   366299137    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sdb5      1457338368  1465147391     3904512   82  Linux swap / Solaris
/dev/sdb6   *   732549120  1457338367   362394624   83  Linux

Partition table entries are not in disk order
```

On /dev/sda (a 256 Gb SSD drive) there is 5 partitions in reality. In order (saw using gparted) :

[LIST=1]
[*]200 Mb fat 32 partition, where I suppose win7 has it's EFI running (flagged as bios_grub)
[*]unkown partition of 128 Mb, really dark this one, I don't know what it's for (flagged as mfstres)
[*]70 Gb OS partition
[*]143 Gb partition to install big applications
[*]a 25 Gb recovery partition (flagged as hidden,diag)
[/LIST]
On /dev/sdb, sdb6 is flagged "boot" and this is where my ubuntu is installed.


I tried boot-repair with several different options (even tried to uninstall grub-efi and install grub-pc ; but boot-repair reversed this), tried to disable UEFI in the BIOS, tried to force boot on sda or sdb, tried all I found in multiple forums ; All without success. I still get the same error message when trying to boot in windows.



I don't have any win7 boot disk, only the recovery partition which I cannot access. I am feeling I don't need to do much to make it work, but I can't understand how to correctly connect the GRUB end to the win7 end...


Can someone help me ? What's with that EFI thing ?

---

### Post by darkod on 2012-09-08
fdisk says it detected GPT table on /dev/sdb but it also says it has extended partition, which can't be true for GPT. If the disk has gpt table earlier and you switched it to msdos using windows tools, it doesn't delete the backup gpt table from the disk so linux will be able to detect it and get confused.

If this is the case, you can remove the backup gpt leftovers with fixparts. It will detect it and offer to remove it, just open the disk with it.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

This still won't solve everything, but it's one step forward.

EFI or UEFI is the new boot system and there are still issues when dual booting with it. Hopefully it didn't delete your windows boot files but that can happen too.

First sort out the backup gpt table on sdb and then we'll see.

---

### Post by Mortuis0 on 2012-09-08
I followed the procedure for the /dev/sdb partition you gave me. As you said, ```
fixparts /dev/sdb
``` offered me to remove the GPT remainings, I answered yes. Here is the new output of "sudo fdisk -l" :

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x527cd163

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   500118191   250059095+  ee  GPT

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xbbc58b91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   732547071   366272512    7  HPFS/NTFS/exFAT
/dev/sdb2       732549118  1465147391   366299137    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sdb5      1457338368  1465147391     3904512   82  Linux swap / Solaris
/dev/sdb6   *   732549120  1457338367   362394624   83  Linux

Partition table entries are not in disk order

```I then reran boot-repair and followed the instructions to the letter, choosing to install GRUB on sda (only). I noticed the installation of grub-pc during the process. Here is the ticket : [http://paste.ubuntu.com/1193897/](http://paste.ubuntu.com/1193897/)

Ubuntu now boots with the message "the disk driver for boot/efi/ is not ready or not present" and I have the option to "skip the mounting" by pressing 's', which is what I do and get in Ubuntu without problem. I noticed that in the boot menu in the BIOS, there is a "volume absent" label for the "windows loader" and "ubuntu" boot choices.

However, trying to boot choosing either "windows 7" or "windows recovery" leads to a windows boot manager screen telling me to run a recovery procedure from a win7 disk to "repair the installation". I cannot go beyond that screen.

I guess it's one step forward as you said :) What would be the next ?

---

### Post by darkod on 2012-09-09
Do you have any win7 rescue cd to repair the install?

I don't have all the answers since I don't use UEFI, and also you have two separate disks one with gpt and the other with msdos tables.

From what I have seen so far, the main thing when installing on UEFI systems is to boot the ubuntu cd in UEFI mode, not in the standard mode. In BIOS there will be two different devices referring to the cd-rom. You need to fire it off in uefi mode so that it tries to install grub-efi instead of grub-pc.

Unfortunately the previous install mighe have messed up the windows efi boot process. Without a win7 dvd or a win7 rescue cd it might be impossible to fix. If you do manage to get hold of it, I guess it's best to disconnect the ubuntu disk temporarily and try the repair.

---

### Post by Mortuis0 on 2012-09-09
I finally reformated my sda drive installing a new windows 7 on it (can't use an utlimate edition repair a home edition...like if the boot was that different ; or this is thievery to enable EFI support only in one edition and not in the others, anyways). At first, I couldn't choose to install on the existing partition dedicated to the OS, I had to entirely destroy the filesystem in order to reinstall it (a pop-up indicating I couldn't install with GPT partition tables). During the process, the setup recreated a 100 Mb partition at the beggining of the drive, which I already saw in a different installation where I could dual boot with ubuntu without problem.

Now I have a running win7 on my sda and after installing all basic stuff (anti-virus, office, etc.), I'll do an image of it, plug the sdb drive back in and try to restore the dual boot. With an luck, this will (finally) work.

This leads me to my next question : do you recommend any specific configuration for what I am about to do ? And by the way, is it usual to install linux and it's swap on an extended partition ?

---

### Post by darkod on 2012-09-09
It seems that you have UEFI boot disabled in the BIOS. If it is, leave it that way since it's easier to dual boot in the standard bios boot.

One of the ways to check this is to boot the ubuntu cd in live mode, and run in terminal:
```
sudo parted -l
```

That will show the partition table type, msdos or gpt. If it's msdos that means you are not using uefi boot since win7 needs gpt table to work with uefi.

You need to know in what mode to reinstall ubuntu if you are reinstalling.

As for configurations, depends on how you use your computer. I always like having separate /home partition but you need to use the manual partitioning install to create that. In that case you would create like 20-25GB root partition (mount point / ), a swap partition and the rest for /home partition.
Linux has no problems working with logical partitions (which are inside the extended one). How many primary or logical you create depends on the layout and how many partition you want because the maximum with msdos table is 4 primary partitions, or 3 primary + 1 extended holding the logical ones.

---

### Post by Mortuis0 on 2012-09-09
Ok, all is now up and running with the initial configuration I wanted. I bypassed EFI usage but learnt a lot about it, thanks to you Darko. See you !

---

### Post by YannBuntu on 2012-09-11
Good job :)

You had several problems in your previous configuration ([http://paste.ubuntu.com/1193897/](http://paste.ubuntu.com/1193897/)).

Please could you indicate your current [Boot-Info]("https://help.ubuntu.com/community/Boot-Info") URL, so that we can compare?

---

### Post by Mortuis0 on 2012-09-17
I'm sorry, I think I didn't took note of the link boot repair told me the last time I ran it. I would be glad to share, do you know where I can find it afterward ?

---

### Post by oldfred on 2012-09-17
You have a link to the BootInfo report in post #3. And if you want your current configuration you can rerun it at anytime.

It saves copies, but they may be in temporary locations that are not saved after a reboot. 

I see it saves version here:
/var/log/boot-sav with different dates & versions

---

### Post by YannBuntu on 2012-09-18
> **Mortuis0 said:**
> I'm sorry, I think I didn't took note of the link boot repair told me the last time I ran it. I would be glad to share, do you know where I can find it afterward ?

Please just run Boot-Repair, click "Create BootInfo summary", and tell us the new URL that will appear.

---

