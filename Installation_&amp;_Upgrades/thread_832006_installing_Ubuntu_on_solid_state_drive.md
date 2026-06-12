---
title: "installing Ubuntu on solid state drive"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2008-06-17
Has anyone sucessfully installed Ubuntu on a machine that is using a solid state hard drive as the boot drive ?

If so, how was the boot time and overall performance compared to an installation of Ubuntu on a disc. type hard drive ?

Was the performance enhancement worth the extra investment in the solid state drive ?  Any downsides to this configuration ?

Thanks.

---

### Post by castoroil97 on 2008-12-22
I am curious too.  I am looking into getting one, cause at this point, the biggest speed bottleneck is drive access time.

---

### Post by wpshooter on 2008-12-22
> **castoroil97 said:**
> I am curious too.  I am looking into getting one, cause at this point, the biggest speed bottleneck is drive access time.

Boy, I glad someone other than just me finally had the *$%)@$* to say this !!!

Thanks.

---

### Post by yt_l9 on 2008-12-30
Has nobody done this or has nobody wanted to post results?  

I'm toying with trying this as my boot drive:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820609332](http://www.newegg.com/Product/Product.aspx?Item=N82E16820609332)
while keeping my 750GB as the media drive.

I'll post results here after if nobody else has, but it will be a few weeks.

:)

---

### Post by Swerve1000 on 2009-01-03
I'm interested to.

My research has shown me that some of the cheaper SSDs have very poor performance, in which regard I cannot remember though. The more expensive models though were operating much better.

---

### Post by hello_kitty on 2009-02-17
I just ordered a 128 GB G.Skill Titan SSD a few days ago, but unfortunately, have yet to receive it.  However, if any of you would be curious as to the reasoning behind my purchase, I'll include a link to one of the reviews that persuaded me: [http://www.legionhardware.com/document.php?id=804&p=0](http://www.legionhardware.com/document.php?id=804&p=0)

Once I receive my drive, I'll be sure to post my opinion of it.

---

### Post by 3rdalbum on 2009-02-17
I just bought the latest issue of Linux Format, where one of the columnists installs OpenSUSE on an SSD. He observes much faster speeds, but notes that the boot process has not been optimised for SSDs and by removing several "sync" calls during boot, he shaves a few seconds off the boot time.

If you've got the dough, it's worth buying an SSD.

I have installed Ubuntu on an SSD, but only the one that came in my Aspire One :-)

---

### Post by wpshooter on 2009-02-20
> **hello_kitty said:**
> I just ordered a 128 GB G.Skill Titan SSD a few days ago, but unfortunately, have yet to receive it.  However, if any of you would be curious as to the reasoning behind my purchase, I'll include a link to one of the reviews that persuaded me: [http://www.legionhardware.com/document.php?id=804&p=0](http://www.legionhardware.com/document.php?id=804&p=0)

Once I receive my drive, I'll be sure to post my opinion of it.

Hello_Kitty:

I am very interested in how this goes for you.

I am anxiously awaiting your assessment.

Good luck and thanks.

---

### Post by hello_kitty on 2009-02-21
> **wpshooter said:**
> Hello_Kitty:

I am very interested in how this goes for you.

I am anxiously awaiting your assessment.

Good luck and thanks.

Nice to know someone is!  ;)  I'll let you know as soon as the postal service delivers...

---

### Post by hello_kitty on 2009-02-22
> **wpshooter said:**
> Has anyone sucessfully installed Ubuntu on a machine that is using a solid state hard drive as the boot drive ?

If so, how was the boot time and overall performance compared to an installation of Ubuntu on a disc. type hard drive ?

Was the performance enhancement worth the extra investment in the solid state drive ?  Any downsides to this configuration ?

Thanks.

Alright, so I finally received my SSD in the mail today, and successfully installed Ubuntu 8.10 without too much difficulty.  I had an issue during initial installation where the installer would pause for a good deal of time (at 5%) when formatting the partition as ext3.  I am not entirely sure as to the cause of the error, but I was able to circumvent this, at least temporarily, by formatting as ext2.  From what I understand, ext2 is better than ext3 for SSDs anyway (right out of the box), due to its lack of journaling, and therefore considerably fewer disk writes.  This is *supposed* to improve the life expectancy of the drive.  However, should you desire the reliability of ext3, or ext4 for that matter, [here]("http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/") is a link to an informative site on how to decrease journal access times and various other tricks.

As far as performance goes, this baby blows my 5400 rpm drive out of the water!  Boot times are cut in half, applications open almost as fast as you can click them, and Ubuntu, quite simply, flies!  I haven't run any bechmarks, as I am not too concerned with artificially-derived performance ratings, but the real-world performance is through the roof.  This drive is by far the best upgrade I have made for any of my computers in a long time.  Unfortunately, due to "newness" of these drives, the price is still a little higher than I would have liked — especially considering the size — but as far as I am concerned, the investment was well worth it.  Give it another 6 months or so and the prices should drop considerably...

---

### Post by RHCEinUK on 2009-02-22
I have Linux running on SSD, and it screams. My concern is robustness of the drive. Anyone has experience with an SSD drive running in a laptop say more than 1 year?

---

### Post by kamolt on 2009-02-22
Recently I built a new pc with : Asus P6T deluxe V2, Corsair XMS3 3GB, I7-920, Noctua NH-U12P,MSI 9800GT Zilent, Intel X25-M SSD 80 Gb (system-drive), WD Caviar Black 1TB, Enermax Modu 82+, NZXT Roque.., Ubuntu 8.10. First I had some problems with an old DVD drive which refused to boot under 8.10 although it worked under 8.04. After installing a more recent DVD drive the installation worked perfectly. The Intel SSD seems to be pretty fast and I am very happy with it. Since I use Linux only I have no experience with XP or Vista.

---

### Post by daniel014 on 2009-02-22
Make sure to use a non journaling file system like EXT2, and don't use a swap partition as this can reduce SSD life.

---

### Post by kamolt on 2009-02-23
> **daniel014 said:**
> Make sure to use a non journaling file system like EXT2, and don't use a swap partition as this can reduce SSD life.
Thanks for the advice but I already installed the usual way with EXT3 and a SWAP partition. Should I reinstall ? It takes some time to reinstall all the programs and get everything right.
I am bit surprised though about the wearing because there are no moving parts and there is 5 year warranty. Five years is already a long life span for this kind of product which evolve rapidly. Finally isn't EXT3 faster an more reliable then EXT2 and what about EXT4 ?

---

### Post by IgnorantGuru on 2009-03-28
I just installed a new 30GB Vertex SSD (OCZSSD2-1VTX30G) (about $130) on my _[Asus P5QC]("http://wiki.ubuntu.com/Asus_P5QC")_ using kubuntu-8.04.2-alternate-amd64.  The Vertex is competition for Intel's line - one of the fastest.  I previously had a 300GB Velociraptor as my system drive, which I wanted to replace because both it and its RMA replacement emitted a *very* high-pitched whine.

I can tell you that even compared to a velociraptor which hdparm -t rated at 115MB/sec read, this drive ***screams***!  The system boots and runs so fast it actually took awhile getting used to (I'm used to minor delays in which to think of my next step).  hdparm -t reports "201.03 MB/sec"!  (Drive is speced at 200 read and 160 write.)  So it's reading about twice as fast as my velociraptor, plus with almost no seek time.  Even the monstrous OpenOffice loads in about one second.

The only real delay during boot now is when the conventional drives (both 7200rpm) are mounted and checked.  Other than that it practically just 'comes on'.  Using the system is a pleasure and I've had none of the stuttering reported with slower SSD drives (this drive has a 64MB cache which helps with that).  SSDs excel in 'seek time' compared to a conventional drive (no drive head to move), so I find it really makes a big difference in the overall system performance.

A few notes:
I skipped the expensive mounting hardware and used velcro to hold the drive (which is very light and cool) - works great.

The firmware of this drive is reported not to be fully AHCI compatible.  But I read reviews on OCZ's forum that indicated it worked okay, so I went with it.  Ubuntu will only work with my Asus P5QC in AHCI mode, so this was a must.  Also, the manufacturer is taking a very active role in developing the firmware, so I'm sure full AHCI support is coming.  Nevertheless, I've had no issues using the drive in AHCI mode (I didn't upgrade the firmware, but I can't tell you what the firmware of my drive is - where to look?)

Each cell in an SSD has a finite number of writes before it dies.  I think with the modern ones this is a pretty high number because the drive is rated MTBF 1,500,000 hours.  They combat this limit with 'wear leveling' (spreading writes around the drive).  And as others noted, it's best to configure the system to minimize disk writes.  But at $130 for the speed I've achieved, I would replace it every year if necessary (though I doubt it would die that quickly).

Linux gives you a lot of flexibility to configure the system to minimize wear.  You don't have to do these things, but they help not only with wear-reduction but also speed, and they're pretty simple to change.  Here are the steps I took after doing some reading on the subject:

1) I made three 6G system partitions (two spares) and one 13G data partition on the SSD.  (I like multiple system partitions available for testing upgrades, and if one eventually wears out, maybe I can use another.)  I always keep _[partition backups]("http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems")_ so I'm not that concerned with failure.

2) I located the swap partition on my 7200rpm conventional hard drive.  It is generally recommended not to locate it on the SSD due to excessive wear.

3) I located my (rarely used!) Windows XP system on the conventional drive.  Windows is constantly accessing the drive so I assume it would not be good for the SSD (although the drive does advertise itself for Windows).

4) I mounted /tmp, /var/log, and /var/tmp on a ramdrive (tmpfs).  That means these folders are stored in memory only, which is lost when the system is shut off.  Reason:  these folders get a lot of write activity.  An alternative if you want to keep your logs is to locate them on a conventional drive, or save their contents periodically or on poweroff.

4) For the SSD partitions, I used ext3 but raised the commit time from 5 sec to 120 sec (and I may raise that further), and also specify noatime.  ext3 is a journaling fs so it normally writes to the drive a lot.  Reducing the commit time means that I may lose two minutes worth of data (on the system partition) in the event of power failure, etc., instead of 5 seconds worth.  (That's what partition backups and battery UPS are for.)

5) I changed the kernel dirty page writeback time to 120 seconds (Disclosure: I don't really know what this is - shhhhh.  :-$)

6) I changed the I/O scheduler for the SSD to deadline instead of the default (cfq).  Using cfq doesn't make any sense for a random-access device.  You can also use noop, but thus far I think deadline behaves a little better.  I left cfq as the scheduler for the conventional drives.

7) Move Firefox's cache to a ramdrive, such as /tmp (mounted as tmpfs) or /dev/shm (default Ubuntu ramdrive), to reduce wear.

My detailed notes are below.

Notes:
```
SSD Changes

Add commit=120 and noatime to fstab ext3 / entry:
	/dev/sda1 /       ext3 noatime,commit=120  0 1

Add to fstab:
	# For SSD:
	tmpfs /var/log tmpfs defaults,noatime,size=200M,mode=0755 0 0
	tmpfs /tmp tmpfs defaults,noatime,size=1000M,mode=1777 0 0
	tmpfs /var/tmp tmpfs defaults,noatime,size=500M,mode=1777 0 0

Note: Setup swap partition on a hard drive not SSD

Add to bottom of /etc/sysctl.conf:
	# I added to reduce disk activity to 120 seconds
	vm.dirty_ratio = 40
	vm.dirty_background_ratio = 1
	vm.dirty_writeback_centisecs = 12000

Disable the part of pm-utils that will reset our sysctl.conf values by making the script that resets these values not executable:
	sudo chmod -x /usr/lib/pm-utils/power.d/laptop-tools

Add to /etc/rc.local just BEFORE line containing "exit 0":
	# for SSD:
	for dir in apparmor apt cups dist-upgrade fsck gdm installer news samba unattended-upgrades ; do
	mkdir -p /var/log/$dir
	done
	# Set sda to use deadline scheduler and FIFO batch to 1
	echo deadline > /sys/block/sda/queue/scheduler
	echo 1 > /sys/block/sda/queue/iosched/fifo_batch

Note: Alternatively, you can add "elevator=deadline" as a kernel boot option in /boot/grub/menu.lst, but this change will affect the scheduler of ALL drives (whereas the rc.local solution only affects the specified drives):
	kernel  /boot/vmlinuz-2.6.24-23-generic root=/dev/sda1 ro elevator=deadline

Note: You can use noop scheduler as an alternative to deadline
	http://en.wikipedia.org/wiki/Deadline_scheduler
	http://en.wikipedia.org/wiki/Noop_scheduler
	http://en.wikipedia.org/wiki/CFQ

Firefox cache to /dev/shm:
	In Firefox about:config right-click and create new string:
		browser.cache.disk.parent_directory
	and set value to
		/dev/shm/ff-cache

Reboot to affect changes

After boot, test these settings:
	cat /proc/mounts | grep commit
	cat /proc/sys/vm/dirty_ratio
	cat /proc/sys/vm/dirty_background_ratio
	cat /proc/sys/vm/dirty_writeback_centisecs
	cat /sys/block/sda/queue/scheduler
	cat /sys/block/sda/queue/iosched/fifo_batch
	cat /sys/block/sdb/queue/scheduler

References:
http://ubuntuforums.org/showthread.php?t=839998
http://starcubetech.blogspot.com/2008/10/ssd-optimization-on-ubuntu.html
http://forum.eeeuser.com/viewtopic.php?id=890

```

---

### Post by Chemical Imbalance on 2009-03-28
> **Swerve1000 said:**
> I'm interested to.

My research has shown me that some of the cheaper SSDs have very poor performance, in which regard I cannot remember though. The more expensive models though were operating much better.

Yes, do not go for an el cheapo.  My eeepc has a piece of junk 4gb that takes *forever*.

---

### Post by IgnorantGuru on 2009-03-28
> **kamolt said:**
> Thanks for the advice but I already installed the usual way with EXT3 and a SWAP partition. Should I reinstall ? It takes some time to reinstall all the programs and get everything right.

I recommend adding noatime and commit=120 to your fstab options on the SSD partitions for ext3.  It may not be necessary, but it will extend the life of the drive, and should also speed things up a bit.  I think modified ext3 is a better choice for stability.

```
/dev/sda1 /       ext3 noatime,commit=120  0 1
```

As for the swap, personally I would put it in a conventional drive partition if you have one available.  You can move your swap as follows:

```
To repair or install/change swap partition:

# WARNING: The following command destroys the contents of /dev/sdb1
sudo mkswap /dev/sdb1    # or wherever
sudo swapon -va
sudo vol_id -u /dev/sdb1

(put that UUID in fstab instead of /dev/sdb1):
	UUID=xxx none swap sw 0 0

Edit /etc/initramfs-tools/conf.d/resume
	RESUME=UUID=xxx 
(xxx = your correct swap UUID)

sudo update-initramfs -u

(reboot)

top       #shows current swap and memory usage

```

---

