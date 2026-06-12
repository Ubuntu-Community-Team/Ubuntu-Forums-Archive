---
title: "FS issues"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tychobrailleur on 2010-04-16
Hi All, 

Here is a follow-up to [this]("http://ubuntuforums.org/showthread.php?t=1410189") post (thanks to [[COLOR=#d40000]**overdrank**[/COLOR]]("http://ubuntuforums.org/member.php?u=234741") for moving it to the right place, btw).

I am having serious problems with Lucid, running on Dell Studio 17 (64 bits).  Regularly, the filesystem becomes read-only, and restarting, the machine goes completely loolah (either it doesn't go past fsck, or just freezes, or other unexpected error, the latest being the new ubuntu splash being in complete textmode).  I then have to recover the system with a live cd, run fsck, and an awfully long list of erors gets fixed.  I can then restart ok (until a certain point when the system is absolutely banjaxed, and I have to *reinstall*) -- sometimes.  I can't really spot any obvious pattern, I'm afraid.

I am absolutely certain I have shut down the system « cleanly », so I cannot explain this.  I was suspecting a hw failure, but I happen to have 2 HDs in my laptop, and installing Lucid on the second drive brought the same disastrous conclusion.

I have been a Ubuntu user for years, and to be honest, this is getting me kind of depressed to get errors after errors when booting my system, when my other machines running on older versions are behaving just fine... :(

So, in a nutshell, my questions are:
- Am i doing something wrong (i.e. am I really an idiot)?
- If not, is anybody out there having the same troubles?
- What to do when this sort of troubles come up to (a) recover cleanly the system, and (b) maybe provide a proper feedback to the Ubuntu people
- Has anybody any inkling as to what the problem is, or how to go diagnosing it? 

Thanks,
Seb
p.s. I am starting to think I've been a complete nutter to install a not-yet-released version of Ubuntu on my brand new system...

---

### Post by tychobrailleur on 2010-04-26
Hi,

Here is an update on this.
I still experience issues, even with 10.04 RC.  Still the same symptoms: the filesystem becomes suddenly read-only, and I have to restart and use a Live CD for a fsck to fix the fs errors (if there is a better way of doing this, btw, I'm all ears!!).

The only “relevant” errors (as in, occurring roughly around the time I encounter problems) I can find in the logs is the following:

```

Apr 26 19:51:44 greystones kernel: [ 7174.099291] ata1: exception Emask 0x10 SAct 0x0 SErr 0x50000 action 0x1e frozen
Apr 26 19:51:44 greystones kernel: [ 7174.099300] ata1: irq_stat 0x00400001, PHY RDY changed
Apr 26 19:51:44 greystones kernel: [ 7174.099308] ata1: SError: { PHYRdyChg CommWake }
Apr 26 19:51:44 greystones kernel: [ 7174.099320] ata1: hard resetting link
Apr 26 19:51:45 greystones kernel: [ 7175.020070] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr 26 19:51:45 greystones kernel: [ 7175.235352] ata1.00: configured for UDMA/133
Apr 26 19:51:45 greystones kernel: [ 7175.250112] ata1: EH complete

```These errors codes are documented in the [libata error messages list]("https://ata.wiki.kernel.org/index.php/Libata_error_messages"), but I can't say it's helping me much :)

The only pattern of note is that I have the feeling this is likely to occur after moving around the laptop (and unplugging it).  Could be a total red herring, though, for all I know.

I have done a fair amount of reading on ext4, but I must admit I'm still way out of my league...  Anyway, here are some more details, in case someone out there wants to have a look:

```

sebastien@greystones:~$ export LANG=C
sebastien@greystones:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00077520

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       28931   232284833+   7  HPFS/NTFS
/dev/sda3           28932       60801   255995775   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4c4ce6bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30434   244461073+   7  HPFS/NTFS
/dev/sdb2           30435       60801   243922927+   5  Extended
/dev/sdb5           30435       59565   233994726   83  Linux
/dev/sdb6           59566       60801     9928138+  82  Linux swap / Solaris
sebastien@greystones:~$ cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=b64aaf16-28b2-46d7-b11a-9d3cceaf0673 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=d9a4a2aa-9a82-41cb-97e7-7dffd4654152 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=13a05033-7dce-46c4-84fc-9582b89eaaf7   /home    ext4          nodev,nosuid       0       2 

```sdb5 is where the system is installed, and my /home directory is in sda3. SMART is happy enough with the state of the drives.

Thanks,
Seb

---

