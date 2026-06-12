---
title: "Clone Ubuntu 10.04 server - GPT partition and Grub"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by zee on 2011-02-03
Hi.
  I have a bunch of computers with the same configuration, so I would like to install Ubuntu only to one master computer and later on just copy the partition layout and the filesystem unto other computers.

  Previously I was able to simply copy the partition layout (via the sfdisk utility), the filesystem (a simple "cp -a") and install Grub (via script).

  Now I had to use the parted utility to partition the 2TB drive and Grub2 is the default boot loader.

  My questions are now:
1. How do I copy the partition layout from /dev/sda (master) to /dev/sdb (clone)?
2. How do I batch install install Grub2 to the other disk (e.g. /dev/sdb) ?
In Grub 0.97 it used to be something like that:
```
# GRUB the disk
grub --no-floppy --batch <<EOF_GRUB
root ($GRUB,0)
setup ($GRUB)
quit
EOF_GRUB
```

In Grub 2 I tried with:
```
grub-install --force --root-directory=/mnt/sdb1/ /dev/sdb
```

Only to get this error:
```
+ grub-install --force --root-directory=/mnt/sdb1/ /dev/sdb
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
Installation finished. No error reported.
```

Yet the partition layout is similar on the master computer and clone disk:
```
root@c1:~# parted /dev/sda p
Model: ATA WDC WD2003FYYS-0 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  1940GB  1940GB  ext4            root  boot
 2      1940GB  2000GB  60.4GB  linux-swap(v1)  swap
```

```
root@c1:~# parted /dev/sdb p
Model: ATA WDC WD2003FYYS-0 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  1940GB  1940GB  ext4            root  boot
 2      1940GB  2000GB  60.4GB  linux-swap(v1)  swap
```

Could anyone point me in the right direction? The Grub2 syntax is way different compared to Grub0.97.

Yes, I do could use the Grub2-suggested option but since the partition layouts on both partitions are equal, I see little point in setting the BIOS Boot Partition option, since the master computer works without it and I don't remember any error message during the install.

Thanks in advance,
zee

---

### Post by Skaperen on 2011-02-03
If the 2TB drives are the same size on the staging machine as on the target machines, you can accomplish the transfer by raw copy that includes the first 34 sectors and last 33 sectors of the drive, plus all partitions that need to be replicated (others, like swap space and empty filesystems can just be initialized on the target).  If the sizes are different (but your intent is to copy the system parts that occupy the same size portion at the start), you'll have to partition dynamically on each target.  And GPT makes this somewhat harder since you can't just do this by sector copying.

1.  Copy sectors with dd.  If the sdb copy target will become the sda drive on the target machine, don't worry that it is sdb for now.

2. I can't advise on GRUB2 since the GRUB developers are taking this former bootloader into a new realm I don't want to deal with (I'm one of those people that want a bootloader to do one job ... can you guess what that is).

If you copy the whole disk, sector by sector, it should be bootable if the target is at the same device location as the source when it is booted.  But you might have issues if the source is also the running system that is doing the copying, because copying a mounted working filesystem sector by sector is not reliable.

You should have a "staging system" which is the system you build up and configure in the way you want the target machines to run.  This can be done in some cases inside a virtual machine (assign the whole /dev/sdb to that virtual machine so it is /dev/sda there).  Or you can dedicate a real machine to this purpose, which helps ensure the right drivers are there if the targets are the same hardware.

On the dedicated machine, boot some other system, like a Live Ubuntu CD, to do the replication work.  Plug in a target machine's drive as a 2nd drive, boot the Live CD, run dd to copy the (not mounted) staging disk to the target disk.

Doing things more dynamically, such as having a script to partition the disk, format filesystems, load files (like from cpio), and customize for each target instances (for example, configure static IP addresses, hostnames, etc), is harder.  BTDT in Slackware with MBR.  I'm still learning Debian and Ubuntu details to do the same.  I've found parted to be nightmare tool for partitioning.  The gdisk or sgdisk tools are better, but I'm still planning my own ultimate partition+bootloader tool project (e.g. it can put a simple bootloader in place as part of doing the partitioning).

---

### Post by psusi on 2011-02-03
You need to create a bios boot partition to install grub to a GPT disk.  Rather than copy the partition table, just write the commands to create them to a file and pipe it to parted to execute.

---

### Post by oldfred on 2011-02-03
Just to add to psusi's comments:

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.  Thus, you must make a separate "BIOS boot partition" to hold core.img.  Make it 128 kiB as recommended in the following link.  Actually, using ext2 for example, and GParted Live CD, the minimum partition size is 8 MB, or 32 MB for FAT32.
sudo parted /dev/sda set <partition_number> bios_grub on
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
"unknown" filesystem! may be shown

Grub will install but it uses block lists which are not considered reliable without the BIOS boot partition.

Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
Multiboot install with gpt & using gdisk
[http://ubuntuforums.org/showthread.php?t=1566090](http://ubuntuforums.org/showthread.php?t=1566090)

[http://www.rodsbooks.com/gdisk/bios.html](http://www.rodsbooks.com/gdisk/bios.html)

You need to have gdisk:
GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by psusi on 2011-02-03
You don't need to use gdisk - parted will happily do it.  Just set the bios_grub flag on the partition ( 1mb is plenty ).

---

### Post by Skaperen on 2011-02-03
> **psusi said:**
> You don't need to use gdisk - parted will happily do it.  Just set the bios_grub flag on the partition ( 1mb is plenty ).
I have managed to get parted to do GPT configurations.  But I find gdisk to be much easier.  Even so, neither reach the level of ease that I think should be doable.

Note that my concept of "easy" may be someone else's concept of "horribly impossible" ;) ... and visa versa.  Mine would involve being able to specify, either in a command line or in a config control file, things like boundary alignment constraints, layout order, and partition sizes in either common units like bytes, sectors, blocks, and pages (and k,M,G,T multiples thereof) or in the alignment unit.  And it shall me possible to have the partition which is last in the layout be specified to "run to the last alignment unit before the backup table".

---

### Post by zee on 2011-02-03
@Skaperen:
I hate the idea (and the implications) of having an application with 1000 functions, of which only a few work "as advertised". I also don't see any good reason why Ubuntu chose Grub2 for its mainstream releases. I mean...even more bleeding-edge releases don't use Grub2.

Since the machines are equal in terms of hardware using "dd" might just be thing I need.

Regarding the cloning script: I already have one that does just that (hostname, IP change, ...) I used in the past, that I already adapted to the new situation. It is just this two pesky, little things that bother me now.

@all:
I did manage to partition the new drive using commands like the ones below:
```
parted -s $DISK mklabel gpt
parted -s $DISK mkpart primary ext4 1049KB 1940GB -a optimal
parted -s $DISK mkpart primary linux-swap 1940GB 2000GB -a optimal
```

The main problem is that the Ubuntu 10.04 server installer does not make use of the Grub Bios partition as evidenced by the output of the command "parted /dev/sda/ print" on the master machine:
```
Model: ATA WDC WD2003FYYS-0 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  1940GB  1940GB  ext4            root  boot
 2      1940GB  2000GB  60.4GB  linux-swap(v1)  swap
```

There's no extra partition, unless it is kept hidden.

The question is then how the Ubuntu installer manages to install Grub in the first place.

To make a long story short:
If I make this Bios Boot Partition, the only command needed to install Grub2 to the /dev/sdb is this one:
```
grub-install --force --root-directory=/mnt/sdb1/ /dev/sdb
``` ?

Thanks again.
zee

---

### Post by psusi on 2011-02-03
> **Skaperen said:**
> 
Mine would involve being able to specify, either in a command line or in a config control file, things like boundary alignment constraints, layout order, and partition sizes in either common units like bytes, sectors, blocks, and pages (and k,M,G,T multiples thereof) or in the alignment unit.  And it shall me possible to have the partition which is last in the layout be specified to "run to the last alignment unit before the backup table".

You can do all of that with parted.

> **zee said:**
> @Skaperen:
I also don't see any good reason why Ubuntu chose Grub2 for its mainstream releases. I mean...even more bleeding-edge releases don't use Grub2.

Because grub legacy is irreparably broken in several ways, so its authors decided several years ago to dump it and rewrite it from scratch and get things right.  Continuing to use a version that is no longer maintained and has several significant known (and unfixable) bugs is silly.

> **zee said:**
> The main problem is that the Ubuntu 10.04 server installer does not make use of the Grub Bios partition as evidenced by the output of the command "parted /dev/sda/ print" on the master machine:

Probably should file a bug on that.  It should at least warn you that you should create one.

> **zee said:**
> The question is then how the Ubuntu installer manages to install Grub in the first place.

The same way you did; by falling back to the unreliable blocklist method.  That was a warning, not an error.

> **zee said:**
> To make a long story short:
If I make this Bios Boot Partition, the only command needed to install Grub2 to the /dev/sdb is this one:
```
grub-install --force --root-directory=/mnt/sdb1/ /dev/sdb
``` ?


Yes, and you won't even need the --force.

---

### Post by zee on 2011-02-03
Thank you for all the explanations and clarifications.

zee

---

### Post by Skaperen on 2011-02-03
> **psusi said:**
> You can do all of that with parted.It wasn't apparent from the man page.  And a number of combinations of things just didn't work.  It looks like an attempt, much like the COBOL language, to be "English like".

> **psusi said:**
> Because grub legacy is irreparably broken in several ways, so its authors decided several years ago to dump it and rewrite it from scratch and get things right.  Continuing to use a version that is no longer maintained and has several significant known (and unfixable) bugs is silly.
Yes, grub legacy has its breakage.  But what I use of it works.  And I could not figure out how to use grub2 to do these things.  Part of that is because I was NOT putting grub ON to the host disk, but rather, TRYING to put grub IN to a constructed image.  The grub installer program had no concept of what I was doing, for either grub1 or grub2.  But grub1's files were at least usable.  I could copy stage1, maybe stage1.5, and then stage2, along with other things I was doing, to construct my image file as I wanted it.  That resulting device image could be recorded to the media and booted and it came up just fine (not as pretty since it had text instead of graphics, but it worked).  Oh, I did have to make a patch to the grub source code to force a specific sector number for the next stage, since all attempts to make a config file do it never succeeded.  But grub2 was simply nowhere near usable for that project.  It was then I started thinking "I need a simple KISS-principle boot loader that does its one thing well".  If I need to make it do a variation on the one thing, I don't mind ... for a bootloader ... to have a script patch the assmbly source code and rebuild a new image.  A hard coded assembly constant is, IMHO, a simpler concept to deal with than having to squeeze in extra code to find and parse a config file.

My end result:  [http://slashusr.net/ubuntu/10.10/ubuntu-10.10-desktop-amd64.iso.img](http://slashusr.net/ubuntu/10.10/ubuntu-10.10-desktop-amd64.iso.img)

Just dd that to the whole device name of a sacrificial USB memory stick and it will be bootable and does what the Ubuntu ISO does.  But this is no unetbootin product.  That same image file is still a usable ISO which can be burned to a CD (if big enough) or DVD, and is still bootable and still does the same thing.  One image file, two media types.

If you want other variations of that image, change ubuntu to kubuntu or xubuntu, desktop to netbook where applicable, amd64 to i386, and 10.10 to 10.4.1 or 10.4 or 9.10, as desired in that URL.

---

### Post by psusi on 2011-02-03
> **Skaperen said:**
> 
Just dd that to the whole device name of a sacrificial USB memory stick and it will be bootable and does what the Ubuntu ISO does.  But this is no unetbootin product.  That same image file is still a usable ISO which can be burned to a CD (if big enough) or DVD, and is still bootable and still does the same thing.  One image file, two media types.

Hrm... interesting idea.  The iso9660 fs leaves the first 2kb unused right?  So you can still cram an MBR in there.  This might be a useful feature to add to grub2.

---

### Post by srs5694 on 2011-02-03
I agree with much of the advice posted here so far. I do have a few additional thoughts, though.

First, I do *not* recommend a byte-for-byte copy (using dd or similar tools) of either GPT or filesystem data for this application. The reason is that GPT uses Globally Unique IDs (GUIDs; the "G" in "GPT"), and Linux filesystems use the similar Universally Unique IDs (UUIDs). Both have the same purpose, as suggested by their names: to uniquely identify specific disks, partitions, or filesystems. Doing a byte-for-byte copy defeats this purpose; the cloned disk will have the same GUIDs and UUIDs as the original. This is probably acceptable, and even desirable, for a backup disk, but not when cloning a disk for a new computer. What happens if you need to pull the disk from one computer and use another computer to repair it? Potentially dangerous confusion over which partition gets mounted, that's what. To clone a GPT disk using a script, use sgdisk or parted to copy the partition table, use mkfs to create a new filesystem, and then copy the filesystem data using tar or some similar file-level utility. Alternatively, do a low-level clone and then use sgdisk to change the GPT's GUID values and tune2fs (or similar tools for other filesystems) to change the filesystems' UUID values.

My second comment is that 2 TB disks are still small enough to use MBR. If you're running into significant problems with GPT, using MBR is still fine. It's not like you can add to the disk space like you could add to a computer's RAM (unless you've got a 2 TB RAID array), so you're unlikely to run into problems with MBR's limitations on these installations. Of course, if you're trying GPT now because you know you'll need it on bigger disks in 6 or 12 months, then getting the bugs worked out now makes perfect sense. I just want to point out that 2 TB (2 x 10^12 bytes) is less than the 2 TiB (2 x 2^40 bytes) limit of MBR with disks that use 512-byte sectors, so you won't be losing disk space or anything with MBR.

Third, if you don't like GRUB Legacy (patched for GPT) or GRUB 2, you could look into [Syslinux.](http://syslinux.zytor.com/wiki/index.php/The_Syslinux_Project) I haven't investigated it in detail, but I understand that there is a version available that can boot Linux from GPT disks on BIOS-based systems.

Fourth, for the future, there's evidence that the long-discussed shift from BIOS to UEFI may be underway; some motherboard manufacturers have released several UEFI-based motherboards in quantity (although most of these seem to have been temporarily withdrawn, victims of the [Sandy Bridge SATA bug](http://techreport.com/discussions.x/20326)). Unfortunately, most Linux distributions seem to have very poor EFI/UEFI boot support at the moment. I was trying out the Ubuntu 11.04 alpha recently, and although it'll boot the installer in UEFI mode, doing so is like pulling teeth. Fedora 14's better in this respect, but still painful. (I've got a working Fedora 14 UEFI installation in VirtualBox.) For the short term, it's best to stick with a conventional BIOS. I only mention this as a heads-up to avoid such boards for the next few months, and to investigate the matter again before buying a motherboard or computer in 6 or 12 months. Also, if and when it becomes desirable or necessary to use UEFI, some of the partitioning and boot loader issues will be different from what they are now. For instance, there's no need for a BIOS Boot Partition on such a computer, but you do need an EFI System Partition.

---

### Post by psusi on 2011-02-03
Odd.  I got one of those boards recently and had no trouble booting natty in efi mode.

---

### Post by srs5694 on 2011-02-03
It may vary by implementation; or perhaps we had slightly different alpha versions. It didn't quite work for me using a 64-bit image downloaded Feb. 1 in VirtualBox with its EFI implementation, on a PC using a UEFI DUET setup, or (using the 32-bit image) on a Mac Mini 1,1. In the first two of those cases, I got a "grub>" menu when I tried to boot. I was able to get it to go further in UEFI DUET by manually setting the prefix and root environment variables, loading the "normal" module, and running that module. The installer then started and ran, but it had problems installing a package (console-setup or some such, IIRC; the same package gave problems when I tried to install in BIOS mode, so clearly that's not an EFI-specific bug.) I could get past the boot loader the same way in VirtualBox, but then it ran into video problems; I think it booted to the installer, but the video display was dark. The i386 version didn't even include the necessary EFI boot files.

It's good that you got it to work. With any luck these were alpha-test problems that have been corrected already.

---

