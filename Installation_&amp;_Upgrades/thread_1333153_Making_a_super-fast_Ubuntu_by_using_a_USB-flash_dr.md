---
title: "Making a super-fast Ubuntu by using a USB-flash drive and RAM?"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by Walther -FI- on 2009-11-21
Hello everyone,

I have a nice, fast computer, but I still want it to be faster. (If it ain't broken, fix it until it is ;) )

Could it be possible to make a USB-flash drive, with fully operating Ubuntu in it, which would boot into RAM and still be able to save things into the USB-drive and/or to the hard drive? I want to be able to use Ubuntu normally - to be able to install stuff, etc.

That would make a great improvement in the speed of the computer - RAM reading and writing speeds are so much bigger compared to a normal hard drive.

I'm having a Core2 Quad, 4gb of RAM, enough big USB-flash drive and so on, so the hardware is not the issue.

Thank you in advance,

Walther

---

### Post by scorp123 on 2009-11-21
Why USB??? USB is slow like hell.

If you want to speed things up you should at least do it the right way. You could experiment with I/O schedulers (I have achieved good results with the **deadline** scheduler) and with the **vm.swappiness** settings.

[http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that](http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that)

(you might have to browse to the top of that page ... for some odd reasons it always opens at the comment section towards the bottom ...)

---

### Post by phillw on 2009-11-21
The Vista marked 'Memory Boost' usb memory sticks are both fast & designed for heavy usage without over-heating and dying. They are not, however, cheap - like about 2 - 3 X price of 'normal' usb memory stick of the same capacity. I have heard of pen-drives dying, usually through over-heating. It just so happens I have a2GB one from this machine being vista dual boot and, as a dual usb, persistant stick - it's fast :-)

As with all memory, there's memory and there's memory. If you are serious about keeping your data / installation - IMHO, I'd pay the extra cash and get one of those drives - they are not certified for usage as a memory swap area for nothing.

A good site for playing with pen-drives is -->>  [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)  They some quite wonderful combinations !!!

From memory, the 32 bit 9.10 system can handle something like 64GB of RAM - So, you could always install a nice big RAM DISK ;-)
(You have to install an 'extra for that - by default it is 3.5 GB)
Regards,

Phill.

---

### Post by Walther -FI- on 2009-11-21
Hi,

Scorp, thanks for your post, but that wouldn't help in my case - because as I said, I have enough RAM (2x 2Gb) and my 2Gb swap area is empty all the time. And, USB 2.0 -flash drives are not slow, compared to hard disk drives.

Phill, thanks for your post, but I'm not really looking for a good, fast USB-flash drive but a way to make my computer really fast by using the hard drive as little as I can. I have had an usb-bootable Ubuntu, from pendrivelinux, but the problem has been that it seems to use my HDD a lot (swap area maybe?) even though I have lots of RAM. And, it has been quite slow. I would like to have the system booting entirely to RAM, and only be able to use HDD when I want to.

Because, the main point is to make my computer as fast as possible, and hard disk drives are _really_ slow.


The main idea could be that the USB-flash drive would copy itself entirely to RAM and boot from there, and when shutting down copying everything from RAM back to the USB-flash. And being a _completely_ installed version of Ubuntu in the USB-flash, not a "portable" version.

---

### Post by scorp123 on 2009-11-21
> **Walther -FI- said:**
>  but that wouldn't help in my case  You obviously didn't read or understand the article I linked to. My machine has 8 GB RAM and modifying the vm.swappiness settings **_definitely helps_** even if either way you never ever use swap. It's all about snappiness. Plus the article mentions other settings too that have an influence on the amount of RAM used for disk caching vs. amount of RAM used for running apps.

> **Walther -FI- said:**
>  And, USB 2.0 -flash drives are not slow, compared to hard disk drives.  Yeaaah? Riiiiight.

USB 2.0 = 40 MB/s effective rate for bulk transfer (... such as booting an OS ...)

USB Flash drives = 30 MB/s average ... and only if nothing else is on the same USB bus. Read it for yourself:
[http://www.everythingusb.com/usb2/faq.htm](http://www.everythingusb.com/usb2/faq.htm)

SATA = 150 MB/s minimum ... modern SATA drives are rated at 300 MB/s.

So which one again is faster? USB @30 MB/s or SATA @150+ MB/s ???

> **Walther -FI- said:**
>  The main idea could be that the USB-flash drive would copy itself entirely to RAM and boot from there ...  You want RAM disks?

[http://www.linux-mag.com/cache/7388/1.html](http://www.linux-mag.com/cache/7388/1.html)

---

### Post by Walther -FI- on 2009-11-22
Hello again,

Scorp, thanks for your post. I have been really busy, so I read the article you linked to quite fast. I was wrong. I'm going to try tweaking the swappiness. And I already know about RAM-drives, they seem to be very interesting. They are quite expensive, though. I'm buying one of those into my next computer, maybe during the next summer.

And the USB-thing. Again, I was wrong. Thank you for making it clear to me. I have always been interested in learning things.

So, I edit my question a bit:
Could it be possible to make the OS boot partly/fully into RAM, from the SATA-HDD? It could improve the speed of opening/using applications. (?)

And about other tweaks: I know about configuring the startup applications with sysv-rc-config, removing eye-candies (I don't want to :D ) and all these "basic" things. They are not what I'm looking for, at this time, because I know about them (the basics).

I would like to use more RAM because a) I have some of it b) it is faster than HDD and c) my computer isn't using RAM quite much (it could use more, and thus improve the speed of everything?)

(and apologies for my bad English...)



Thank you in advance,

--
Walther

---

### Post by phillw on 2009-11-22
Hi,

Read the link provided by scorp - it's an excellent article. I thoroughly enjoyed it :D

You'll have to track down a motherboard that supports the amount of RAM you want (There are some good ones out there) and then save up for the RAM - If you choose your motherboard carefully, you will be able to install x amount of RAM to begin with and add to it as funds allow, so you'll be looking for a m/board with LOTS of RAM slots ;)
Do, however, bear in mind that YOU will be responsible for data safety, I'd suggest NOT putting /home into RAM. That will, at least will mean your documents etc get saved to hard-disk. Certainly an interesting project, I wish you well with it.

Here's someone who's done it :  [http://cboard.cprogramming.com/tech-board/115697-running-linux-ramdisk-root.html](http://cboard.cprogramming.com/tech-board/115697-running-linux-ramdisk-root.html)

According to quick read I've done /dev/shm  is setup automatically and will grow to 1/2 of your RAM area, 

Phill.

---

### Post by presence1960 on 2009-11-22
**_Internal Solid State Drives (SSD)_**

---

### Post by phillw on 2009-11-22
> **presence1960 said:**
> **_Internal Solid State Drives (SSD)_**

I've looked at SSD's - whilst they are, doubtless, faster than their robotic bretheren, they're still in league 4 as compared to RAM disks. when you are comparing millisecond access times to nanosecond access times ... well - it's kinda of an unfair competition 

Bit like pitching an F15 against the Wright Brothers ;)

Phill.

---

### Post by scorp123 on 2009-11-22
> **Walther -FI- said:**
>  Scorp, thanks for your post. I have been really busy, so I read the article you linked to quite fast. I was wrong. I'm going to try tweaking the swappiness. Trust me. It really helps improve the perceived snappiness of the system. I am currently running this very laptop I am writing this from with these settings:
```
vm.vfs_cache_pressure = 50
vm.swappiness = 10
```

... People who've sat in front of it find it hard to believe that this is only a old "CoreDuo" (= the Intel product line before "Core2Duo" were introduced) from 2004 running at 1.6 GHz. And I have desktop effects and what not turned on. Despite all the "bling bling" it all feels fast and smooth even if I have lots of windows open.

> **Walther -FI- said:**
>   Could it be possible to make the OS boot partly/fully into RAM, from the SATA-HDD? It could improve the speed of opening/using applications. (?) Yes, that was the idea of the link I posted. The article explains how to create your own temporary RAM disks e.g. dedicating parts of your RAM for a mount-point ...

So depending on what you want to do with your computer you could follow that method maybe? I imagine a file server or a database that's running on a RAM disk should have superb read and write I/O performance.

Maybe you could write a boot script that ...
- creates a RAM disk upon boot
- creates a mount point ... e.g. /opt ?
- rsync's the software you want to run from the HD, e.g. /opt_archive
- then starts the actual software from your /opt/path/to/application (now on your RAM disk)

I imagine that this would be super fast.

Your real problem is going to be reliabilty. One small electric glitch or a sudden power outage and whatever you had on that RAM drive will be gone ...

Or maybe use ZFS? e.g. via "zfs-fuse" ... With ZFS it would be easy to integrate both a RAM disk and a hard disk into one single ZFS pool. ZFS is smart enough to use the faster RAM disk for caching often accessed stuff ...

Maybe you could construct something like that using "unionfs" too? e.g. the saved data is mounted from the disk, the RAM disk is mounted on top over that and just takes the deltas (= the data that changed). In case of a power outage you'd only be setback to the data you already had on the disk ....

Maybe you could try something like that?

---

### Post by Walther -FI- on 2009-11-22
Hi again,


I read the article someone posted about mounting the whole / (root) to RAM during boot ( [http://blog.rikiji.it/index.xml#i4](http://blog.rikiji.it/index.xml#i4) ) - and that is what I would like to have - because I have already the /home on other partition in my HDD, there shouldn't be any major fears of losing data. (?) (always when a new Ubuntu version comes, I perform a clean install to root partition)

However, the files that have to be edited to make this ramdisk mount and load stuff from the HDD root partition during boot, are really different in the examples than the ones on my computer. (the article and example scripts are written for Debian) With my experience, I cannot be creative and merge things together. I have been using linux distros for over three years, and I know quite much - but not enough to do it alone.

If someone has enouh (read: too much) free time, and wants to help me - many thanks!

Here is the content of my /usr/share/initramfs/scripts/local , the file that should be edited (by the article of rikiji)

```

# Local filesystem mounting			-*- shell-script -*-

# Parameter: device node to check
# Echos fstype to stdout
# Return value: indicates if an fs could be recognized
get_fstype ()
{
	local FS FSTYPE FSSIZE RET
	FS="${1}"

	# blkid has a more complete list of file systems,
	# but fstype is more robust
	eval $(fstype "${FS}" 2> /dev/null)

	if [ -z "${FSTYPE}" ]; then
		FSTYPE="unknown"
	fi

	if [ "$FSTYPE" = "unknown" ] && [ -x /sbin/blkid ]; then
		FSTYPE=$(/sbin/blkid -s TYPE -o value "${FS}" 2> /dev/null)
	fi
	RET=$?

	if [ -z "${FSTYPE}" ]; then
		FSTYPE="unknown"
	fi

	echo "${FSTYPE}"
	return ${RET}
}

root_missing()
{
	ROOT="${1}"
	[ ! -e "${ROOT}" ] || ! $(get_fstype "${ROOT}" >/dev/null) || ! /sbin/udevadm settle
}

# Parameter: Where to mount the filesystem
mountroot ()
{
	[ "$quiet" != "y" ] && log_begin_msg "Running /scripts/local-top"
	run_scripts /scripts/local-top
	[ "$quiet" != "y" ] && log_end_msg

	# If the root device hasn't shown up yet, give it a little while
	# to deal with removable devices
	while root_missing "${ROOT}"; do
		log_begin_msg "Waiting for root file system..."

		# Default delay is 30s
		if [ -z "${ROOTDELAY}" ]; then
			slumber=30
		else
			slumber=${ROOTDELAY}
		fi
		if [ -x /sbin/usplash_write ]; then
			/sbin/usplash_write "TIMEOUT ${slumber}" || true
		fi

		slumber=$(( ${slumber} * 10 ))
		while root_missing "${ROOT}"; do
			/bin/sleep 0.1
			slumber=$(( ${slumber} - 1 ))
			[ ${slumber} -gt 0 ] || break
		done

		if [ ${slumber} -gt 0 ]; then
			log_end_msg 0
		else
			log_end_msg 1 || true
		fi
		if [ -x /sbin/usplash_write ]; then
			/sbin/usplash_write "TIMEOUT 15" || true
		fi

		# Run failure hooks, hoping one of them can fix up the system
		# and we can restart the wait loop.  If they all fail, abort
		# and move on to the panic handler and shell.
		if root_missing "${ROOT}" && ! try_failure_hooks; then
			break
		fi
	done

	# We've given up, but we'll let the user fix matters if they can
	while root_missing "${ROOT}"; do
		# give hint about renamed root
		case "${ROOT}" in 
		/dev/hd*)
			suffix="${ROOT#/dev/hd}"
			major="${suffix%[[:digit:]]}"
			major="${major%[[:digit:]]}"
			if [ -d "/sys/block/sd${major}" ]; then
				echo "WARNING bootdevice may be renamed. Try root=/dev/sd${suffix}"
			fi
			;;
		/dev/sd*)
			suffix="${ROOT#/dev/sd}"
			major="${suffix%[[:digit:]]}"
			major="${major%[[:digit:]]}"
			if [ -d "/sys/block/hd${major}" ]; then
				echo "WARNING bootdevice may be renamed. Try root=/dev/hd${suffix}"
			fi
			;;
		esac
		echo "Gave up waiting for root device.  Common problems:"
		echo " - Boot args (cat /proc/cmdline)"
		echo "   - Check rootdelay= (did the system wait long enough?)"
		echo "   - Check root= (did the system wait for the right device?)"
		echo " - Missing modules (cat /proc/modules; ls /dev)"
		panic "ALERT!  ${ROOT} does not exist.  Dropping to a shell!"
	done

	# Get the root filesystem type if not set
	if [ -z "${ROOTFSTYPE}" ]; then
		FSTYPE=$(get_fstype "${ROOT}")
	else
		FSTYPE=${ROOTFSTYPE}
	fi

	[ "$quiet" != "y" ] && log_begin_msg "Running /scripts/local-premount"
	run_scripts /scripts/local-premount
	[ "$quiet" != "y" ] && log_end_msg

	if [ ${readonly} = y ] && \
	   [ -z "$LOOP" ]; then
		roflag=-r
	else
		roflag=-w
	fi

	# FIXME This has no error checking
	modprobe ${FSTYPE}

	# FIXME This has no error checking
	# Mount root
	mount ${roflag} -t ${FSTYPE} ${ROOTFLAGS} ${ROOT} ${rootmnt}
	mountroot_status="$?"
	if [ "$LOOP" ]; then
		if [ "$mountroot_status" != 0 ]; then
			if [ ${FSTYPE} = ntfs ] || [ ${FSTYPE} = vfat ]; then
				panic "
Could not mount the partition ${ROOT}.
This could also happen if the file system is not clean because of an operating
system crash, an interrupted boot process, an improper shutdown, or unplugging
of a removable device without first unmounting or ejecting it.  To fix this,
simply reboot into Windows, let it fully start, log in, run 'chkdsk /r', then
gracefully shut down and reboot back into Windows. After this you should be
able to reboot again and resume the installation.
(filesystem = ${FSTYPE}, error code = $mountroot_status)
"
			fi
		fi
	
		mkdir -p /host
		mount -o move ${rootmnt} /host

		while [ ! -e "/host/${LOOP#/}" ]; do
			panic "ALERT!  /host/${LOOP#/} does not exist.  Dropping to a shell!"
		done

		# Get the loop filesystem type if not set
		if [ -z "${LOOPFSTYPE}" ]; then
			eval $(fstype < "/host/${LOOP#/}")
		else
			FSTYPE="${LOOPFSTYPE}"
		fi
		if [ "$FSTYPE" = "unknown" ] && [ -x /sbin/blkid ]; then
			FSTYPE=$(/sbin/blkid -s TYPE -o value "/host/${LOOP#/}")
			[ -z "$FSTYPE" ] && FSTYPE="unknown"
		fi

		if [ ${readonly} = y ]; then
			roflag=-r
		else
			roflag=-w
		fi

		# FIXME This has no error checking
		modprobe loop
		modprobe ${FSTYPE}

		# FIXME This has no error checking
		mount ${roflag} -o loop -t ${FSTYPE} ${LOOPFLAGS} "/host/${LOOP#/}" ${rootmnt}

		if [ -d ${rootmnt}/host ]; then
			mount -o move /host ${rootmnt}/host
		fi
	fi

	[ "$quiet" != "y" ] && log_begin_msg "Running /scripts/local-bottom"
	run_scripts /scripts/local-bottom
	[ "$quiet" != "y" ] && log_end_msg
}

```


I hope that you understand that I'm ready to do some work, and I really am excited about modifying things. (I'm one of the adminstrators in my high school and we have a own linux-based server and a one whole class full of linux-computers, quite a lot of things to do)

So, you don't have to do everything ready for me (I know that no-one would do that) but just explain what should be done and show the main things that have to be done to the "local"-script file.


Many thanks to you all!

--
Walther

---

### Post by doixanh on 2009-11-22
Ok I figured it out. Since I don't have RAM as much as 4gb (I have 2GB only), I managed to put the /usr/share into RAM since boot. This directory in my system is only 400MB, but I believe it's one of the most accessed directories in my system. It worths being put in RAM :-)

Basically I followed the instructions at Rikiji's blog, with only some minor modification to the boot up script:
```

    # FIXME This has no error checking
    # Mount root
    echo "dx: Mounting root to '$rootmnt' ..."
    mount ${roflag} -t ${FSTYPE} ${ROOTFLAGS} ${ROOT} ${rootmnt}
    
    # added: create the /usr/share in RAM, unpack the content
    echo "dx: create /usr/share in RAM..."
    mount -t tmpfs none ${rootmnt}/usr/share
    cd ${rootmnt}/usr/share
    echo "dx: Unpacking /usr/share into ram..."
    ${rootmnt}/bin/tar -xf "$rootmnt/usr.share.tar"
    echo "dx: Unpacking done. Enjoy."

```compressing my /usr/share directory into a tarball:
```

dx@dx-laptop:~$ cd share/
dx@dx-laptop:/usr/share$ sudo tar -cf /usr.share.tar *

```generate initrd:
```
sudo mkinitramfs -o /boot/initrd.img-`uname -r`-ramshare
```add an entry to grub.cfg
```

menuentry "Ubuntu, Linux 2.6.31-14-generic '/usr/share in RAM'" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 18ab529a-0502-4374-bfbd-55c62bf5a934
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=18ab529a-0502-4374-bfbd-55c62bf5a934 ro  quiet  splash
    initrd    /boot/initrd.img-2.6.31-14-generic-ramshare
}

```The drawback is that whenever  installing packages I have to restart, install them and recreate my /usr.share.tar
It's acceptable since I installed almost everything I need for everyday work :D

/edit : I've just moved /usr/lib into RAM, too... it's fast, really. Boot time increased ~30 secs but everything is blazingly fast :D

---

### Post by doixanh on 2009-11-22
**Some personal comments about this idea**

Advantages :
- reduces application start time
- packed data in tarballs is (nearly) continous, therefore unpacking the data doesn't force the HDD's head to jump everywhere, thus effectively treats high HDD's "random seek" time. This is critical for slow HDD, especially laptop ones (like mine :D)

Disadvantages :
- inconvenience of (re)installing apps
- requirements of HUGE RAM
- increase of boot time

---

### Post by phillw on 2009-11-22
> **doixanh said:**
> **Some personal comments about this idea**

Advantages :
- reduces application start time
- packed data in tarballs is (nearly) continous, therefore unpacking the data doesn't force the HDD's head to jump everywhere, thus effectively treats high HDD's "random seek" time. This is critical for slow HDD, especially laptop ones (like mine :D)

Disadvantages :
- inconvenience of (re)installing apps
- requirements of HUGE RAM
- increase of boot time


Dear Santa .......  :D

Guess that means I'm saving up for some RAM - 2 X 2GB is the maximum for my laptop. 
I'll bookmark this thread for when I get it.

Thanks for the info,

Phill.

---

### Post by Walther -FI- on 2009-11-27
Hello again, folks

I started to wonder - could it be possible to make a script that compresses the whole root (without /home and some others that are on different partitions) to a tarball during the shutdown and when booting up, using that tarball to boot to RAM?

That would mean, that no major data losses could happen and the whole system would be running from RAM, without a need to update the tarball every time when installing something.


--
Walther

---

### Post by ProDigit on 2009-11-30
I did a test about this a while ago, and generally running Xubuntu on a USB stick works fine with EXT4 partition, no SWAP partition, and creating a RAM disk for temporary internet files or cache files.

The best USB sticks for the jobs at the moment are those flash drives, (or SSD drives as they sometimes call them) that have both USB2.0 and an e-sata port on each side of the stick.

They boast an acceptable 30-50MB/s burst speed on average, and between 12 and 28MB/s random read, and are your best bets in running the OS fast and silent!
No need for running from RAM. Running Ubuntu from RAM only makes sense if you have +4GB of RAM.
Especially so, if you have an integrated graphics chip that uses part of the RAM as VRAM, and have no cache drive!

Remember that you can't upgrade, can't update, can't install programs, and can't run the OS infinitely from RAM (if there's even that possibility); because if you do, as soon as you reboot, the Os will need to reload again.
Some computers on standby don't allow loading the full OS from RAM.

A modern USB stick is fast enough for your needs!
Use 8 or 16GB. 4GB is too small for Ubuntu, because it needs an additional 1,5GB of free space for updates and system upgrades!
Every major USB flash drive manufacturer has a performance line of USB sticks.
They might have low iops, but their high throughput (30-50MB/s) can help bottlenecks when reading/writing to the stick.
I currently use an old 4GB flash drive with 8/5 MB/s R/W . It has low IOPS, but xubuntu runs just fine.
I only have problems with Firefox storing cache data on the disk while browsing (especially watching youtube vids), and when major system OS upgrades are available. Then I need to download the new ISO, and re-install the OS on the stick since I only have 800MB free space (I also have some programs installed).

Remember to enable noatime!

---

### Post by doixanh on 2009-12-08
Well, at first I thought tar is better than tar.gz. Since I had a quite good CPU (a Core2 Duo 2.53GHz), I've just decided to use tar.gz to compress the backup /usr/lib and /usr/share to share the work between HDD and CPU :D

Result is much less time disk read and boot time is dramatically reduced.
tar : total size is around 1GB, untar takes ~30 secs
tar.gz : total size is around 350MB, decompression takes ~13 secs

Also, since it's a dual-core CPU, I tried pigz instead of default gzip, and the decompression time is only 10 secs.

Much better improvement I think.

@ProDigit : well, every method has its own drawbacks. Moving files to RAM makes everything fast, but (re)installing apps is very inconvenient. It's the main disadvantages. But I installed most of the things I need, what do I need more? :D

Buying SSD drives consumes a lot of money. I'd rather buy more RAM. USB sticks are too slow. Read the previous page and the articles.

---

### Post by ProDigit on 2009-12-08
> **doixanh said:**
> 
@ProDigit : well, every method has its own drawbacks. Moving files to RAM makes everything fast, but (re)installing apps is very inconvenient. It's the main disadvantages. But I installed most of the things I need, what do I need more? :D

Buying SSD drives consumes a lot of money. I'd rather buy more RAM. USB sticks are too slow. Read the previous page and the articles.

I beg to differ! Latest USB sticks with an esata port on the other side (in specific the OCZ throttle is blazing fast).
Read more here:
[http://www.tomsguide.com/us/eSATA-USB-Flash,review-1195.html](http://www.tomsguide.com/us/eSATA-USB-Flash,review-1195.html)

It's faster than a 7200rpm HD in everything but continuous write/read.

I'm thinking of either buying a stick like this, or wait for an upcoming flash memory stick with a USB3.0 connection.

---

### Post by Stason on 2010-03-10
Wow! Great post! Hope this works in Lucid!

On the plus side I would also add increased virus and data protection, since all malicious or corrupted code lives only until next reboot. :popcorn:

---

