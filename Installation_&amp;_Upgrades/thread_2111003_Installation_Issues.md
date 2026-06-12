---
title: "Installation Issues"
date: 2013-01-31
forum: Installation &amp; Upgrades
---

### Post by Baudzilla on 2013-01-31
My computer uses a RAID 0 array of 2 160GB SATA drives.  Before trying to install Ubuntu, I had both Windows XP and Fedora 17 installed on my system.  I apologize in advance if I misuse any terminology, as I'm still fairly new to some of these things.

When installing Ubuntu, I tried selecting the partitions for it to use, however the installer always shows 2-3 duplicates of each partition for some reason.  So I instead chose the option to install over my existing OS, not noticing it said "all OSs".  Despite the fact that the button I selected for this action was "continue" and not "install now", Ubuntu started installing over my entire system.  Consequently, I now have to reinstall my everything.

Even though Ubuntu had free reign of my hard drive like this, it still couldn't install a bootloader correctly and generated an error, where I was given the option to choose another bootloader partition (none of which the installer would allow), continue without a bootloader, or stop the installation.  Consequently, I ended up with a system which was erased, and also not bootable.

So now I'm trying to pick up the pieces.  I used GParted to remove the existing partitions from the failed install, created an NTFS partition for Windows XP, and installed XP onto that partition.  Now I try to install Ubuntu and choose the option to install alongside other operating systems.  Ubuntu once again fails to install a bootloader (GRUB).

So then I use GParted to set up the partitions myself, adding a 512MB ext2 primary partition for a bootloader, and a 75GB extended partition containing a 70GB ext4 logical volume for Ubuntu and a 5GB linux-swap.

After that, I try install Ubuntu again and tell it to install to those partitions.  The install menu still displays many duplicates of each partition, even though both fdisk and gparted just list them once.  I select to format the ext4 partition and mount it as /, but I don't get those options for the swap.  As soon as the install begins, I get the error "The creation of swap space in partition #1 of Serial ATA RAID nvidia_cdjbbejb3 (partition #3) failed."

It seems to me that it shouldn't be trying to create swap space, as a space is already set up.  I'm really not sure what else to try now.  Anyone have ideas?

Edit: Installing with a Ubuntu desktop 12.10 live DVD.  GParted was also used from the live DVD.

---

### Post by Baudzilla on 2013-02-01
Okay, I've managed to get 12.10 installed and from what I've seen, it seems the reason for Ubuntu failing to install GRUB was that it would always try to write to my first hard drive, rather than to the device for the raid array.  This was not be affected by which device was selected for installing the bootloader to.  Instead, I had to manually use grub-install to set it up myself.

But now, the output I get from fdisk seems rather alarming.  SDA/SDB are my hard drives, /dev/mapper/nvidia_* are my raid array and its partitions.

```

root@A8N-E:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5e295e29

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005af8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   471375871   235686912    7  HPFS/NTFS/exFAT
/dev/sdb2       471375872   617163007    72893568   83  Linux
/dev/sdb3       617163008   625163519     4000256   82  Linux swap / Solaris

Disk /dev/mapper/nvidia_cdjbbejb: 320.1 GB, 320083722240 bytes
255 heads, 63 sectors/track, 38914 cylinders, total 625163520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x0005af8a

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_cdjbbejb1   *        2048   471375871   235686912    7  HPFS/NTFS/exFAT
/dev/mapper/nvidia_cdjbbejb2       471375872   617163007    72893568   83  Linux
/dev/mapper/nvidia_cdjbbejb3       617163008   625163519     4000256   82  Linux swap / Solaris

Disk /dev/mapper/nvidia_cdjbbejb1: 241.3 GB, 241343397888 bytes
255 heads, 63 sectors/track, 29341 cylinders, total 471373824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

                        Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_cdjbbejb1p1   ?   218129509  1920119918   850995205   72  Unknown
Partition 1 does not start on physical sector boundary.
/dev/mapper/nvidia_cdjbbejb1p2   ?   729050177  1273024900   271987362   74  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/nvidia_cdjbbejb1p3   ?   168653938   168653938           0   65  Novell Netware 386
Partition 3 does not start on physical sector boundary.
/dev/mapper/nvidia_cdjbbejb1p4      2692939776  2692991410       25817+   0  Empty

Partition table entries are not in disk order

Disk /dev/mapper/nvidia_cdjbbejb2: 74.6 GB, 74643013632 bytes
255 heads, 63 sectors/track, 9074 cylinders, total 145787136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/nvidia_cdjbbejb2 doesn't contain a valid partition table

Disk /dev/mapper/nvidia_cdjbbejb3: 4096 MB, 4096262144 bytes
255 heads, 63 sectors/track, 498 cylinders, total 8000512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x50e6b6ec

Disk /dev/mapper/nvidia_cdjbbejb3 doesn't contain a valid partition table

```I hardly know where to start with all that.  I've always been using GParted for changing my partitions, but it often produced errors, even if it got the job done.  I'm wondering if I need to get some professional software for fixing partitions, as GParted doesn't seem very compatible with my system if it does this.

---

### Post by ronparent on 2013-02-01
I can't tell from your narrative what you have left after trying your install.

Just to put things in perspective, you have what the Linux community calls a fakeRAID. It is a software raid setup thru the bios and tailored for use by Windows. It is perfectly usable by Ubuntu, if you know what you are doing.

First off, I personally have not been able to do a simple install of 12.10 to my raid. 12.10 does not directly support fakeRAID at this stage probably because of complications of trying to accommodate install environments of both UEFI  and legacy bios systems. That said it can be done but not easily if you don't know Linux. And as you have discovered it doesn't properly identify where to install the grub boot loader.

Secondly, gparted works well with caveots. It will show both the raid with its partitions as well as each of individual drives with unallocated space. If you partition the unallocated space on either of those drives you will destroy integrity of the raid and in the case of a raid 0 (stripe) totally render it unrecoverable.

I can't tell where you are. Try booting from the installation disk to a live cd session and open a terminal. Write the command > sudo blkid and post the results here.

---

### Post by Baudzilla on 2013-02-01
Thanks for the help!  I know it's a long read.

I quite sure I've never tried install any partitions to either of the individual drives, but I guess maybe a misguided installer could've.  Here's the output of that command, executed from my live cd.

```

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda: TYPE="nvidia_raid_member" 
/dev/sr0: LABEL="Ubuntu 12.10 i386" TYPE="iso9660" 
/dev/sdb: TYPE="nvidia_raid_member" 
/dev/mapper/nvidia_cdjbbejb1: UUID="CA9034FE9034F315" TYPE="ntfs" 
/dev/mapper/nvidia_cdjbbejb2: UUID="becb6d7f-bc2f-47f5-aaac-e9072a0062c3" TYPE="ext4" 
/dev/mapper/nvidia_cdjbbejb3: UUID="6bd30d2a-706b-4a09-858d-a01c3216aae0" TYPE="swap" 

```As shown above, I only have 3 primary partitions configured.

---

### Post by ronparent on 2013-02-01
So far, so good! Everything look intact.

Here is where it gets tacky. With my system, in my attempts to install 12.10, the install process died at a point that I didn't have an operable system. We can try that out by installing grub from the live cd. For your case, the grub installation may be basically a three step process.  

1. mount the new install - 
> sudo mount /dev/mapper/nvidia_cdjbbejb2 /mnt

2. We will first check that dmraid has been installed (needed to activate the raid)-
> sudo chroot apt-get install dmraid
If already installed, fine. Else it will be when the command is executed. 

3. Install the grub to your 12.10 partition and the boot loader to the raid - 
> sudo grub-install --root-directory=/mnt/ /dev/dm-0

Then try to boot to your Ubuntu install (Windows will also be in the boot menu). I would be amazed if this works. If it does you are home free. If not I will have to guide you through another approach. That would be to install to a non raid drive (another hard disk internal or external, usb memory key, etc.). Then copy all of the files from a working install to the raid. Let us know how it works out.

---

### Post by Baudzilla on 2013-02-01
Sorry if my previous posts were unclear, but I was already successful in installing GRUB manually.  I didn't use any commands to install dmraid, and the install command was like this:
> 
sudo grub-install --root-directory=/mnt/ /dev/mapper/nvidia_cdjbbejb
The result gave me a GRUB command line on boot.  So I used commands to locate and boot off my Linux partition.  From there, I used "update-grub" to write a menu for GRUB which worked great.

But I'm concerned about what fdisk tells me about my partitions.  Do you think it's nothing to worry about?  The output is in my second post.

---

