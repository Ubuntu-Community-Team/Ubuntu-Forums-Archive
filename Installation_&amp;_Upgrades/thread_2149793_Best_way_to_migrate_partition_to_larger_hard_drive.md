---
title: "Best way to migrate partition to larger hard drive?"
date: 2013-05-29
forum: Installation &amp; Upgrades
---

### Post by gamblor01 on 2013-05-29
I have a drive that appears to be failing on me.  Sometimes when I boot up my machine I get some rather strange messages, looks like inode addresses or something, and the system never quite finishes booting up.  So far I have been able to simply reboot and then it works, but I went ahead and bought a new HDD on Amazon ($65 US for a 1TB drive!).

The current drive is 500GB.  I have several partitions on it (used to play around with installing lots of flavors of Linux and triple/quad booting my machine).  What I would like to do is to install a single partition on my new drive (or maybe a 750GB partition with a 250GB playground?), and then clone my existing data to it.  Currently my "main" partition is a 275GB partition on /dev/sdb5:

```

Disk /dev/sdb: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ebf86

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   390829319   195414628+  83  Linux
/dev/sdb2       390829320   392789249      979965   82  Linux swap / Solaris
/dev/sdb3       392790014   976769023   291989505    5  Extended
/dev/sdb5       392790016   976769023   291989504   83  Linux

```


Let's just say I put the new drive in and create a single 1TB partition on it (let's call it /dev/sdc1 for now).  Can I then use dd to clone the old partition to the new one directly?  Something like:

```

dd if=/dev/sdb5 of=/dev/sdc1 bs=32256

```


Most tutorials I see out there copy the entire drive, not just a partition:


```

dd if=/dev/sdb of=/dev/sdc bs=32256

```


Can I copy a partition to a partition if they aren't the exact same size?  If not, what's the best way to migrate?  I guess I could clone sdb to sdc, and then use a gparted live CD to remove all partitions except the one I want, and resize it to use the entire disk?

---

### Post by ahallubuntu on 2013-05-30
~

---

### Post by gamblor01 on 2013-05-30
Thanks I'll give that a shot.  I already burned the gparted live CD so I'll try it out.  Stuff keeps getting easier and easier...  :)

---

### Post by Mark Phelps on 2013-05-30
You can also use Clonezilla -- as it has a clone "disk" feature -- which will migrate ALL the partitions to another drive.

---

### Post by gamblor01 on 2013-05-31
> **Mark Phelps said:**
> You can also use Clonezilla -- as it has a clone "disk" feature -- which will migrate ALL the partitions to another drive.

Thanks -- I actually didn't want to do that.  I have several partitions on the old drive but they aren't really necessary any longer.  One was Fedora, another was Ubuntu 12.04 32-bit (since that was the initial platform targeted for the Steam Linux beta...though it turned out not to be necessary), etc.  My goal was to just get one parititon but clone the existing one I wanted (/dev/sdb5).

Anyway, I fired up gparted and created /dev/sdb1 as a 750GB partition.  I then put a small space for swap on /dev/sdb2 and left the rest unpartitioned for now.  Then I did the copy/paste action, and ran through the chroot command to update grub.

It cloned the partition and now I have tons of free space.  Hooray!

```

bdmayes@ubuntubox:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       721G  213G  472G  32% /

```

I'm still missing something however.  grub is definitely installed, but my system doesn't seem to boot it.  Oddly enough, if I put the gparted CD back in and select the "boot local OS" option, then it seems to properly chainload (I guess?) my grub 2.0 and viola! I can boot up just fine.  In fact, I'm in 13.04 right now as I type this.

So here is the new (and current) parititon layout.  The drive is /dev/sdb because I have an old drive with XP installed on it at /dev/sda (which itself has been cloned/migrated at least once to a larger drive).  I don't really ever use it any longer, but every so often I *have* to boot into it to get something to work properly...or to play a game.  When I got my Steam beta invite I bought several games, even some that I knew weren't supported on Linux and probably never would be (like the Crysis pack).  One day I'll boot into XP and try them out.  One day.....


Anyway, here is the layout:


```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2b7a2b79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   781401599   390700768+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000c876d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1536002047   768000000   83  Linux
/dev/sdb2      1536002048  1544390655     4194304   82  Linux swap / Solaris

```


I have even tried reinstalling grub and updating it.  It clearly recognizes my partitions.  However, when I reboot it will POST and then after realizing there is no bootable CD/DVD it just hangs and never loads up grub.  I just ran these commands and rebooted but it still didn't help:

```

bdmayes@ubuntubox:~$ sudo grub-install --recheck /dev/sda
Installation finished. No error reported.
bdmayes@ubuntubox:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found initrd image: /boot/initrd.img-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found initrd image: /boot/initrd.img-3.8.0-21-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found linux image: /boot/vmlinuz-3.0.0-17-generic
Found initrd image: /boot/initrd.img-3.0.0-17-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done

```


I guess I can try installing boot-restore and using that but I'm not sure why the above commands aren't working.  Since grub was already installed I shouldn't even need to install it.  Just running update-grub should have been sufficient to properly redefine grub.cfg (which I just checked and it looks good -- the UUID matches perfectly).

grub is definitely installed in the MBR:

```

bdmayes@ubuntubox:~$ sudo file -s /dev/sda
/dev/sda: x86 boot sector; GRand Unified Bootloader, stage1 version 0x3, boot drive 0x80, stage2 address 0x2000, stage2 segment 0x200; partition 1: ID=0x7, active, starthead 1, startsector 63, 781401537 sectors, code offset 0x63

```


Any idea what I'm missing?  It is late so it's very possible I did something stupid and/or I'm forgetting something.  Thanks!

---

### Post by ahallubuntu on 2013-05-31
~

---

### Post by gamblor01 on 2013-05-31
> **ahallubuntu said:**
> I'm surprised you installed Grub on /dev/sda if you're Linux drive is /dev/sdb ?  You can do that, but then you  must have that other Windows drive installed to boot.    My preference would have been to leave /dev/sda with the Windows boot loader and /dev/sdb with Grub; set /dev/sdb as your first boot drive in BIOS and then Grub can choose either drive.

What's the contents of your /etc/fstab file?

Both drives should be installed/connected so it doesn't really matter where grub is installed.  If I decide to change something in the future I can always fire up a live CD and reinstall/update grub.

I'm not really sure why /etc/fstab matters at this point -- it's not even getting into grub so it shouldn't even care about /etc/fstab until the kernel is loaded.  I did update it to make sure that the UUID values were correct.  The swap partition was not so I had to correct it.  In any case:


```

bdmayes@ubuntubox:~$ sudo blkid
/dev/sda1: UUID="74DCF903DCF8C102" TYPE="ntfs" 
/dev/sdb1: UUID="d7e75a4b-7b71-47bc-a73a-4552a5dada86" TYPE="ext4" 
/dev/sdb2: UUID="9542b51f-171b-41e5-a4a3-c389ce0c25b6" TYPE="swap" 
/dev/sr0: LABEL="GParted-live" TYPE="iso9660" 
bdmayes@ubuntubox:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=d7e75a4b-7b71-47bc-a73a-4552a5dada86 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=9542b51f-171b-41e5-a4a3-c389ce0c25b6 none            swap    sw              0       0
# Windows XP
/dev/sda1               /media/sda1      ntfs rw,defaults,umask=0000 0 0

```

---

### Post by ahallubuntu on 2013-05-31
Please run down your exact procedure for re-installing Grub.  I'd still install it on /dev/sdb - that seems cleaner to me, plus I see no advantage of having it on /dev/sda .

---

### Post by gamblor01 on 2013-05-31
> **ahallubuntu said:**
> Please run down your exact procedure for re-installing Grub.  I'd still install it on /dev/sdb - that seems cleaner to me, plus I see no advantage of having it on /dev/sda .

See post #5:

[http://ubuntuforums.org/showthread.php?t=2149793&p=12671093#post12671093](http://ubuntuforums.org/showthread.php?t=2149793&p=12671093#post12671093)


After cloning the drive I just ran **sudo grub-install --recheck /dev/sda** (which I still argue wasn't really necessary since /dev/sda didn't change) and then followed it up with **sudo update-grub** to adjust boot.cfg.  That's it.

---

### Post by ahallubuntu on 2013-05-31
> **gamblor01 said:**
> See post #5:

[http://ubuntuforums.org/showthread.php?t=2149793&p=12671093#post12671093](http://ubuntuforums.org/showthread.php?t=2149793&p=12671093#post12671093)


After cloning the drive I just ran **sudo grub-install --recheck /dev/sda** (which I still argue wasn't really necessary since /dev/sda didn't change) and then followed it up with **sudo update-grub** to adjust boot.cfg.  That's it.

If you want to install Grub properly, use the chroot method I gave you in post #2 instead.

---

### Post by gamblor01 on 2013-05-31
I did that initially (from the gparted live CD).  It didn't work so I rebooted and tried to select the option to boot a local OS -- which worked.  While in my local OS I have tried to correct it several times without any luck.  So something is goofy with grub because the live CD can boot my local partitions just fine but the grub installed on disk cannot.  I'm just not sure what is missing from the configuration...

---

### Post by gamblor01 on 2013-05-31
Nevermind...solved it!  I started thinking about how it boots just fine with some other grub to chainload it, which led me to believe grub was fine and I needed to start looking around in BIOS.  For some reason, I guess the system scanned the drives at some point and decided to put sdb (my new 1TB drive) in the boot order prior to sda (the old 500GB drive with XP on it).  I just swapped the order and BOOM!  My system boots up perfectly now.  :)

Marking as solved.  Many thanks ahallubuntu.  And I guess I'll stop cloning drives manually from now on.  The output in gparted is much more informative (progress report and estimated time remaining).  Using dd gives absolutely no output until it is finished.  :/

---

