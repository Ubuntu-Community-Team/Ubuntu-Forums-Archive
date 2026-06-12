---
title: "Advice on 2-disk partitioning scheme"
date: 2012-06-02
forum: Installation &amp; Upgrades
---

### Post by digisus on 2012-06-02
Hello,

I bought a new PC \\:D/ with 2 SATA HDs (1TB each) to run Ubuntu exclusively with me as the only user.

I would like to use the first HD for:
- /, the system
- swap -- if still needed? (I have 8G RAM)
- Another / partition, unmounted, for easy switching to new installs in the future
- the Videos folder in /home (to make use of the huge disk with data that is not crucial if lost)

Second HD:
- /home

My questions: 
- How would a good partitioning scheme incl. mount points look like?
- Does it matter whether hda or hdb is the system disk?
- Any reasons to leave free space on the disk(s)?
- Should I define partitions for /Documents, /Music, etc. separately? (If yes, how can it be done that it is seamless in Nautilus and not 5 additional devices?)

Thank for sharing your experience!
digisus

PS. Sent from my laptop. If needed, I can upload the partitioning I tried yesterday, but it does not work... no read access to any of the home folders... no booting unless I switch the boot HD (no idea why that happened)... just let me know.

---

### Post by oldfred on 2012-06-02
Just to complicate things have you considered gpt. It is a new partitioning scheme instead of MBR(msdos) and is required for drives over 2TB and recommended for SSDs. You can stay with MBR since both drives are 1TB.

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

When you have separate data partitions, I prefer to keep /home inside / with only the hidden user files & folders. I also move some hidden folders with lots of data to my data partition also, so my /home is less than 1GB even with .wine for Picasa.

I still recommend some swap, but you may never use it. Someone posted that while booting it looks for swap and has to time out if not found, so having some helps booting a bit. Others with lots of RAM say they have not had swap and it works just fine.

I like to have a system on every drive with its boot loader on the same drive & all its required partitions including /home on the same drive. Then each drive is independently bootable. Then I mount all my data partitions form various drives, but if a drive fails, other drive's system will boot even if mounting a data partition fails.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

I plan on a new system with UEFI soon, so I create both an efi partition since it has to be first and would be difficult to add later, a bios_grub partition as that is required with BIOS boot and gpt partitioning and gpt partitions.

For the Total space you want for Ubuntu, standard suggestion with separate /home:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

I actually do not use a separate /home anymore as all my data is in data partitions.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Another way to share:
Morbius1 uses bind, now:
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead for fstab entries. Post #6

---

### Post by digisus on 2012-06-04
oldfred, thank you very much for the exhaustive reply!

As the whole GPT and UEFI stuff is completely new for me, I spent some hours yesterday to read all your links and some more. To be honest, I am quite overwhelmed .. both seem to be very new areas with information spread in bits and pieces across the web. Up to now I could not find any step-by-step guide on how to get UEFI set up and an install procedure for GPT that *is clear to me*. :-k

In other words, I still do not know where to start. I am not even sure whether the following questions make sense... :roll:

**1)** Could not find any UEFI switching on/off in the BIOS although the product spec says it is supported. How do I tell the BIOS that I'd like to switch on UEFI? And: Is that enough then or do I need to 

**2)** What happens if I skip 1) and just select GPT in a new install of 12.04? Does it just work or do I need to set a BIOS boot partition because of GRUB2?
 
**3)** If the boot partition is needed, can I do that during install or do I need to come in from a live CD? If live CD, is it enough to onyl set up the boot partition and all other partitions will be done later during install process? And: Do I need to use a specific size to align on 4096-byte blocks for newer HDs? If yes, how to determine the size (I read somewhere it needs to be 1MiB)?

**4)** Goes GPT require a 64-bit ubuntu?

**HW specification**:
- Shuttle XPC SH61R4 with Shuttle Mainboard FH61, [http://www.shuttle.eu/fileadmin/resources/download/docs/spec/barebones/SH61R4_e.pdf](http://www.shuttle.eu/fileadmin/resources/download/docs/spec/barebones/SH61R4_e.pdf)
- BIOS American Trends, Aptio 2.02.1205
- Intel i3-2100T

Thanks for having another look!
If it turns out to be laborious to figure out remotely what steps I need to do, please do not bother. Right now, I think I will do it the same old way as I did in the last years and not bother about new boot procedures or new partition schemes, but rather wait 1-2 releases until things are more streamlined for me to understand and use. :-)

Thanks in any case for your help! :-)

---

### Post by dino99 on 2012-06-04
- BIOS American Trends, Aptio 2.02.1205

so that it, you does not have a uefi but a bios; it cant be switched

---

### Post by digisus on 2012-06-04
Thanks dino99.
Hm, OTOH if I boot from the USB stick it gives me the choice with boot devices... and one says "UEFI: <name-of-usb-key>" aside the normal "<name-of-usb-key>.
But yes, you are probably right because if I choose the UEFi option, nothing happens and it boots from HD.

---

### Post by oldfred on 2012-06-04
Those that have gotten UEFI to work have Partitioned in advance. But if you use gpt and want Windows you have to boot in UEFI mode. You cannot have Ubuntu in BIOS mode & Windows in UEFI mode (as far as I know). Both Windows & Ubuntu seem to install in UEFI mode if you boot installer in UEFI mode. 

Some BIOS have a switch and some just seem to look for efi partition and if not found revert to BIOS mode.

I use gpt with BIOS to boot from both a 8GB partition on my flash drive (testing only)  and my SSD in a 25GB root partition with all my data on my rotating drives. I have the bios_grub 1MB unformated partitions and grub2 just installs like normal.

I suggest both the efi & bios_grub, but you can actually only use one or the other. With new large drives they take very little space.

In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

With BIOS mode & gpt, you install the grub2 boot loader like normal to the MBR, the bios_grub partition is just used automatically to store core.img. In MBR formating core.img is written automatically to the sectors just after the MBR which do not exist in gpt partitioning. 
With UEFI the boot loader is installed in the efi partition, but that is just the efi bootloader not a separate /boot partition (which for standard desktops, I do not recommend).

GUIDE: (U)EFI installation Also full install post *52 superfreak
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)

Some instructions out there discuss recompiling grub2 to get it to work. But not required with the new versions.

---

### Post by flemur13013 on 2012-06-04
FWIW, I agree with "oldfred" - entire OS and /home on one partition (20GB, use is typically 3.5 to 10 GB), data in another partition.  I have "/home/username/Music" etc, directories, but they only hold a few files at a time, then the files are moved to /data/music (or whatever), on a different partition (200GB), after they're sorted out.

---

