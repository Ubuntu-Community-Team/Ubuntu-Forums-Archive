---
title: "New PC, large drive partitioning scheme advice"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by ratcheer on 2011-06-02
I am supposed to get a new PC in the next few days. It has a 1 TB disk drive. I have never had anything like that (my current PC is 6 & 1/2 years old and has an 80 GB disk) and it is a bit bewildering trying to decide how to partition it. I have been doing research on the question this morning and, of course, I find all kinds of differing advice.

Here is my initial plan:


[LIST]
[*]First, a 30 GB primary partition for Ubuntu /
[*]Second, a 70 GB primary partition for other possible OS's that require installation in a primary partition, such as BSD.
[*]Third, a 2 GB primary partition for swap space (the new PC has 8 GB RAM).
[*]Fourth, a large extended partition for Ubuntu /home and the installation of other Linux systems as I decide to play with them, including Ubuntu pre-release testing systems. Should this be the rest of the disk or just a couple of hundred GB?
[/LIST]
Is this a sensible scheme? Are there very good reasons for doing something differently?

Thanks,
Tim

---

### Post by dozycat on 2011-06-02
Maybe is overkill but you can get for swap 8gb in case you want to go sleep, you have enough space with the new hard disk.

---

### Post by ratcheer on 2011-06-02
Thanks. I have even considered leaving 7 GB of unallocated space after the swap partition, just in case I decide I need to make it larger, later.

Tim

---

### Post by oldfred on 2011-06-02
You do not have to partition entire drive right away. Just be sure that extended partition is at end of space you do partition so you can extend it into the unallocated or include remaining space in extended, but not create logicals. 

My newer 650GB drive from 2 or 3 years ago is still not full allocated. I keep adding 20 or 25GB partitions to install some system to and then do not reuse that partition. I only have a couple of larger partitions for data, but do not save lots of large files like movies.

I will only use gpt not MBR/msdos for new drives. But gpt does not work with all systems unless booting with UEFI and UEFI is just starting to work for some grub2/Linux systems. Not sure about BSD, but I understand it does not play well with other systems.

---

### Post by ratcheer on 2011-06-02
Thanks, oldfred. I have kept researching this pretty much all day and I am coming to a few conclusions that are similar to yours.

1) Even though everyone on another forum continue to strongly recommend a /boot partition, I have never used one and still don't really see the need for one. If this is wrong, someone please enlighten me.

2) Apparently, everything Ubuntu uses can go into logical partitions, including the swap space. Some people strongly recommend that swap be primary, and others recommend that root be in a primary.

My current 80 GB system has swap in a 2 GB primary, root in a 29 GB primary, and /home in a 19 GB logical. I also have Fedora 15 installed in an 11 GB logical partition in the same extended partition with Ubuntu's /home. This pattern has served me very well for about three years.

So, here is my current thinking:


[LIST]
[*]No /boot unless someone convinces me why it is so good to have one. If I am talked into it, it will be 300 MB ext3. (Can it be ext4? If not, why not?)
[*]2 GB swap primary partition.
[*]Either have or not have the 70 GB primary partition for other OS that might need it.
[*]A big extended partition (maybe 300 GB) for Ubuntu and other Linuxes. If necessary, this can be expanded later, as you said.
[/LIST]
How does that sound?
Tim

---

### Post by oldfred on 2011-06-02
Sounds good to me. But my own optimal partitioning when I got a new drive is now obsolete. Things do change.:)

I also do not think you need a /boot. Some distributions have to have a /boot as they may use a root partition that cannot support booting. May need it if using RAID, LVM or have a very old system with 137GB BIOS boot limit. 

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by srs5694 on 2011-06-02
> **dozycat said:**
> Maybe is overkill but you can get for swap 8gb in case you want to go sleep, you have enough space with the new hard disk.

I concur. I'd go slightly larger (say, 9 or 10 GiB), just to be sure it's big enough, in case of GB/GiB confusion.

> **oldfred]I will only use gpt not MBR/msdos for new drives. But gpt does not work  with all systems unless booting with UEFI and UEFI is just starting to  work for some grub2/Linux systems. Not sure about BSD, but I understand  it does not play well with other systems.[/quote]

This is an extremely important set of comments.

First, does the new system use an old-style BIOS or a new-style UEFI? Most computers that use Intel's new Sandy Bridge are UEFI-based, as are some new AMD systems. The current generation of UEFI has a BIOS compatibility mode, so if you like you can treat the computer as if it were BIOS-based. For Linux purposes, this is the path of least resistance at the moment because Linux distributions' support for UEFI ranges from fair to abysmal (on a scale of excellent-good-fair-poor-abysmal). I'd rate Ubuntu's UEFI support as "fair," FWIW. OTOH, in the long run UEFI is where things are heading, and it's got some advantages. If you plan to keep this computer for as long as you kept the old one, you might want to go with UEFI despite the early hurdles, since there may be future advantages to it. (It's possible to switch at any time, but this may require juggling things around and even re-installing an OS or two.)

Second, the GUID Partition Table (GPT) scheme is superior to the old Master Boot Record (MBR) partitioning system. Among other things, GPT has no concept of extended or logical partitions said:**
> "Booting from GPT"[/url] page for details. I don't know what FreeBSD's state of UEFI support is.

[quote=ratcheer]Even though everyone on another forum continue to strongly recommend a  /boot partition, I have never used one and still don't really see the  need for one. If this is wrong, someone please enlighten me.

A /boot partition is not needed by Ubuntu, at least not in a fairly standard configuration. It is needed if you use GRUB Legacy rather than GRUB 2 and if you use a RAID or LVM configuration. These conditions apply to a standard Fedora installation (which uses GRUB Legacy and LVM), so Fedora users frequently have /boot partitions.

FWIW and IMHO, LVM is worth considering. Using LVM gives you a lot of flexibility about how to use your disk space in the future, particularly if you're not sure how to use it just yet. You can set it up with logical volumes (which are the containers for filesystems, rather than partitions as containers for filesystems) that are sized for something between your known current needs and your best-guess future needs, with lots of space left unallocated in the volume group. Then, if your need for disk space grows in some unexpected way, you can simply resize the relevant logical volume *without worrying about moving other filesystems*. LVM lets you do this because logical volumes can be fragmented, like files on a filesystem. You can even do it while the volume is mounted if you use ext2/3/4fs. You'll lose some performance if you make a lot of changes like this, but probably not that much, and there are ways to "defragment" a volume group, if necessary.

LVM does have drawbacks, though. The biggest is that it's got a bit of a learning curve associated with it, and this is made worse by the fact that Ubuntu provides poor LVM support in its desktop installer. Another drawback is that LVM adds complexity that can complicate data recovery in a disaster situation. (OTOH, the fact that you never need to move the start of a filesystem makes it less likely that you'll never need such disaster recovery.) Linux's LVM is also Linux-only, so it won't help much in allocating space to Linux vs. FreeBSD vs. Windows vs. whatever.

What I've been doing with my recent installations is something like this:

- EFI System Partition and/or BIOS Boot Partition (on GPT disks)
- Non-Linux OS partitions to be installed immediately
- A cross-OS data exchange partition (FAT, NTFS, or HFS+)
- 2-4 ~200MiB partitions to be used as Linux /boot partitions
- ~4 LVM partitions

That last item deserves elaboration: You can use just one partition for LVM in Linux, or you can use several LVM partitions, even on different disks, to combine together for re-allocation in any way you want. Creating several LVM partitions gives some added flexibility, since if there's enough free space in the volume group, you can remove one of those LVM partitions from the volume group and reassign it for use by some other OS. On an MBR disk, I'd want at least one of those LVM partitions to be primary so that it could be used by Windows, FreeBSD, or some other primary-needing OS.

[quote=ratcheer]Apparently, everything Ubuntu uses can go into logical partitions,  including the swap space. Some people strongly recommend that swap be  primary, and others recommend that root be in a primary.[/quote]

AFAIK, there's no advantage to placing swap space in a primary partition. If you go with MBR, conserve your primaries for OSes that need them.

[quote=ratcheer]No /boot unless someone convinces me why it is so good to have one. If I  am talked into it, it will be 300 MB ext3. (Can it be ext4? If not, why  not?)[/quote]

Whatever you do, if you think you might be installing other Linux distributions, you should set things up so that it's *possible* to create a /boot partition, even if it's not absolutely necessary. Personally, I use ext2fs (yes, *2*) for /boot. The reason is that /boot should be small -- mine are 200 MiB -- and the journal of ext3fs chews up too much space on such a small partition, with very little gain. (The journal doesn't improve reliability; it just reduces disk check times after a power failure or system crash, and the time to check a 200 MiB partition is pretty tiny.) Ext4fs's advantages all apply to large partitions and large files, so there's no reason to use it on a separate /boot partition, either.

---

### Post by ratcheer on 2011-06-02
Wow, srs5694, there is a wealth of info in that post. Thank you very much.

Apparently, I have fallen behind the curve on current PC technology. I have never heard of gpt or UEFI, but my new PC should support them because it is the revised Sandy Bridge architecture - P68. I did use to use an LVM on Sun Solaris when I was still working (Veritas Volume Manager with Veritas File System).

How does btrfs fit in with the stuff you have brought up? It sounds like btrfs supports several similar concepts. I found an excellent wiki page on installing Ubuntu 11.04 onto btrfs, but it does still call for a /boot partition. [https://btrfs.wiki.kernel.org/index.php/Getting_started#Ubuntu_Linux_11.04_.28Natty_Narwhal.29_Btrfs_Full_Disk_Encryption](https://btrfs.wiki.kernel.org/index.php/Getting_started#Ubuntu_Linux_11.04_.28Natty_Narwhal.29_Btrfs_Full_Disk_Encryption)

Do gpt and UEFI go together, or are they either/or? I will research them on my own, but please let me know if you have any good links that can explain how to use them.

Again, I really appreciate your in depth reply.

Tim

---

### Post by ratcheer on 2011-06-02
More info: The new PC has a Gigabyte Z68A-D3-B3 motherboard. The BIOS specs say:


[LIST=1]
[*]2 x 32 Mbit flash
[*]Use of licensed AWARD BIOS
[*]Support for DualBIOS&#8482;
[*]PnP 1.0a, DMI 2.0, SM BIOS 2.4, ACPI 1.0b
[/LIST]
I see nothing about UEFI, but I'm still not sure.

PS - I found this in the motherboard product overview:

"Hybrid EFI Technology combines the benefits of GIGABYTE's mature BIOS  platform including stability and compatibility with 3rd party products  with 3TB+ HDD support from **EFI technology**, allowing GIGABYTE to offer  the best of both worlds through a quick and easy BIOS update using  GIGABYTE's @BIOS utility that is freely available from the GIGABYTE  website. 
 GIGABYTE DualBIOS&#8482; is a patented technology that automatically recovers  BIOS data when the main BIOS has crashed or failed. Featuring 2 physical  BIOS ROMs integrated onboard, GIGABYTE DualBIOS&#8482; allows quick and  seamless recovery from BIOS damage or failure due to viruses or improper  BIOS updating. In addition, GIGABYTE DualBIOS&#8482; now supports 3TB+  (terabyte) hard drive booting without the need for partitioning, and  enables more data storage on a single hard drive.         "

Tim

---

### Post by oldfred on 2011-06-02
Almost all my links are to srs5694's web pages on gpt.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

GPT info
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR details including 2TiB limit and GPT link
GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)

I converted one older drive and a flash drive to gpt and boot with BIOS. Actually do not notice much difference, which I think is a good thing.
Apple Macs with Intel use EFI and gpt. 

grub EFI
[http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html](http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html)
How boot a (U)EFI system natively (without BIOS CSM) using GRUB 2
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
Grub2 efi info ArchLinux
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)
Has chainload window efi grub entry:
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by ratcheer on 2011-06-02
Thank you, oldfred. That is a ton of info. Much of it is way over my head. How would you suggest I start? gpt plus BIOS?

Tim

---

### Post by oldfred on 2011-06-03
I think gpt with BIOS is fine. Using gpt lets you have a little more flexibility on partitions, but you will not be able to install windows ever. If you did later want windows just get another drive and make it MBR/msdos. I would also download gdisk from the gdisk link posted above. It is newer than the one in synaptic. But I still use gparted to create partitions. Before creating partitions with gparted change to gpt, under device, advanced choose gpt.

With gpt and BIOS you need a small bios_grub partition just for the part of grub that usually installs just after the MBR. That space does not exist in gpt drives.

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
sudo parted /dev/sda set <partition_number> bios_grub on

It only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues.

---

### Post by srs5694 on 2011-06-03
> **ratcheer said:**
> How does btrfs fit in with the stuff you have brought up? It sounds like btrfs supports several similar concepts.

Yes, Btrfs provides features similar to those of an LVM, but without using an LVM. Btrfs is still officially experimental, though, so at the moment I'd go with LVM and some other filesystem(s) rather than Btrfs if you want those features.

> Do gpt and UEFI go together, or are they either/or? I will research them on my own, but please let me know if you have any good links that can explain how to use them.

GPT is defined as part of the EFI and UEFI specifications. (UEFI being a newer version of EFI.) The two aren't wed, though; you can use GPT without (U)EFI, and you can boot a (U)EFI computer using an MBR disk -- at least in theory. Microsoft ties the two together at least for the boot disk, so if you use a BIOS, you must boot from MBR, and if you use UEFI, you must boot from GPT. Linux isn't limited in that way, though.

> More info: The new PC has a Gigabyte Z68A-D3-B3 motherboard.

Most Sandy Bridge boards use UEFI; however, IIRC there's one manufacturer that's shipping them with a traditional BIOS. I *thought* that was Gigabyte, but much of what you've quoted suggests it's got UEFI firmware, so I might be misremembering, or my information might be incorrect.

It's actually sometimes hard to tell what's going on, since UEFI technology has been working its way into "BIOS" firmware for a while now; it's just been creeping up, or implemented using BIOS compatibility mode with the EFI-style booting disabled.

---

### Post by ratcheer on 2011-06-03
Thanks again, oldfred and srs5694. I am trying to digest it all.

Tim

---

### Post by ratcheer on 2011-06-04
Ok, I have settled on a lot of decisions, but I still have a few questions.

I have decided that, unless UEFI is working on my new PC by default, which I doubt will be the case, I will use the normal BIOS.

I intend to use gpt partitioning. However, I have not found a way to do this at installation, all the methods I have found are to convert an existing installed system from mbr to gpt. Is there a way to invoke creation of the gpt partitioning at Ubuntu install time?

I am strongly considering using LVM at install time, and I have found instructions for doing this. The instructions say to put /, /boot, and swap into normal partitions and manually create /srv in an LVM volume. Next question - can I create /home in the LVM volume instead of /srv? I don't see any logical reason why not, but I'd like to be sure.

Finally, if I have to convert from mbr partitioning to gpt after the installation has completed, will having set up LVM at installation interfere with doing it?

I will probably have more questions, later.

Thanks,
Tim

---

### Post by oldfred on 2011-06-04
I always partition in advance, then use manual install to choose & format partitions with the installer.

With gparted just choose gpt under devices advanced before anything else. You can also use gdisk from command line. 

Do not know about LVM.

---

### Post by srs5694 on 2011-06-04
> **ratcheer said:**
> I intend to use gpt partitioning. However, I have not found a way to do this at installation, all the methods I have found are to convert an existing installed system from mbr to gpt. Is there a way to invoke creation of the gpt partitioning at Ubuntu install time?

Unfortunately, the Ubuntu installer doesn't give you an explicit option for this; it uses what is present or, if the disk is unpartitioned, uses MBR for disks smaller than ~1TB and GPT for larger disks. (I don't know what the exact cutoff value is.) If you want to be sure which you use, you can partition the disk yourself before you begin. You can do this by booting into the "try it now" mode (or whatever exactly it's called) and use GParted or gdisk. (I'm not sure if either is installed by default.) In GParted, select Device -> Create Partition Table, click the Advanced button, and select "gpt" as the partition table type. In gdisk, launch it on the disk from a shell ("sudo gdisk /dev/sda") and then type "w" to write an empty partition table. In either, you can create partitions, too. (GParted lets you create filesystems in the partitions, but gdisk doesn't.) In fact, I'd recommend creating at least one partition in this way so that you're sure the installer doesn't look at a defined but empty partition table and decide to change it to the other type. Try creating a BIOS Boot Partition of 1 MiB. In GParted, set its "bios_grub" flag. In gdisk, give it a type code of EF02. You might also want to create an EFI System Partition of ~200 MiB, too, just in case you decide to switch to EFI boot mode in the future. In GParted, make it a FAT32 partition and set the "boot" flag. In gdisk, give it a type code of EF00.

> I am strongly considering using LVM at install time, and I have found instructions for doing this. The instructions say to put /, /boot, and swap into normal partitions and manually create /srv in an LVM volume. Next question - can I create /home in the LVM volume instead of /srv? I don't see any logical reason why not, but I'd like to be sure.

First, you don't need to put any of the directories you mention in normal partitions if you're using GRUB 2, although putting /boot in a normal partition will give you more options for boot loaders, so I'd recommend doing that. You significantly reduce the utility of LVM by putting root (/) in a normal partition, and slightly reduce it by putting swap in a normal partition.

Second, /srv isn't a standard partition. From its name, I'm guessing that your source document uses that directory to store files for a server program. You can certainly store /home in the LVM. In fact, if you were to put root (/), /boot, and swap in normal partitions, there wouldn't be much else to put in the LVM unless you split off some other directory, like /usr or /tmp.

> Finally, if I have to convert from mbr partitioning to gpt after the installation has completed, will having set up LVM at installation interfere with doing it?

No. I've done such conversions. (As the author of gdisk, which is one of the few programs to do it, I was probably one of the first, if not *the* first, to do so, and I didn't have any problems even on my first conversion.)

---

### Post by ratcheer on 2011-06-04
Excellent info as always, gentlemen. Thank you very much. Now I just have to wait for the new PC (delivery is estimated by end of the day, Monday), then I can go to work,

Tim

---

### Post by ratcheer on 2011-06-07
The new PC came yesterday. I cannot get it to work. It will not install any Linux CD or DVD, a flash drive, or even a Parted CD. It will boot any of them except the flash drive, but when I try to install any of them, it loses track of the CD or DVD.

See my other thread for details.

[http://ubuntuforums.org/showthread.php?t=1776797](http://ubuntuforums.org/showthread.php?t=1776797)

Tim

---

### Post by ratcheer on 2011-06-10
I finally got the new PC loaded with Ubuntu 11.04 AMD64, but it was so much trouble my grand partitioning plans were lost in the shuffle.

What I ended up with is a /boot primary of 300 MB, and an extended partition with logical partitions of 11.2 GB for root, 35.4 GB for /home, and an 8.4 GB swap partition.

After all the excitement was over, I installed gdisk and converted the drive to gpt. gpt reports that Partition 2 does not begin on an 8-sector boundary. I know that things will work perfectly well, this way, but should it be fixed? If so, is there a non-destructive way to do it?

```

GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 857D7DD4-515A-442E-8C38-5D1AD3F59D47
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 8-sector boundaries
Total free space is 1837710735 sectors (876.3 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          585727   285.0 MiB   0700  Linux/Windows data
   2              34            2047   1007.0 KiB  EF02  BIOS boot partition
   5          587776        24023039   11.2 GiB    0700  Linux/Windows data
   6        24025088        98242559   35.4 GiB    0700  Linux/Windows data
   7        98244608       115820543   8.4 GiB     8200  Linux swap

Command (? for help): v

Caution: Partition 2 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.
No problems found. 1837710735 free sectors (876.3 GiB) available in 4
segments, the largest of which is 1837704591 (876.3 GiB) in size.


```Thanks,
Tim

---

### Post by srs5694 on 2011-06-10
Don't worry about it. The BIOS Boot Partition is read when the computer first boots and is not read thereafter. It's written only when you re-install GRUB (as in "sudo grub-install /dev/sda"). The performance problems for misaligned partitions mostly affect writes to many small files. Given the way the BIOS Boot Partition is used, I'd be shocked if your boot times suffered by as much as 0.1 second, and even re-installing GRUB is unlikely to be noticeably affected. It's also an issue only if your disk is an Advanced Format model. My impression is that a lot of the recent disks are Advanced Format, but not all of them are, so it's conceivable yours isn't one.

All that said, if you decide you do want to clean it up just to avoid seeing the gdisk warning, you can delete it and create a new partition that's just a bit smaller (starting at sector 40, for instance). You'll then need to reboot and then re-install GRUB ("sudo grub-install /dev/sda"). There's a chance that this will go wrong, though, so I wouldn't bother.

---

### Post by ratcheer on 2011-06-10
Thank you. I won't mess with it.

Tim

---

