---
title: "After Lucid installation, my puter won't boot."
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by tarahmarie on 2010-08-29
Hi, all:

I changed out the CMOS battery, flashing the BIOS. I also changed out my primary HD, going to a 2TB WD Caviar Black (I know, I know. You're jealous--but try to restrain yourselves, cuz apparently there's a 2TB limit I didn't know about on GParted).

I used the Kubuntu LiveCD to format my HD and install Lucid; I divvied it up as many of us do into 4 partitions or so, and installed the OS to /, nothing to /altos (that will be a Mandriva install one day in happier times), the bootloader to /locked, and nothing to /home, where I've transferred all my stuff now.

When I attempt to boot after install, I get a message saying "Intel Boot Agent failed to find a bootable disk". I am able to boot by using the LiveCD and choosing teh 'boot from first hard drive' option.  I am aware that all this has to do with a 2TB limit for Gparted (or something like that), but I thought it was a PARTITION limit, not a HARD DRIVE limit. My /home is 1950GB, putting it safely under the limit. 

That bootloader, as previously mentioned, was installed to /locked (sda3, I think). I was going to use that partition for financials and stuff, but this is the second time I tried an install to this HD. I had the same error the first time, and I wanted teh bootloader where I could put my hands on it.

tarahmarie@tarahmarie-desktop:~$ grub-install -v
grub-install (GNU GRUB 1.98-1ubuntu7)

That's so you can see it's installed.

Ok, here's teh question: why won't my puter boot?  Do I need to properly configure grub2 somehow? If so, does it have something to do with GPT? I've been going through threads for a day now, and all I am is more confused.

---

### Post by oldfred on 2010-08-29
Some BIOS (intel?) require a boot flag on a primary partition to allow booting. Grub does not use the boot flag but windows has to have one, so the BIOS must think everyone has windows.

If you used gpt partitions you do not have the 2TiB limit. That limit is for msdos (MBR) partitions. MBR has a four partition limit but one partition can be converted to an extended an hold additional logical, but you still have a 2TiB limit.

If you create a boot partition you should not be using it for other things. I do not recommend a separate boot partition for desktop installs unless you have an old BIOS that requires it at the front of the disk or a few other special cases.

If you are going to have multiple installs you should think about 20-25GB system partitions for each install (including boot & /home) and separate /data partition for all your data. Then you can mount data without any conflicts that may happen if you attempt to share boot or home partitions. If you have some settings in /home that you know will work in another install you can copy them, but different versions of software may have different config files in /home.

Partitioning basics with some info on /data older but still valid by bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)

Herman on advantages/disadvanges of separate system partitions
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

To see what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by tarahmarie on 2010-08-29
To the best of my ability to tell, I have a problem with the BIOS not finding the boot partition.

I get the Intel Boot Agent seeking for a bootable disk and not finding one. 

I tried to reinstall grub2 to the MBR on my primary HD (sda), but got this as an error message:

/usr/sbin/grub2-install --recheck --no-floppy /dev/sda --force
grub-setup: warn: This GPT partition label has no BIOS Boot Partition;
embedding won't be possible!
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in
this setup by using blocklists.  However, blocklists are UNRELIABLE and its
use is discouraged.
Installation finished. No error reported. 

WTH?

---

### Post by oldfred on 2010-08-29
If you have gpt you need another small (8-32mb) partition for grub. Are you using efi or BIOS compatible mode?

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.  Thus, you must make a separate "BIOS boot partition" to hold core.img.  Make it 128 kiB as recommended in the following link.  Actually, using ext2 for example, and GParted Live CD, the minimum partition size is 8 MB, or 32 MB for FAT32. You can set bios_grub flag in gparted or with command line:
sudo parted /dev/sda set <partition_number> bios_grub on
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
"unknown" filesystem! may be shown
grub EFI
[http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html](http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html)

---

### Post by srs5694 on 2010-08-29
The BIOS Boot Partition that oldfred describes *may* be the cause of the problem. GRUB 2 *can usually* work without it, but it's more reliable with this partition, and I've seen reports that some versions of GRUB 2 just plain don't work without it. The BIOS Boot Partition can be very small, so you may be able to squeeze it in even if the disk is already (almost) completely allocated.

There are a number of other [BIOS issues with GPT,](http://www.rodsbooks.com/gdisk/bios.html) which amount to BIOS bugs with specific BIOS versions. Oldfred has already alluded to one of these issues, in that some BIOSes (particularly on some Intel boards) require a boot/active flag to be set on an MBR primary partition before they'll boot. This is a completely brain-dead design, but some (not all, just some) BIOSes are designed this way. Check my link for other issues. Please post detailed motherboard and BIOS information (model and revision numbers) if you need more help with this.

---

### Post by tarahmarie on 2010-08-29
Ok, I tried doing precisely that: I created an 8MB ext3 partition as sda1. It's right at the front (notably, in the Kubuntu installer, it shows 1MB of free space in front of that partition, and I apparently can't do anything with it). I mounted it at /boot. Grub2 was installed to it during a reinstall of Kubuntu.

After that reinstallation completed, I executed 'sudo parted /dev/sda set 1 bios_grub on', and rebooted.

I'm still faced with the same problem; no boot. Here is more detailed information:

BIOS version: DPP3510J.86A.0437.2008.0521.1993

Here's the error I get on booting (this is as exact as I can make it, not being able to cut and paste...so forbear if I've gotten something wrong):

Intel (R) Boot Agent GE v1.2.22

CLIENT MAC ADDR: XX XX XX XX XX XX GUID: DC8EF94C 1816 11DD ADE8 0013D4E33164

PXE-E53: No boot filename received.

PXE-MOF: Exiting Intel Boot Agent
No bootable device -- insert boot disk + press any key


That's what happens when nothing will boot. I've blanked my MAC for security's sake.

It's like it's trying to boot from network, but that's disabled in BIOS.

---

### Post by srs5694 on 2010-08-29
I think you misunderstand what the BIOS Boot Partition is. It is *not* part of the Linux installation per se; it's used prior to Linux booting, by GRUB 2. You should *not* mount it as part of the Linux installation process. If you want to have a separate /boot partition, that's fine, but that should be a regular Linux partition, not a BIOS Boot Partition. You should flag the BIOS Boot Partition as such *before* you install Linux -- or at least before you install GRUB 2. Doing it afterwards, as you did, will do absolutely no good and may actually harm your installation, if you also used it for /boot, as it sounds like you did.

Also, it sounds like you've got an Intel motherboard. Some Intel BIOSes are known to require an MBR partition to be flagged as active/bootable. Thus, if you try again with the BIOS Boot Partition as just described, and if it still doesn't boot, you should use Linux fdisk to set the GPT (type-0xEE) partition in the MBR as active/bootable. AFAIK, this can't be done by GParted on GPT disks, although GParted does have an option to set this flag on MBR disks. You'll have to use fdisk for this job.

---

### Post by tarahmarie on 2010-08-30
> **srs5694 said:**
> I think you misunderstand what the BIOS Boot Partition is. It is *not* part of the Linux installation per se; it's used prior to Linux booting, by GRUB 2. You should *not* mount it as part of the Linux installation process. If you want to have a separate /boot partition, that's fine, but that should be a regular Linux partition, not a BIOS Boot Partition. You should flag the BIOS Boot Partition as such *before* you install Linux -- or at least before you install GRUB 2. Doing it afterwards, as you did, will do absolutely no good and may actually harm your installation, if you also used it for /boot, as it sounds like you did.


How do I flag the BIOS boot partition?

---

### Post by srs5694 on 2010-08-30
> **tarahmarie said:**
> How do I flag the BIOS boot partition?

You did it before:

```

sudo parted /dev/sda set 1 bios_grub on

```

---

### Post by tarahmarie on 2010-08-30
I must be confused:

(1) Make a small partition near the beginning.
(2) Install grub2 to that partition.
(3) Flag it to the bios using this code: sudo parted /dev/sda set 1 bios_grub on


That is what I did.  What am I not understanding?

---

### Post by tarahmarie on 2010-08-30
> **srs5694 said:**
> I think you misunderstand what the BIOS Boot Partition is. It is *not* part of the Linux installation per se; it's used prior to Linux booting, by GRUB 2. You should *not* mount it as part of the Linux installation process. If you want to have a separate /boot partition, that's fine, but that should be a regular Linux partition, not a BIOS Boot Partition. You should flag the BIOS Boot Partition as such *before* you install Linux -- or at least before you install GRUB 2. Doing it afterwards, as you did, will do absolutely no good and may actually harm your installation, if you also used it for /boot, as it sounds like you did.


How would I create a partition that is not part of the Linux installation?  I'm using the partition editor found on the Kubuntu LiveCD. In addition, if it's not mounted or found by the Linux install, how do I do anything to do it in bash if I can't mount it?

---

### Post by oldfred on 2010-08-30
I converted a small 160GB drive to GPT and use gpt on my 16GB flash drive just to see how it works.

You just create the small partition and set bios_grub on. You do not do anything with it. Then when you install grub automatically finds it and puts part of its code into it. 

I do notice that when I run the boot_info script it tells me it is an unknown partition and that my grub core.img cannot be found, but that is because the script is not yet set up to parse gpt bios-grub partitions.

---

### Post by tarahmarie on 2010-08-30
> **oldfred said:**
> I converted a small 160GB drive to GPT and use gpt on my 16GB flash drive just to see how it works.

You just create the small partition and set bios_grub on. You do not do anything with it. Then when you install grub automatically finds it and puts part of its code into it. 

I do notice that when I run the boot_info script it tells me it is an unknown partition and that my grub core.img cannot be found, but that is because the script is not yet set up to parse gpt bios-grub partitions.

When viewing my drive (sda), it's currently divided into:

1MB free space
10MB ext3 /boot
20GB ext3 /
10GB ext3 /altos
1950GB ext3 /home
1MB free space

Here is what I did last time.

(1) Stick the Kubuntu LiveCD in.
(2) Boot the installer.
(3) Format the /boot partition and the / partition. Mount them both, as well as /altos and /home.
(4) Install Kubuntu.
(5) Use the LiveCD to boot up the computer, since it won't boot as is, and won't boot to the first hard drive.
(6) Mount the /boot partition.
(7) Use the bios_on command.
(8) Watch as absolutely nothing happens and my puter still won't boot.

Please explain what you mean by 'create a small partition'. What about me creating /boot as a small partition DIDN'T work? Kubuntu is finding /boot and installing grub2 to it; why isn't that working? Do I need to not use the Kubuntu LiveCD to create the partitions?

---

### Post by oldfred on 2010-08-30
I actually do not recommend /boot partitions for most desktops as it unnecessarily complicates things. 

I just used gparted and created the smallest (8MB) FAT32 partition I could and set bios-grub on. I think the EF02 code says it is the bios_grub partition. Then I did my install of Ubuntu.

I think you could just create the 8MB fat partition and set bios-grub on. Then reinstall grub and it will find it. Having a separate /boot partition makes the reinstall of grub a little more complicated as you also have to mount that partition.

Most of the partition listing tools do not even show sdb1.
```
fred@fred-LucidDT:~$ sudo gdisk -l /dev/sdb
[sudo] password for fred: 
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 312581808 sectors, 149.1 GiB
Disk identifier (GUID): 8309E92E-0149-4DB4-9AF3-AA60B26ED1D1
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 312581774
Total free space is 5070 sectors (2.5 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34           16064   7.8 MiB     EF02  
   2           16065        51215219   24.4 GiB    0700  
   3        51215220        57352049   2.9 GiB     8200  
   4        57352050       312576704   121.7 GiB   0700  
fred@fred-LucidDT:~$ 


```

---

### Post by srs5694 on 2010-08-30
> **tarahmarie said:**
> Here is what I did last time.

(1) Stick the Kubuntu LiveCD in.
(2) Boot the installer.
(3) Format the /boot partition and the / partition. Mount them both, as well as /altos and /home.
(4) Install Kubuntu.
(5) Use the LiveCD to boot up the computer, since it won't boot as is, and won't boot to the first hard drive.
(6) Mount the /boot partition.
(7) Use the bios_on command.
(8) Watch as absolutely nothing happens and my puter still won't boot.

Please explain what you mean by 'create a small partition'. What about me creating /boot as a small partition DIDN'T work? Kubuntu is finding /boot and installing grub2 to it; why isn't that working? Do I need to not use the Kubuntu LiveCD to create the partitions?

Step #7 is 100% useless *when* you did it. You should issue that command either *before* you do anything else (step #0) or, if the installer has that command, between steps 2 and 3.

The partition you flag as the BIOS Boot Partition is *not* mounted in Linux. It is *not* the same as the /boot partition. Rather, it holds something on the order of 30KB of data that's used by GRUB during the boot process, before Linux itself is running. You can create the BIOS Boot Partition with Linux tools, but it's not a Linux filesystem per se. Try as an analogy some residential property (that's your hard disk). The Linux installation (the house you build on that property) has a number of rooms (partitions that are mounted in the Linux directory tree). The BIOS Boot Partition, though, is more like a detached garage or utility shed -- it's part of the property (hard disk), but it's not part of the house (Linux directory tree). Nonetheless (and here the analogy breaks down), you can't boot Linux without the BIOS Boot Partition, and the Linux installer (particularly the GRUB installation that occurs as part of the Linux installation) stores data in the BIOS Boot Partition.

Another way of looking at this: Every time you boot the computer, the following steps happen:


[list=1]
[*]The BIOS runs miscellaneous hardware checks.
[*]The BIOS reads the first sector of the hard disk and executes the program it finds there. This is the *stage 0 boot loader.*
[*]The stage 0 boot loader accesses the hard disk and loads more data from it. In the case of a GPT disk with GRUB 2, the stage 0 boot loader tries to read this data from the BIOS Boot Partition. (Hence that partition's name.) This step is necessary because the first sector of the hard disk is only 512 bytes in size, so more complex code has to be stored elsewhere.
[*]The BIOS Boot Partition code loads the Linux kernel from a Linux partition.
[*]The Linux kernel begins running Linux programs, ultimately leading to a Linux login prompt or desktop display.
[/list]


This is a bit of a simplification, but as you can see, the BIOS Boot Partition comes into play *before* Linux boots, and it's not accessed afterwards (unless you need to update it).

---

### Post by tarahmarie on 2010-08-30
Ok, I can't use gparted with the live cd, but I can use parted at the CL.  

Should I do precisely this to create the small partition you're talking about?

(1) Boot with the live cd.
(2) Do NOT mount sda.
(3) Use this at the CL:

```

sudo parted /dev/sda mkfs 1 fat32
sudo parted /dev/sda set 1 bios_grub on

```

---

### Post by tarahmarie on 2010-08-30
> **srs5694 said:**
> Step #7 is 100% useless *when* you did it. You should issue that command either *before* you do anything else (step #0) or, if the installer has that command, between steps 2 and 3.

The partition you flag as the BIOS Boot Partition is *not* mounted in Linux. It is *not* the same as the /boot partition. Rather, it holds something on the order of 30KB of data that's used by GRUB during the boot process, before Linux itself is running. You can create the BIOS Boot Partition with Linux tools, but it's not a Linux filesystem per se. Try as an analogy some residential property (that's your hard disk). The Linux installation (the house you build on that property) has a number of rooms (partitions that are mounted in the Linux directory tree). The BIOS Boot Partition, though, is more like a detached garage or utility shed -- it's part of the property (hard disk), but it's not part of the house (Linux directory tree). Nonetheless (and here the analogy breaks down), you can't boot Linux without the BIOS Boot Partition, and the Linux installer (particularly the GRUB installation that occurs as part of the Linux installation) stores data in the BIOS Boot Partition.

Another way of looking at this: Every time you boot the computer, the following steps happen:


[list=1]
[*]The BIOS runs miscellaneous hardware checks.
[*]The BIOS reads the first sector of the hard disk and executes the program it finds there. This is the *stage 0 boot loader.*
[*]The stage 0 boot loader accesses the hard disk and loads more data from it. In the case of a GPT disk with GRUB 2, the stage 0 boot loader tries to read this data from the BIOS Boot Partition. (Hence that partition's name.) This step is necessary because the first sector of the hard disk is only 512 bytes in size, so more complex code has to be stored elsewhere.
[*]The BIOS Boot Partition code loads the Linux kernel from a Linux partition.
[*]The Linux kernel begins running Linux programs, ultimately leading to a Linux login prompt or desktop display.
[/list]


This is a bit of a simplification, but as you can see, the BIOS Boot Partition comes into play *before* Linux boots, and it's not accessed afterwards (unless you need to update it).

I am beginning to understand now.  Are the steps I just outlined how I'll create that 8MB BIOS boot partition? Let's get that straight before I worry about how to install grub2 to it.

---

### Post by srs5694 on 2010-08-30
> **oldfred said:**
> I just used gparted and created the smallest (8MB) FAT32 partition I could and set bios-grub on. I think the EF02 code says it is the bios_grub partition. Then I did my install of Ubuntu.

[FONT=monospace]Y[/FONT]es, "EF02" in GPT fdisk corresponds to the "bios_grub flag" being set in GNU Parted. The two programs just have different ways of referring to the underlying GPT data structures. Either program can create a suitable partition.

FWIW, libparted (upon which GNU Parted, GParted, and several other Linux partitioning tools) employs layers of abstraction that has the effect of obfuscating the underlying disk data structures. When I wrote GPT fdisk, I made the conscious decision to enable more direct editing of the true data structures. "EF02" is a shorthand code, not the real data that gets stored, but otherwise, GPT fdisk shows something that's closer to the truth than libparted-based tools show. This fact isn't really critical to the main problem under discussion, though; whether you think of a BIOS Boot Partition as having a particular type code or as having a particular flag set, the issue is that the partition must exist *and be correctly flagged/typed* when GRUB is installed. Furthermore, the partition must *not* be mounted by Linux by default, or even be set to be mountable, since it won't contain a valid filesystem once GRUB has used it. (Any filesystem on the partition will be destroyed by GRUB.)

---

### Post by tarahmarie on 2010-08-30
> **srs5694 said:**
> [FONT=monospace]Y[/FONT]es, "EF02" in GPT fdisk corresponds to the "bios_grub flag" being set in GNU Parted. The two programs just have different ways of referring to the underlying GPT data structures. Either program can create a suitable partition.

FWIW, libparted (upon which GNU Parted, GParted, and several other Linux partitioning tools) employs layers of abstraction that has the effect of obfuscating the underlying disk data structures. When I wrote GPT fdisk, I made the conscious decision to enable more direct editing of the true data structures. "EF02" is a shorthand code, not the real data that gets stored, but otherwise, GPT fdisk shows something that's closer to the truth than libparted-based tools show. This fact isn't really critical to the main problem under discussion, though; whether you think of a BIOS Boot Partition as having a particular type code or as having a particular flag set, the issue is that the partition must exist *and be correctly flagged/typed* when GRUB is installed. Furthermore, the partition must *not* be mounted by Linux by default, or even be set to be mountable, since it won't contain a valid filesystem once GRUB has used it. (Any filesystem on the partition will be destroyed by GRUB.)

This conversation's getting a bit over my head again ;-)

Are the steps I outlined above going to convert the 10MB /boot partition at sda1 that I had set up into the BIOS boot partition needed?

---

### Post by srs5694 on 2010-08-30
> **tarahmarie said:**
> I am beginning to understand now.  Are the steps I just outlined how I'll create that 8MB BIOS boot partition? Let's get that straight before I worry about how to install grub2 to it.

Try this, *if* you're willing to wipe the disk:


[list=1]
[*]Boot an Ubuntu installer or an emergency disc, like [Parted Magic](http://gparted.sourceforge.net/) or [System Rescue CD.](http://www.sysresccd.org/) If using an Ubuntu installer, boot it into a recovery mode so that you can get a shell rather than booting straight into the installer.
[*]Launch a text-mode shell.
[*]If you're using an Ubuntu installer, type "sudo apt-get install gdisk" to obtain and install GPT fdisk (gdisk).
[*]Type "sudo gdisk /dev/sda" (you can omit "sudo" on some emergency disks).
[*]Type "o" and answer "y" to the verification prompt to create a fresh partition table. Note that this will wipe out all your existing partitions.
[*]Type "n" to create a new partition. Give values of: partition #1, start sector 2048, end sector +1M, hex code of EF02. This creates the BIOS Boot Partition.
[*]Type "n" to create another new partition. Give values of: partition #2, hit enter for the default start sector, end sector +20G (or however big you want the Ubuntu main installation to be, minus space for your user files), hex code of 0700 (the default). This creates what will be the Linux root (/) partition.
[*]Type "n" to create another new partition. Give values of: partition #3, hit enter for the default start sector, end sector +2G (or however big you want to make your swap space), hex code of 8200. This creates a Linux swap partition.
[*]Type "n" to create another new partition. Give values of: partition #4, hit enter for the default start sector, hit enter for the default end sector (to use the whole disk), hex code 0700 (the default). This creates what will be the Linux /home partition. If you want other partitions, you should set some other end value and create additional partitions at this point.
[*]Type "p" to review your partition table. It should have an EF02 BIOS Boot Partition, two Linux/Windows data partitions, and a Linux swap partition. If it doesn't, correct the problems or quit by typing "q" and start again.
[*]Type "w" to save the partition table.
[*]If necessary, reboot into the Ubuntu installer; or just launch the installation process. When you get to the disk partitioning section, tell the system to do custom partitioning, but *do not* start from scratch. Instead, tell it to use /dev/sda2 as root (/), /dev/sda3 as swap, and /dev/sda4 as /home. (Adjust these partition IDs as necessary, if you deviated from the numbers I specified earlier.) The installer will create new filesystems or swap space on these partitions. You should *not* tell the installer to do anything with /dev/sda1; when the system installs GRUB, the GRUB installer should use /dev/sda1 automatically.
[*]Continue with the installation.
[/list]


It's possible to use GNU Parted or GParted instead of GPT fdisk in the preceding procedure. It may be possible to use the installer's disk partitioner, too, but I'm not positive of that. I just specified GPT fdisk because I'm more familiar with its syntax and I didn't want to experiment with other tools to write this reply.

---

### Post by tarahmarie on 2010-08-30
> **srs5694 said:**
> Try this, *if* you're willing to wipe the disk:


[list=1]
[*]Boot an Ubuntu installer or an emergency disc, like [Parted Magic](http://gparted.sourceforge.net/) or [System Rescue CD.](http://www.sysresccd.org/) If using an Ubuntu installer, boot it into a recovery mode so that you can get a shell rather than booting straight into the installer.
[*]Launch a text-mode shell.
[*]If you're using an Ubuntu installer, type "sudo apt-get install gdisk" to obtain and install GPT fdisk (gdisk).
[*]Type "sudo gdisk /dev/sda" (you can omit "sudo" on some emergency disks).
[*]Type "o" and answer "y" to the verification prompt to create a fresh partition table. Note that this will wipe out all your existing partitions.
[*]Type "n" to create a new partition. Give values of: partition #1, start sector 2048, end sector +1M, hex code of EF02. This creates the BIOS Boot Partition.
[*]Type "n" to create another new partition. Give values of: partition #2, hit enter for the default start sector, end sector +20G (or however big you want the Ubuntu main installation to be, minus space for your user files), hex code of 0700 (the default). This creates what will be the Linux root (/) partition.
[*]Type "n" to create another new partition. Give values of: partition #3, hit enter for the default start sector, end sector +2G (or however big you want to make your swap space), hex code of 8200. This creates a Linux swap partition.
[*]Type "n" to create another new partition. Give values of: partition #4, hit enter for the default start sector, hit enter for the default end sector (to use the whole disk), hex code 0700 (the default). This creates what will be the Linux /home partition. If you want other partitions, you should set some other end value and create additional partitions at this point.
[*]Type "p" to review your partition table. It should have an EF02 BIOS Boot Partition, two Linux/Windows data partitions, and a Linux swap partition. If it doesn't, correct the problems or quit by typing "q" and start again.
[*]Type "w" to save the partition table.
[*]If necessary, reboot into the Ubuntu installer; or just launch the installation process. When you get to the disk partitioning section, tell the system to do custom partitioning, but *do not* start from scratch. Instead, tell it to use /dev/sda2 as root (/), /dev/sda3 as swap, and /dev/sda4 as /home. (Adjust these partition IDs as necessary, if you deviated from the numbers I specified earlier.) The installer will create new filesystems or swap space on these partitions. You should *not* tell the installer to do anything with /dev/sda1; when the system installs GRUB, the GRUB installer should use /dev/sda1 automatically.
[*]Continue with the installation.
[/list]


It's possible to use GNU Parted or GParted instead of GPT fdisk in the preceding procedure. It may be possible to use the installer's disk partitioner, too, but I'm not positive of that. I just specified GPT fdisk because I'm more familiar with its syntax and I didn't want to experiment with other tools to write this reply.

God bless you, I am totally willing to wipe the disk and start over, and I will let you know how it goes in a few hours.

---

### Post by srs5694 on 2010-08-30
I'd like to also refer back to a previously-mentioned issue: If you follow my procedure and successfully install Ubuntu but still have problems, you may need to set the active/bootable flag on the GPT protective partition in the MBR. To do this:


[list=1]
[*]Boot an emergency disc, such as Parted Magic or System Rescue CD.
[*]Launch a shell.
[*]Type "fdisk /dev/sda".
[*]Type "p" to view the MBR partition table. It should show one partition, with "ee" in the "Id" column. This is normal, even though you created several GPT partitions.
[*]Type "a" and enter "1" (or whatever the partition number is) when prompted.
[*]Type "p" again. You should now see an "*" under the "Boot" column.
[*]Type "w" to save the changes.
[*]Remove the emergency CD and reboot. You should *not* need to re-install.
[/list]


These steps are only necessary with some buggy BIOSes. Some Intel BIOSes are known to be buggy and require this workaround.

---

### Post by tarahmarie on 2010-08-30
Here's where I'm at:

I'm in a LiveCD session at step 3.  You can't use aptitude to download and install gdisk, so I used this link:

[http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.6.10/gdisk_0.6.10-1_i386.deb/download](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.6.10/gdisk_0.6.10-1_i386.deb/download)

And grabbed gdisk.

Here's my output so far:

```

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo apt-get install gdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gdisk
ubuntu@ubuntu:~$ cd /home
ubuntu@ubuntu:/home$ ls
ubuntu
ubuntu@ubuntu:/home$ cd ..
ubuntu@ubuntu:/$ ls
bin   cdrom  etc   initrd.img  media  opt   rofs  sbin     srv  tmp  var
boot  dev    home  lib         mnt    proc  root  selinux  sys  usr  vmlinuz
ubuntu@ubuntu:/$ cd home/
ubuntu@ubuntu:/home$ ls
ubuntu
ubuntu@ubuntu:/home$ cd ubuntu/
ubuntu@ubuntu:~$ ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos
ubuntu@ubuntu:~$ cd Documents/
ubuntu@ubuntu:~/Documents$ ls
gdisk_0.6.10-1_i386.deb
ubuntu@ubuntu:~/Documents$ sudo dpkg -i gdisk_0.6.10-1_i386.deb 
Selecting previously deselected package gdisk.
(Reading database ... 74902 files and directories currently installed.)
Unpacking gdisk (from gdisk_0.6.10-1_i386.deb) ...
Setting up gdisk (0.6.10-1) ...
Processing triggers for man-db ...
ubuntu@ubuntu:~/Documents$ ^C
ubuntu@ubuntu:~/Documents$ 


```

I'm recording what's going on not only for posterity, but because I can access this thread no matter what system I'm on.

---

### Post by tarahmarie on 2010-08-30
And here's the output as I'm redoing the partitions in gdisk:

```

ubuntu@ubuntu:~/Documents$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 0.6.10

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): o
This option deletes all partitions and creates a new protective MBR.
Proceed? (Y/N): y

Command (? for help): n
Partition number (1-128, default 1): 1
First sector (34-3907029134, default = 34) or {+-}size{KMGT}: 2048
Last sector (2048-3907029134, default = 3907029134) or {+-}size{KMGT}: +1M
Current type is 'Linux/Windows data'
Hex code (L to show codes, 0 to enter raw code, Enter = 0700): EF02
Changed type of partition to 'BIOS boot partition'

Command (? for help): n
Partition number (2-128, default 2): 2
First sector (34-3907029134, default = 4096) or {+-}size{KMGT}:    
Last sector (4096-3907029134, default = 3907029134) or {+-}size{KMGT}: +20G
Current type is 'Linux/Windows data'
Hex code (L to show codes, 0 to enter raw code, Enter = 0700): 0700
Changed type of partition to 'Linux/Windows data'

Command (? for help): n
Partition number (3-128, default 3): 3
First sector (34-3907029134, default = 41947136) or {+-}size{KMGT}: 
Last sector (41947136-3907029134, default = 3907029134) or {+-}size{KMGT}: +8G
Current type is 'Linux/Windows data'
Hex code (L to show codes, 0 to enter raw code, Enter = 0700): 8200
Changed type of partition to 'Linux swap'

Command (? for help): n
Partition number (4-128, default 4): 4
First sector (34-3907029134, default = 58724352) or {+-}size{KMGT}: 
Last sector (58724352-3907029134, default = 3907029134) or {+-}size{KMGT}: +10G 
Current type is 'Linux/Windows data'
Hex code (L to show codes, 0 to enter raw code, Enter = 0700): 0700
Changed type of partition to 'Linux/Windows data'

Command (? for help): n
Partition number (5-128, default 5): 5
First sector (34-3907029134, default = 79695872) or {+-}size{KMGT}: 
Last sector (79695872-3907029134, default = 3907029134) or {+-}size{KMGT}: 
Current type is 'Linux/Windows data'
Hex code (L to show codes, 0 to enter raw code, Enter = 0700): 0700
Changed type of partition to 'Linux/Windows data'

Command (? for help): p
Disk /dev/sda: 3907029168 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 37136C9B-9A93-4983-A624-6A1EAF0819C0
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            4095   1024.0 KiB  EF02  BIOS boot partition
   2            4096        41947135   20.0 GiB    0700  Linux/Windows data
   3        41947136        58724351   8.0 GiB     8200  Linux swap
   4        58724352        79695871   10.0 GiB    0700  Linux/Windows data
   5        79695872      3907029134   1.8 TiB     0700  Linux/Windows data

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed, possibly destroying your data? (Y/N): y
OK; writing new GUID partition table (GPT).
Warning: The kernel is still using the old partition table.
The new table will be used at the next reboot.
The operation has completed successfully.
ubuntu@ubuntu:~/Documents$ 


```

---

### Post by srs5694 on 2010-08-31
Your gdisk "p" output looks reasonable, provided you have a reason for creating one more partition than I suggested. (I'm guessing /dev/sda5 will become /home and /dev/sda4 will be used for something else.)

---

### Post by tarahmarie on 2010-08-31
Thank you so much!

I did indeed have to reboot with the LiveCD to flag the boot partition, and I received warnings for doing so--but it booted fine.

I really appreciate it!

---

### Post by kjurkic on 2010-09-30
> **srs5694 said:**
> I'd like to also refer back to a previously-mentioned issue: If you follow my procedure and successfully install Ubuntu but still have problems, you may need to set the active/bootable flag on the GPT protective partition in the MBR. To do this:


[list=1]
[*]Boot an emergency disc, such as Parted Magic or System Rescue CD.
[*]Launch a shell.
[*]Type "fdisk /dev/sda".
[*]Type "p" to view the MBR partition table. It should show one partition, with "ee" in the "Id" column. This is normal, even though you created several GPT partitions.
[*]Type "a" and enter "1" (or whatever the partition number is) when prompted.
[*]Type "p" again. You should now see an "*" under the "Boot" column.
[*]Type "w" to save the changes.
[*]Remove the emergency CD and reboot. You should *not* need to re-install.
[/list]


These steps are only necessary with some buggy BIOSes. Some Intel BIOSes are known to be buggy and require this workaround.

Hi there

I am having this same problem (Intel MoBo, or should I say MoFo?) WD Green 2TB drive.

I printed & check listed every step you describe here, and I CANNOT get this POS booted up. I have googled for days, and re-installed at least 10 times, and cannot crack this puppy. I am using the latest SystemRescue CD to follow the steps.

In the above instructions at step 3, I assume that you mean gdisk /dev/sda, rather than fdisk? When I try fdisk, I get an error that fdisk doesn't support GPT.

Also, at step 5, where you state to enter 'a' - that is not an option in gdisk on SystemRescue. When I try GParted from GUI, I can flag sda1 as either bios-grub or boot, but not both.

Also, should I be starting the disk clean with MS-DOS, or GPT (create partition table advanced feature in GParted)

I am feeling very disappointed/frustrated that I should have to jump through hoops like this when Ubuntu is supposedly very current. 2TB drives are now selling under $120cdn, and will soon be given away as the prize in cereal boxes. I want to stick with Debian/Ubu, but this project isn't for the fun of it; I need this box for NAS very soon.

thanks
Ken

---

### Post by tarahmarie on 2010-09-30
> **kjurkic said:**
> Hi there

I am having this same problem (Intel MoBo, or should I say MoFo?) WD Green 2TB drive.

I printed & check listed every step you describe here, and I CANNOT get this POS booted up. I have googled for days, and re-installed at least 10 times, and cannot crack this puppy. I am using the latest SystemRescue CD to follow the steps.

In the above instructions at step 3, I assume that you mean gdisk /dev/sda, rather than fdisk? When I try fdisk, I get an error that fdisk doesn't support GPT.

Also, at step 5, where you state to enter 'a' - that is not an option in gdisk on SystemRescue. When I try GParted from GUI, I can flag sda1 as either bios-grub or boot, but not both.

Also, should I be starting the disk clean with MS-DOS, or GPT (create partition table advanced feature in GParted)

I am feeling very disappointed/frustrated that I should have to jump through hoops like this when Ubuntu is supposedly very current. 2TB drives are now selling under $120cdn, and will soon be given away as the prize in cereal boxes. I want to stick with Debian/Ubu, but this project isn't for the fun of it; I need this box for NAS very soon.

thanks
Ken

Hi, Ken!

Fortunately, I just posted a blog post with detailed instructions on how I did each of these things.  

[http://thecowgirlcoder.com/2010/09/28/triple-booting-linux-distros-with-a-mix-of-grub2-and-grub-legacy-part-2/](http://thecowgirlcoder.com/2010/09/28/triple-booting-linux-distros-with-a-mix-of-grub2-and-grub-legacy-part-2/)

Try there! Ask me questions in the comments, and I'll respond there so I can help everyone.

---

### Post by srs5694 on 2010-09-30
> **kjurkic said:**
> In the above instructions at step 3, I assume that you mean gdisk /dev/sda, rather than fdisk? When I try fdisk, I get an error that fdisk doesn't support GPT.

No, I really did mean fdisk. The other issues you report are a result of your using gdisk rather than fdisk. The root cause of the problem is that, for reasons unknown, Intel decided that its BIOS should check the MBR partition table for a bootable/active partition. If the disk is GPT and strictly follows the GPT spec, there will be no such partition, so the BIOS refuses to load the boot loader from the MBR. The workaround is to modify the MBR's partition table so that the only "partition" it contains (the GPT protective partition) is marked as bootable. The tool that's best suited to do this is fdisk.

Don't worry; fdisk won't trash the GPT data structures. You're just using it to modify the protective MBR, which it can safely do in this specific circumstance. (You don't want to make a habit of using fdisk on GPT disks, of course, but for *this specific* task, it'll do the job.)

---

### Post by kjurkic on 2010-09-30
> **srs5694 said:**
> No, I really did mean fdisk. The other issues you report are a result of your using gdisk rather than fdisk. The root cause of the problem is that, for reasons unknown, Intel decided that its BIOS should check the MBR partition table for a bootable/active partition. If the disk is GPT and strictly follows the GPT spec, there will be no such partition, so the BIOS refuses to load the boot loader from the MBR. The workaround is to modify the MBR's partition table so that the only "partition" it contains (the GPT protective partition) is marked as bootable. The tool that's best suited to do this is fdisk.

Don't worry; fdisk won't trash the GPT data structures. You're just using it to modify the protective MBR, which it can safely do in this specific circumstance. (You don't want to make a habit of using fdisk on GPT disks, of course, but for *this specific* task, it'll do the job.)

Ok, so I am back to sq01...but I still have the issue with fdisk not wanting to play with GPT (at least the fdisk packaged with SystemRescue)

So I will wipe the device & create a GPT config. When I check it with gdisk, it should show:
Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Then I can create the partitions. Then I can install Lucid - there should be no formatting or mounting for sda1, and it should only be the 1MB in size, correct?

 / = dev/sda2. format ext4
swap = /dev/sda3
whatevermountpoint = /dev/sda4, format ext4

After that if I understand the earlier instructions, I SHOULD NOT have to specify a location for /boot?

If I examine the partitions in gparted, should /dev/sda1 be flagged bios_grub or boot?

Thanks for the help; I am getting pretty burned out on this project.

regards
Ken

---

### Post by tarahmarie on 2010-09-30
> **kjurkic said:**
> Ok, so I am back to sq01...but I still have the issue with fdisk not wanting to play with GPT (at least the fdisk packaged with SystemRescue)

So I will wipe the device & create a GPT config. When I check it with gdisk, it should show:
Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Then I can create the partitions. Then I can install Lucid - there should be no formatting or mounting for sda1, and it should only be the 1MB in size, correct?

 / = dev/sda2. format ext4
swap = /dev/sda3
whatevermountpoint = /dev/sda4, format ext4

After that if I understand the earlier instructions, I SHOULD NOT have to specify a location for /boot?

If I examine the partitions in gparted, should /dev/sda1 be flagged bios_grub or boot?

Thanks for the help; I am getting pretty burned out on this project.

regards
Ken

If you're installing Lucid, why not try it as a live disk first instead of using SystemRescue? I know for a fact that the fdisk packaged with Lucid works perfectly as srs described.

---

### Post by srs5694 on 2010-09-30
> **kjurkic said:**
> Ok, so I am back to sq01...but I still have the issue with fdisk not wanting to play with GPT (at least the fdisk packaged with SystemRescue)

No, *use fdisk.* The warning it displays is a warning, not a terminal error. It *will* work. (That is, fdisk will work; I can't promise with 100% certainty that adding the active/boot flag to the 0xEE partition will let the computer boot, although I strongly suspect it will.)

---

### Post by tarahmarie on 2010-09-30
> **srs5694 said:**
> No, *use fdisk.* The warning it displays is a warning, not a terminal error. It *will* work. (That is, fdisk will work; I can't promise with 100% certainty that adding the active/boot flag to the 0xEE partition will let the computer boot, although I strongly suspect it will.)

Your instructions worked perfectly for me. 

Ken, you have to ignore the warning messages fdisk gives you and simply follow the instructions. It works, swear.

---

### Post by kjurkic on 2010-10-04
Hi SRS & tarahmarie,

I used the lucid CD, booted live, wiped the disk & started fresh with all the steps listed for gdisk, did the install, then fdisk, saw & ignored the error message, and still no joy in booting.

I am going to try swapping the M/B with an AOpen (UGH) board I have here, to see if this is an Intel BIOS issue, or drive issue. Will update when done. 

thanks for the help

regards
Ken

---

### Post by tarahmarie on 2010-10-04
> **kjurkic said:**
> Hi SRS & tarahmarie,

I used the lucid CD, booted live, wiped the disk & started fresh with all the steps listed for gdisk, did the install, then fdisk, saw & ignored the error message, and still no joy in booting.

I am going to try swapping the M/B with an AOpen (UGH) board I have here, to see if this is an Intel BIOS issue, or drive issue. Will update when done. 

thanks for the help

regards
Ken

The thing that fixed it for me was ensuring that the boot partition was flagged. Did you check for the asterix?

---

### Post by kjurkic on 2010-10-04
Hi again

Yes Tarah, I did confirm the boot flag.

Took drive & installed on ASUS m/b in another case; Lucid booted fine - no CD needed. The PITA here is that the Intel board has 4SATA ports (I have 4x2TB drives), but the ASUS has only 2 sata....

So this whole event is the result of the Intel BIOS not playing nice:mad:

Rather than beat my head anymore against a brick wall, I will just add a PCI sata card I have kicking around so I can use all 4 disks.

Thanks for all the help here though - I didn't find any other sites that has such excellent detail regarding the Intel issue. A few other postings on the forums refer folks to more info about GPT, partitions, and disk geometry; I just needed to get this working without going back to school for a semester:)

regards
Ken

---

### Post by tarahmarie on 2010-10-04
I am a little frustrated too.  Can you give me your bios version? When I get home in a bit, I will reboot and find out if it is the same as yours.

---

### Post by kjurkic on 2010-10-04
> **tarahmarie said:**
> I am a little frustrated too.  Can you give me your bios version? When I get home in a bit, I will reboot and find out if it is the same as yours.

Hi Tarah

BIOS version TS94610J.86A.0077.2007.0403.1030
Intel 946GZIS desktop m/b p4 3.0Ghz Intel, 2GB RAM

You can see detailed specs here:
[http://reviews.cnet.com/motherboards/intel-desktop-board-d946gzis/4507-3049_7-31985879.html](http://reviews.cnet.com/motherboards/intel-desktop-board-d946gzis/4507-3049_7-31985879.html)

Hope that is helpful

Ken

---

### Post by srs5694 on 2010-10-04
It's possible you're running into another of the issues noted on [my Web page on the topic.](http://nessus.rodsbooks.com/gdisk/bios.html) If you used gdisk for the initial setup, my first suspicion at this point would be that you need to use the 'h' option on the gdisk experts' menu, or the equivalent of typing "sudo sgdisk -C /dev/sda" with a recent version of the program. My Web page details several other suggestions, but most of those are speculative; the three issues I've encountered personally or seen described in enough detail to be confident of are the active flag on the MBR partition, the CHS issue solved by 'h' on the experts' menu, and BIOSes so buggy they require updating.

If you get this working in some way not documented on my Web page (besides swapping the motherboard, as you've done), I'd like to hear the details so I can add information on your solution to that page.

---

### Post by kjurkic on 2010-10-05
To quote Charlie Brown
***[SIZE="3"]AAAAAAAAAAAAAAUUUUUUUUUUUUUUUUUUUUUUUUUUUGGGGGHHH!!!!!!![/SIZE]***

Decided to try a fresh install, as I was having a graphic driver problem after moving the drive onto the Asus m/b. Following the recipe again & used only Lucid CD.

Used gdisk from universe repos. 

partitioned, installed, and amended with fdisk. 

Now all I get at reboot is:

Error: no such partition.
grub rescue>

:confused::confused::confused::(:(:(
-ken

---

### Post by srs5694 on 2010-10-05
If you want to debug it, you should post the output of the [Boot Info Script,](https://sourceforge.net/projects/bootinfoscript/) along with the output of "sudo gdisk -l /dev/sda". Please post both between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

Alternatively, you could use the "z" option on gdisk's experts' menu to destroy the GPT and MBR data structures and start over again with an MBR partitioning scheme rather than GPT. Although GPT will soon be necessary for many disks, MBR is still (barely) adequate for a 2TB drive, and since your BIOS is so flaky with GPT, it might be simpler to just skip it for the time being.

---

### Post by kjurkic on 2010-10-26
Just for the sake of closure.

I ended up using a 1TB boot disk, and 3x2TB for the rest, so I still have almost 7TB of storage capacity. This is the backup server for a small LAN, and this is JBOD, not RAID of any sort.

I have neither the time nor inclination to go deep on this (I calculate that I burned over 30hrs getting nowhere), and I would guess that by the next release, or at worst the next LTS release, they will have addressed this problem.

Thank you both for the help; always appreciated

best regards
Ken

---

### Post by argibbs on 2010-11-12
> **srs5694 said:**
> I'd like to also refer back to a previously-mentioned issue: If you follow my procedure and successfully install Ubuntu but still have problems, you may need to set the active/bootable flag on the GPT protective partition in the MBR. To do this:


[list=1]
[*]Boot an emergency disc, such as Parted Magic or System Rescue CD.
[*]Launch a shell.
[*]Type "fdisk /dev/sda".
[*]Type "p" to view the MBR partition table. It should show one partition, with "ee" in the "Id" column. This is normal, even though you created several GPT partitions.
[*]Type "a" and enter "1" (or whatever the partition number is) when prompted.
[*]Type "p" again. You should now see an "*" under the "Boot" column.
[*]Type "w" to save the changes.
[*]Remove the emergency CD and reboot. You should *not* need to re-install.
[/list]


These steps are only necessary with some buggy BIOSes. Some Intel BIOSes are known to be buggy and require this workaround.

Was trying to install Ubuntu 10.10 (Maverick) on a Intel D510MO motherboard and a large 2 TB HDD. The Ubuntu installer was correctly partitioning the disk using GPT, but the machine would refuse to boot with a message like "Boot error - no boot disk found".

Because I wasn't trying to install multiple distros, I didn't need to mess around with partitions as discussed earlier in this thread; I just booted into the Ubuntu installer from a USB stick, and installed to the HDD telling it to "Use the entire disk". Then after install completed, I rebooted back into the ubuntu installer, went to 'Try Ubuntu', pulled up a terminal and carried out the commands above. Then rebooted again, pulled the USB stick and the machine booted off the hard drive first time. Job done. Thank you for the neat trick - finding your post was a needle in the internet haystack but it worked like a charm.

Bit shonky that the Intel BIOS doesn't adhere to the GPT spec, but nice that the fix was possible. Thanks!

---

### Post by witnessmenow on 2010-12-27
I just want to say thanks very much to srs5694. I followed the first instructions and it didnt work, but the second set worked a charm.

Like the above poster I have a D510MO and i could not get it too boot :P

---

### Post by vladstudio on 2011-02-05
> **srs5694 said:**
> [list=1]
[*]Boot an emergency disc, such as Parted Magic or System Rescue CD.
[*]Launch a shell.
[*]Type "fdisk /dev/sda".
[*]Type "p" to view the MBR partition table. It should show one partition, with "ee" in the "Id" column. This is normal, even though you created several GPT partitions.
[*]Type "a" and enter "1" (or whatever the partition number is) when prompted.
[*]Type "p" again. You should now see an "*" under the "Boot" column.
[*]Type "w" to save the changes.
[*]Remove the emergency CD and reboot. You should *not* need to re-install.
[/list]

srs5694 - you saved my day! I mean literally, I spent a whole day trying to figure out why Ubuntu won't boot. Thank you, from Russia with love! 
For anyone with same problems - Intel D510MO motherboard, Seagate 2TB hard drive. Tried Ubuntu 10.10, Ubuntu 10.4, desktop, server. Any version installed successfully, then a black screen with "no bootable device insert boot disk and press any key".
Problem solved by following srs5694's two posts.
Thank you thank you thank you!

---

### Post by srs5694 on 2011-02-05
I'm glad my advice is continuing to be useful!

FWIW, last night I did some experiments with an Intel motherboard and UEFI booting. This is an option with many Intel boards released in the last couple of years; check the "Boot" menu in the BIOS setup screen. The Ubuntu 11.04 alpha 2 release installs nicely on such boards in UEFI mode, which obviates the need to modify the MBR's EFI protective partition. I don't believe that Ubuntu 10.10 includes the necessary UEFI boot support, though. My suspicion is you could coax it into working by putting a suitable (U)EFI-enabled version of GRUB on a USB flash drive, but I've not tested that. You can tell whether you're booting the installer in BIOS or (U)EFI mode by the boot loader used by the install disc. The BIOS boot loader is flashier and has more options; the (U)EFI boot loader is GRUB 2.

If anybody cares to try a UEFI installation, be sure to either select the option to have the installer use the whole disk or do manual partitioning and set aside one FAT partition of 100 to 200 MiB as an "EFI boot partition". (The Ubuntu installer makes this partition only 20 or 30 MiB, IIRC, when it creates it automatically. This works, but Windows and Mac OS both create bigger partitions, so my inclination is to make it bigger in case that extra space becomes necessary in the future.)

---

### Post by Yahoé on 2012-05-03
Even though this is solved, I used it to guide myself with installing 12.04 on a gpt disk with a regular non UEFI bios.

500 GB HD, USB official Precise amd64 release:

*Try Ubuntu
*Using Gparted
*Create new gpt partition table
*Create new partition 1MB no file format, set flag to bios_grub
*Create new partition at the end of the drive 4 GB linux-swap
*Create new partition 350 MB ext2, set flag to boot
*Create new partition 10 GB ext4
*Create new partition with the rest of the disk ext4
*Launch Ubuntu installer
*Manual partitioning. First 1 MB partition is ignored, 2nd 350 MB is /boot, 3rd 10 GB is /, 4th is /home
*Went on with installation
*Completed successfully

Computer is running like a charm!

---

### Post by oldos2er on 2012-05-03
Old thread closed.

---

