---
title: "install grub on gpt"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by admilewis on 2011-02-21
Hi,
I have the following gpt table on /dev/sda (2 TB disk):

```
root@virgin:~# gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 3907029168 sectors, 1.8 TiB
Disk identifier (GUID): 08D6A8CF-8F86-4C69-ADD5-2F6595CC6309
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Total free space is 1755 sectors (877.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34         9765659   4.7 GiB     EF02  
   2         9765660        13671910   1.9 GiB     8200  
   3        13671911      3907027379   1.8 TiB     0700  
root@virgin:~# 

```and also parted output:

```
root@virgin:~# parted -l /dev/sda
Modello: ATA WDC WD20EADS-00R (scsi)
Disco /dev/sda: 2000GB
Dimensione del settore (logica/fisica): 512B/512B
Tabella delle partizioni: gpt

Numero  Inizio  Fine    Dimensione  File system     Nome  Flag
 1      17,4kB  5000MB  5000MB      ext4                  bios_grub
 2      5000MB  7000MB  2000MB      linux-swap(v1)
 3      7000MB  2000GB  1993GB      xfs

```but I cant install grub... also if i reboot it doesn't boot because the bios or efi cant find grub.. Now I booted from SystemRescueCD:

```
root@virgin:~# grub-install /dev/sda
Installation finished. No error reported.
root@virgin:~# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```but:

```

root@virgin:~# file -s /dev/sda
/dev/sda: x86 boot sector; partition 1: ID=0xee, starthead 0, startsector 1, 3907029167 sectors, extended partition table (last)\011, code offset 0x63
root@virgin:~# 

```so the problem is... how do I install grub on gpt ?

This is the result I've got since the last upgrade to the current LTS
thx very much for any hint..

---

### Post by srs5694 on 2011-02-21
> **admilewis said:**
> Hi,
I have the following gpt table on /dev/sda (2 TB disk):

```
root@virgin:~# gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 3907029168 sectors, 1.8 TiB
Disk identifier (GUID): 08D6A8CF-8F86-4C69-ADD5-2F6595CC6309
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Total free space is 1755 sectors (877.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34         9765659   4.7 GiB     EF02  
   2         9765660        13671910   1.9 GiB     8200  
   3        13671911      3907027379   1.8 TiB     0700  
root@virgin:~# 

```

First, your BIOS Boot Partition (/dev/sda1) is ridiculously large. It only needs to be about 32 KiB in size, although in most cases I'd recommend making it 1 MiB because of partition alignment issues (see next paragraph). Although 4.7 GiB is still pretty small compared to your disk's total size, you might want to reconsider the sizes if/when you re-install or want to make other changes to the system.

Second, your partitions are not properly aligned for use on an Advanced Format disk. This may not be an issue, depending on your disk type, but I thought I'd point it out, since Advanced Format disks are becoming more common. If you've got such a disk, you'll see very poor performance on writes of relatively small files with your partitions laid out as they are. Therefore, if there's any doubt in your mind about the type of disk you've got, I recommend you repartition immediately, aligning all your partitions on 8-sector boundaries. Most new partitioning tools align on 1 MiB boundaries by default, which satisfies this requirement. For more information on this issue, see [this article I wrote](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) for IBM developerWorks.

Third, if you're using /dev/sda3 as your Linux root (/) filesystem, I strongly recommend that you repartition: Create a new root (/) partition of ~20 GiB and devote the rest to /home (or perhaps /var or some other space if you're setting up a server that requires lots of space outside of /home). Although Ubuntu creates a simple configuration with a single filesystem by default, IMHO this is bad practice. Separating system and user data greatly simplifies certain types of upgrades and re-installations, since you can completely wipe the root (/) partition without losing your user data (in /home, or whatever you use for that purpose). This becomes especially important for really big installations like yours, since backing up and restoring as much data as you'll have on that disk will be very tedious. In fact, you might want to set aside a second ~20 GiB partition for future use. That will enable you to upgrade by installing to the second ~20 GiB partition without touching the original installation, thus enabling you to try a new version while retaining the ability to easily return to your original installation if the new one has problems.

> but I cant install grub... also if i reboot it doesn't boot because the bios or efi cant find grub.. Now I booted from SystemRescueCD:

```
root@virgin:~# grub-install /dev/sda
Installation finished. No error reported.
root@virgin:~# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

It's unclear what happened when you installed Linux on the disk. It *should* have installed GRUB just fine and then booted OK.

When you boot using an emergency disc, you've got to take extra steps to install GRUB to a hard disk, since the /boot directory and the files it contains belong to the rescue disc, not to the OS installation on the hard disk. I don't happen to have a reference handy for the exact steps you need to take. My own preference in this situation is to use [Super GRUB Disk](http://www.supergrubdisk.org) to boot into the installed system. You can then use grub-install to re-install GRUB to the hard disk. (Note you'll need to use the correct version of Super GRUB Disk according to whatever version you've got partially installed on your hard disk.)

You might also try running the [Boot Info Script](http://sourceforge.net/projects/bootinfoscript/) to see what part(s) and version(s) of GRUB are installed already.

One more point: You mentioned "the bios or efi cant find grub." The two have very different requirements about GRUB. If your computer supports both BIOS-style and EFI-style booting (as for instance some Intel boards do), BIOS booting will be easiest to get working from an Ubuntu perspective, since Ubuntu has poor EFI support (through version 10.10; the 11.04 alpha greatly improves matters, at least in the 64-bit version). Many Intel BIOSes, though, have a bug that requires that at least one MBR partition be marked as bootable, so you'll need to use fdisk (*not* gdisk, parted, or GParted) to mark the 0xEE partition as bootable/active. Note this is an Intel-specific bug; most other BIOSes boot from GPT disks just fine with no extra hoops to jump through. See [this page of mine](http://nessus.rodsbooks.com/gdisk/bios.html) for more on this subject.

If you want to use EFI booting, you'll need to install an EFI-enabled version of GRUB, including preparing a suitable .efi file for storage on an EFI System Partition, which you don't currently have. See [this page](http://grub.enbug.org/TestingOnMacbook) for one approach to doing this. You should be able to take some shortcuts by installing the grub-efi package in Ubuntu. This is still very much a "bleeding-edge" boot method for Ubuntu. IMHO, if you want to (or must) boot in this way, it's easier to install the Ubuntu 11.04 alpha 2 version, which (on a test I performed on an Intel motherboard) at least installed properly without a lot of extra hoop-jumping.

---

### Post by admilewis on 2011-02-22
Hi srs5694,

well..
1) the first partition of sda (/dev/sda1) is the system partition, the sda2 is the swap and sda3 is the data partiton.
2) I tryed supergrubdisk before my post but I'm not lucky ... I dont know why it can't boot.. with SRCD I have a system running without the native kernel.
3) I followed your advice so I marked bootable the partiton of sda by fdisk because, now I'm sure, I have bios and not efi. Anyway nothing is changed. It cant boot.
4) I have run boot_info_script.sh and the following is the result:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 34 of the 
    same hard drive for core.img, but core.img can not be found at this 
    location.
 => Grub 2 is installed in the MBR of /dev/sdb and looks at sector 34 of the 
    same hard drive for core.img, but core.img can not be found at this 
    location.

```

I attached the full RESULT,txt file to the message.

5) I cant repartition the disk because I have important data on it (hundreds of giga that I dont know where to put... the disks are 2 with 2TB each...)

6) your link to bios detail seems dont work:
```
$ host nessus.rodsbooks.com
Host nessus.rodsbooks.com not found: 3(NXDOMAIN)

```

7) thanks very very much for your help!

---

### Post by admilewis on 2011-02-22
Up

---

### Post by srs5694 on 2011-02-22
> **admilewis said:**
> Hi srs5694,

well..
1) the first partition of sda (/dev/sda1) is the system partition, the sda2 is the swap and sda3 is the data partiton.

Your gdisk and parted output clearly identifies the type codes. /dev/sda1 is a [BIOS Boot Partition.]("http://grub.enbug.org/BIOS_Boot_Partition") I'm not sure what you mean by "system partition" in this context; however, if you mean it's a Linux root (/) partition, it's not marked correctly in the partition table, and this could be at least part of the problem (see below).

> 2) I tryed supergrubdisk before my post but I'm not lucky ... I dont know why it can't boot.. with SRCD I have a system running without the native kernel.Note that Super GRUB Disk comes in several varieties, and you have to match the variety to your type of GRUB. In your case, you need Super GRUB 2 Disk; Super GRUB (Legacy) Disk won't work on your system.

> 4) I have run boot_info_script.sh and the following is the result:
...
I attached the full RESULT,txt file to the message.A key point from the RESULTS.txt file is this:

> ```
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

```This verifies that /dev/sda1 contains a filesystem, and seems to be your Linux root (/) partition. Thus, it should ***not*** be marked as a BIOS Boot Partition. You should *immediately* mark it correctly. You can do this with gdisk by using its "t" option to change the type code to 0700 and then use "w" to save the changes; or use a libparted-based tool (GNU Parted, GParted, or whatever) to remove the bios_grub flag from the partition. Leaving the partition with the incorrect partition type code could cause problems in the future, and it may already be part of your current problem.

Furthermore....

> ```
sdb1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  -
    Boot sector info:  
...
Partition           Start           End          Size System
/dev/sdb1              34 3,907,027,377 3,907,027,344 Bios Boot Partitio

```/dev/sdb1 is flagged as a BIOS Boot Partition and appears to contain no filesystem, but it also spans most of the disk. If you've got real data on this partition, it's possible that GRUB has wiped them out by installing part of itself there because of this incorrect type code marking. I recommend you try mounting the partition and, if you can, back up the disk immediately; then unmount and run fsck on the partition to fix its problems. If you can't mount it, I recommend you do a low-level dd backup of the /dev/sdb1 partition and then run fsck on it.

In any event, you'll have to use gdisk or a libparted-based tool to fix the partition's type code.

I recommend running fsck on /dev/sda1 from an emergency boot; it's conceivable that GRUB has tried to use the partition as a BIOS Boot Partition, which could have damaged the filesystem. My hunch is that /dev/sda1 is OK, though, and that /dev/sdb1 has suffered this fate and damage as a result.

With these changes made, I recommend you create a new partition (/dev/sda4) to serve as a BIOS Boot Partition. Make it roughly 1 MiB in size and give it a type code of EF02 (in gdisk) or flag it with the bios_grub flag (in parted or GParted). Don't put any filesystem on it. With this partition in place, re-installing GRUB to /dev/sda should make GRUB use the BIOS Boot Partition to store part of its boot code. If done properly, this may then restore the system to bootability. Either use Super GRUB Disk to boot your regular system or research how to install GRUB using your emergency disk; there are some extra hoops to jump through, but I don't recall the details offhand.

> 5) I cant repartition the disk because I have important data on it (hundreds of giga that I dont know where to put... the disks are 2 with 2TB each...)What types of disks are they? (Brand and model?) If they're Advanced Format disks, you *are* suffering poor performance because of the way the disks are partitioned. If they aren't Advanced Format disks, it's not a problem.

Also, you should always be able to back up your data, at least if the data are important to you. Hard disks can and do fail unexpectedly and suddenly, so if you lack a current backup, you're at risk of losing your data. Of course, if the data aren't that important (say, if it's a MythTV box with TV recordings), going without a backup might be reasonable; but if the data are important, you should get another disk, a tape backup unit, or some other means of backing up your data.

> 6) your link to bios detail seems dont work:
```
$ host nessus.rodsbooks.com
Host nessus.rodsbooks.com not found: 3(NXDOMAIN)

```

Oops; that URL should have been: [http://www.rodsbooks.com/gdisk/bios.html](http://www.rodsbooks.com/gdisk/bios.html). I accidentally posted the URL that's on my internal LAN rather than the world-accessible URL. I doubt if the page is relevant, given the new details you've posted, but it's conceivable it still is.

---

