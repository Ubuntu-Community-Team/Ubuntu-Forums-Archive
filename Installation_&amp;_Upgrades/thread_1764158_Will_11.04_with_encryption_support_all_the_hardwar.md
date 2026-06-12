---
title: "Will 11.04 with encryption support all the hardware on my new ThinkPad?"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by ester4 on 2011-05-21
I recently ordered a Lenovo Thinkpad laptop. It's going to have UEFI, Intel SSD, Intel WiFi, and Sandy Bridge processor. It will also have a GOBI 3G broadband card for mobile broadband access.

I'm trying to decide whether I should use Windows 7 or Ubuntu 11.04. The only reason I will use Windows 7 is if all the hardware on the ThinkPad is not supported by ubuntu. I need to encrypt the whole computer also. So I would use the ubuntu Alternate CD to install the LUKS/LVM option.

Has anyone successfully done this on a Thinkpad? Should I anticipate problems due to UEFI, SSD, Gobi, Sandy Bridge? Or is all this hardware supported with full encryption on 11.04?

Thanks guys

---

### Post by ester4 on 2011-05-23
bump

---

### Post by ubujames on 2011-06-14
The only way your going to know is to try it, get yourself a copy of the ubuntu desktop live cd, and boot up using that.

Check to make sure the Video and WIFI work properly, from my experience, if those two work correctly, most everything else will also.

You may also want to check to see if your web cam works too.

Me personally, unless its a major component, like the touch-screen keyboard on the new Iconia Laptop, then I dont mind waiting, but in the case of the Iconia, I opted to not get the laptop, rather than give up Ubuntu.

Goodluck.

---

### Post by Paradoxfox93 on 2011-07-19
To Properly align the SSD you'll have to boot live, partition with Gparted.  Create msdos table.  Create ext2 100mb (or 256mb if you plan to dual boot anything) with 1mb preceding.  Shutdown, boot alternate CD.

Mark the boot partition you created to be formatted ext2, mounted at /boot.

Partition the remaining disk space and mark to use with encryption.  Configure encryption.  Mark the new encrypted volume for LVM unless you're not planning on splitting it up.

IF you do go LVM for partitioning then create a group, include the partition.  Create new volumes inside the group, format, label, and mount them as you see fit.

Install, apply further SSD tweaks to fstab, rc.local and so on.  Works just fine and I well above rated performance on my intel SSD

---

### Post by srs5694 on 2011-07-19
Ubuntu's UEFI support is still flaky, but it can be made to work. The problems mostly relate to the installation trashing a vital partition (the EFI System Partition; back it up before installing Ubuntu!) and sometimes to boot loader configuration and occasionally hangs when shutting down or rebooting. Once Linux is running there shouldn't be other problems.

Note that Windows ties its partition table format to its firmware type -- BIOS to MBR and UEFI to GPT. Linux is much more flexible than this, but if you anticipate dual-booting Windows, you should be very careful about setting the correct partition table type. *Do not* select MBR ("MSDOS") partitions if you use UEFI; but *do* select this type of partition if you use BIOS-style booting.

Most UEFI implementations support a legacy BIOS boot feature that enables the computer to run UEFI-unfriendly OSes. This feature is not always clearly marked in the firmware configuration tool, so setting it (or forcing it off) can be tricky. Given the current state of Ubuntu's UEFI support, the simplest course of action today is probably to use BIOS compatibility, at least for Linux. If you use BIOS boot mode for Windows, that means you'll be locked in to MBR partitioning, which is OK unless you've got a disk that's over 2 TiB in size. Going with UEFI booting, OTOH, will provide greater flexibility in the long run. GPT is required on hard disks over 2 TiB, so if you expect to upgrade to such a hard disk, UEFI may be beneficial at some point, and switching Windows' booting style, although possible, is a bit risky. (Note that Windows can use GPT on non-boot disks even on BIOS-based systems; it's only the boot disk's partition table type that's tied to the firmware.)

---

### Post by Paradoxfox93 on 2011-07-19
Also: [http://ubuntuforums.org/showthread.php?t=1480418&page=2](http://ubuntuforums.org/showthread.php?t=1480418&page=2)

I wrote more about dealing with intel SSD's and setting up encryption in 11.04 and partitioning space. DZ* Provides a a must read link as well.

Also, I don't think he's going to put over 2TB's on a single drive in that laptop.  If so, I'm sure raid can be configured and I know LVM can.

Also Intel is reputed for it's history of linux compatibility and support.  Wifi should be good.  At a glance [Gobi]("https://www.codeaurora.org/contribute/projects/gobi/") looks well supported too.

Also, if you have USB3 consider setting up multiboot USB3 Flash drive for ultra rapid install since you'll have to use both live and alt cd's.

---

### Post by ester4 on 2011-07-19
So I can't just install Ubuntu with the alternate CD? I have to first use the LIVE CD and then switch to the alternate CD? This has to be done specifically with my laptop why? I thought the alternate CD was all I needed to install encrypted LVM?

---

### Post by Paradoxfox93 on 2011-07-19
Specifically you need to used parted to align partitions.

---

### Post by ester4 on 2011-07-19
> **Paradoxfox93 said:**
> Specifically you need to used parted to align partitions.

I thought I could do this from the alternate CD. The alternate CD does not have Gparted?

---

### Post by Paradoxfox93 on 2011-07-19
The alternate cd will not align created partitions as far as I can tell.

---

### Post by ester4 on 2011-07-19
Will I be able to do everything from the LIVE CD with Oneiric? It appears encryption is in development: [http://brainstorm.ubuntu.com/idea/24712/](http://brainstorm.ubuntu.com/idea/24712/)

I'm assuming then I can align the partitions and then encrypt all from the LIVE CD? Does it look this way to you too?

---

### Post by Paradoxfox93 on 2011-07-19
Not likely.  I'd rather see more funtionality and flexability in the alternate CD than migration.

Come to think of it you'll have to reboot back into the liveCD again before you can log in your new setup to configure fstab, rc.local, and tune2fs to turn on writeback cache and disable journaling as well as any other tweaks.  I'm working on compiling a tutorial for SSD FDE  w/ tweaks.

---

### Post by ester4 on 2011-07-20
So all of these headaches are due to the fact I have an SSD? I wouldn't have to do all this stuff if I was using a HDD?

I always assumed I would just be able to use the selection for Guided Setup for encrypted LVM off the alternate CD and I'm all done.

---

### Post by Paradoxfox93 on 2011-07-22
If you didn't expect this migrating to SSD then its fair of me to assume you haven't googled a thing prior to posting. Shame.  Still, it's not that much of a headache.  Took me a couple days of googling to thresh out what advice and tweaks were important, which were dated, and which were unique/excepting to having a Intel so on the bright side you're way ahead of the game because I can assure you it's really not difficult and you'd have to do this configuration with or without encryption.  Setting up encryption is still very easy with the alternate CD.  This is a rough howto feel free to ask questions.

You can, alternatively just encrypt your home folder which is supported on the liveCD installation since lucid.  You will receive performance benefits from doing it this way vs. AES-256 PGP FDE as it causes my reads to suffer (roughly ~50Mb/s vs. 280MB/s) but that might not be true for oyu if you have a more powerful processor which I believe is my bottleneck.


Anyway.  SSD's are pretty much a pain.  A lot less now than they use to be but you're talking about half a dozen or so things you'll have to do to properly configure your system to use an SSD.  Specifically:

1. noatime,discard,data=writeback to mount options on your ext4 fs

2  disable journaling and enable writeback cache.

3  Change IO Scheduler to noop

4. Establish /tmp as a ramfs drive and put firefox cache into it.

First, you can enter alternate cd, exit setup, use parted to establish your partitions but I can't give you instruction for that.  I recommend booting live cd/usb iso and skipping the install, run gparted,  create /boot with 100mb and 1mb preceding.  11.04 should automatically detect an intel SSD and align to MiB instead of cylinders.  Make gpt partition table.  create boot,  create the other partition as %80 of drive since you are intel.

Important:  Other manufacturers force limited user access for wear level reservation and are safe to partition entirely but Intel does not do this.  In other words, leave %20 of your hard disks space unallocated   anywhere on the drive.  I don't know why they do this but it is the better configuration because of the quality controller from intel being able to use ANY free space as wear level reserve this means you can stick a hidden partition with truecrypt in the middle of the empty space later.  You can't do this with any other manufacturer.


Boot alternate, at manual partitioning, select and configure the 100mb to /boot as ext2 (Will not be written enough to need trim support in ext4).  Then mark the large volume to be used as physical volume for encryption.  Configure encryption.  Mark new volume to be used as volume for LVM.  Configure LVM.  Create group, add and name volume.  partition the LVM volume create as you would.

Mark all ext* formated partitions inside and outside encryption with noatime (under mount options when setting up the partition).  Be sure to mark /boot as bootable and install grub to the MBR.

I personally recommend not creating a swap if you have 4Gb or more of ram.  In fact, I just make this one large root partition and don't bother with home or anything else but I dd'd it once I got it where I wanted it and don't keep anything on this computer i don't back up somewhere.  However through LVM you can create as many partitions inside your single encrypted volume  for your setup as desired.

When done reboot into the live cd.
```

sudo apt-get install lvm2
sudo modprobe dm-mod
sudo cryptsetup luksOpen /dev/sd** name
sudo vgscan
sudo vgchange -a y VOLUME
sudo lvscan

```

sd** being your encrypted partition.  enter your password.

This will download and install LVM, unlock your encrypted hard drive and tell LVM to recognize your partitions.  Now before your mount it/them you have to make some tweaks to the fs (enable writeback cache and disable journaling).
```

sudo tune2fs -o journal_data_writeback /dev/GROUP/VOLUME
sudo tune2fs -O ^has_journal /dev/GROUP/VOLUME
sudo e2fsck -f /dev/GROUP/VOLUME

```
Repeat for every partition you set up inside LVM.  "GROUP" and "VOLUME" are whatever you named them during the alt cd install setup of LVM.


Now,
```
 sudo mkdir /media/root
sudo mount /dev/GROUP/ROOTVOLUME /media/root
gksudo gedit /media/root/etc/fstab
```
"ROOTVOLUME" being whatever you named the volume containing the root partition of your installation.
Add
```

tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

```
**Also make sure every ext4 fs has options  noatime,discard,data=writeback**

save it and open /etc/rc.local with gksudo permissions like you did fstab.
```

gksudo gedit /media/root/etc/rc.local
```

add 
```

echo noop /sys/block/sda/queue/scheduler

```
before exit 0

save it & reboot as normal into your new system to finish installation (updates, prop drivers, personal software, etc.)

After you log in, start firefox.  navigate to about:config.  right click->new->string->enter:
```
browser.cache.disk.parent_directory
```
String:
```
/tmp
```

It's actually pretty easy, but I've done it almost six times attempting other options an configurations.  I experiences roughly 1/4 performance under encryption but you have one of those new intel chip with encryption support you might not.  Or a generally more powerful proc.  Mine is only 1.6ghz dual core APU.

Even if you don't use encryption you must still apply those tweaks to your filesystem, fstab and rc.local


discard is TRIM support

noatime stops filesystem logging of read times

noop is a direct to drive data calling scheduler, it's as close as you can get to not choosing a scheduler in that it doesn't prioritize calls at all.  This is why you put it in your rc.local instead of grub as some suggest.  You still need cfq for other drives like usb or whatever and most places to recommend deadline.  Intel has a quality controller and it's safe to use noop and rely on it but if you want rc.local is where you change it.  There are options for deadline you'll have to configure as well.  Anyone using an SSD of a different manufacturer should choose deadline.  

Gparted for 1mb preceding.  This is done to assure alignment of the file system to the physical block.  Misalignment will cause two blocks instead fo one to be called/written at once reducing the effective speed in half if not less.  

Good luck, enjoy.  I promise, it's worth it.  SSD's are awesome. Doing these things will preserve the life of your drive.  Properly configured and used, an SSD manufactured today could outlast HDD's built today.

---

