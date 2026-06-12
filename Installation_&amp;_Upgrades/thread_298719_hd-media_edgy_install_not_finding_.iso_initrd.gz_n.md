---
title: "hd-media edgy install not finding .iso initrd.gz not ref correct .iso"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by john_spiral on 2006-11-13
Hi,

I've been palying around with installing edgy from an .iso file on a machine without a CD-ROM.

Looks like the initrd.gz file provided as part of the edgy hd-media install doesn't recognize any of the edgy .iso files (ubuntu, xubuntu...)

The installer boots fine from the vmlinuz & initrd.gz files, but the installer fails to locate the .iso file. I've placed the .iso file in the same folder as the vmlinuz & initrd.gz files. 

md5sum on the .iso file verifies it's fine and it's also got the correct extension. I've seen the same problem with quite a few uers attempting a hard disk install.

My question:

What line/s should I change within the initrd.gz file to ref the edgy .iso file?

The vmlinuz & initrd.gz files have been downloaded from the below location:

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/)

thanks in advance Johne

---

### Post by drtvasudevan on 2006-11-13
systems specs?
if it is a SATA hard disk it may not be recognised as hdaX
but as sdaX
or is it sde?
there is some issue here. that is what i remember.

---

### Post by john_spiral on 2006-11-13
I did a hd-install a while ago with the dapper .iso and had no problems. I think the current initrd.gz isn't correctly configured for the edgy iso's.

The machine is a sony vaio laptop and I'm sure it uses a bog standard ide drive. I'm currently running DSL (linux) and ubuntu dapper on the same machine. The machine has no CD-ROM drive

Has anyone out there managed to complete a hd-media install of edgy?

---

### Post by drtvasudevan on 2006-11-14
> **john_spiral said:**
> I did a hd-install a while ago with the dapper .iso and had no problems.
good
>  
Has anyone out there managed to complete a hd-media install of edgy?

ah! i would be interested in that!

---

### Post by john_spiral on 2006-11-15
Looks like a bug report has already been created for this problem.

[https://launchpad.net/distros/ubuntu/+source/iso-scan/+bug/71185](https://launchpad.net/distros/ubuntu/+source/iso-scan/+bug/71185)

Has anyone had success with the hd-insall?

---

### Post by fiveseven on 2006-11-15
I'm having the same problem, edgy hd-media installer fails to find the iso, ive tried various version of the ISO and even a drapper ISO (all with correct MD5sums) and none of the iso's are detected.

This is the only method i have available to install ubuntu on this computer, so a fix would be really appreciated. ](*,)

---

### Post by john_spiral on 2006-11-15
Is it worth having closer look at the initd file? 

I've done some searching and it looks like the initd file is mountable. I'm sure there is some script/file located in this ram disk image that will resolve this problem. 

any thoughts?

---

### Post by john_spiral on 2006-11-18
I never normally bump topics, but I think it's important that an iso file based install of edgy works.

It's the fastest way to install ubuntu even from machines just running windows. 

Come on there must be some Ubuntu Gandalfs who know what spells to cast to get the beast into action. 

At present there is no way to install Edgy (ubuntu, xubuntu...) on a machine from an iso file. Don't take my word for it run a topic title search in the forums for .iso, no cd-rom.... and you'll see everyone has the same problem.

Dapper had this facility! Lets not forget our roots.

;-)

johne

---

### Post by john_spiral on 2006-11-19
Hi,

I've managed to dig into the initd file by first expanding it with:

gunzip initrd.gz

to produce:

initrd

I used the below comand to extract the embedded file structure:

cpio -iv < initrd

The resulting ./var/lib/dpkg/info/iso-scan.postinst file looks responsible for the .iso search part of the installation.

see file contents below:

[FONT="Fixedsys"][COLOR="Olive"]#!/bin/sh
. /usr/share/debconf/confmodule
set -e

ISO_COUNT=0
ISO_MOUNT_COUNT=0
MOUNTABLE_DEVS_COUNT=0
TOPLEVEL_DIRS_COUNT=0

log () {
    logger -t iso-scan "$@"
}

mount_device () {
	dev_to_mount=$1
	db_subst iso-scan/progress_mount DRIVE $dev_to_mount
	db_progress INFO iso-scan/progress_mount
	mount -t auto -o ro $dev_to_mount /hd-media 2>/dev/null
}
		
is_debian_iso () {
	test -e /cdrom/.disk/info
}

register_cd () {
	# Set the suite and codename used by base-installer and base-config
	# to the suite/codename that is on the CD. This assumes that there
	# will be no more than one distribution on the CD, and that one of
	# the testing, stable, or unstable links will point to it. Since the
	# CDs currently have many links, parse the Release file to get the
	# actual suite name to use.
	for distlink in stable testing unstable ; do
		relfile=/cdrom/dists/$distlink/Release
		if [ -e $relfile ] ; then
			suite=$(sed -n 's/^Suite: *//p' $relfile)
			codename=$(sed -n 's/^Codename: *//p' $relfile)
			log "Detected ISO with '$suite' ($codename) distribution"
			db_set cdrom/suite $suite
			db_set cdrom/codename $codename
			db_subst iso-scan/success SUITE $suite
			
			description=`sed -n 's/^Description: *//p' $relfile`
			db_subst iso-scan/success DESCRIPTION $description
			
			break
		fi
	done
}

# Try to mount a file as an iso, and see if it's a Debian cd.
try_iso () {
	iso_to_try=$1
	iso_device=$2
	if mount -t iso9660 -o loop,ro,exec $iso_to_try /cdrom 2>/dev/null; then
		ISO_MOUNT_COUNT=$(expr $ISO_MOUNT_COUNT + 1)
		if is_debian_iso; then
			# This could be more sophisticated, and try to deal
			# with multiple Debian ISO's. For now, once we've got
			# a Debian ISO, any Debian ISO, we're done.
			register_cd $iso_to_try $iso_device
			db_progress STOP
			db_subst iso-scan/success FILENAME $iso_to_try
			db_set iso-scan/filename $iso_to_try
			db_subst iso-scan/success DEVICE $iso_device
			db_input medium iso-scan/success || true
			db_go || true

			anna-install apt-mirror-setup || true
			if [ ! -e /cdrom/.disk/base_installable ]; then
				log "Base system not installable from CD image, requesting choose-mirror"
				anna-install choose-mirror || true
			else
				anna-install apt-cdrom-setup || true
			fi
			exit 0
		else
			log "Not an Ubuntu ISO"
			umount /cdrom
		fi
	else
		log "Failed mounting $iso_to_try"
	fi
}

# Try to unmount anything that was previously mounted.
umount /cdrom 2>/dev/null || true
umount /hd-media 2>/dev/null || true

# Hopefully this will find the drive.
hw-detect iso-scan/detect_progress_title || true

# Load up every filesystem known to man. The drive could have anything.
FS="ext2 ext3 reiserfs fat vfat xfs iso9660 hfsplus hfs ntfs"
for fs in $FS; do
	modprobe $fs >/dev/null 2>&1 || true
done
modprobe loop >/dev/null || true

mkdir /cdrom 2>/dev/null || true
mkdir /hd-media 2>/dev/null || true

log "First pass: Look for ISOs near top-level of each filesystem."
DEVS="$(list-devices disk; list-devices partition)"
# Repeat twice if necessary, to accompdate devices that need some
# time to initialise, like USB devices.
for i in 1 2; do
	DEV_COUNT=0
	for dev in $DEVS; do
		DEV_COUNT=$(expr $DEV_COUNT + 1)
	done

	db_progress START 0 $DEV_COUNT iso-scan/progress_title

	for dev in $DEVS; do
		if ! mount_device $dev; then
			log "Waiting for $dev to possibly get ready.."
			sleep 3
			if ! mount_device $dev; then
				continue
			fi
		fi

		db_subst iso-scan/progress_scan DRIVE $dev
		log "Mounted $dev for first pass"
		MOUNTABLE_DEVS="$MOUNTABLE_DEVS $dev"
		MOUNTABLE_DEVS_COUNT=$(expr $MOUNTABLE_DEVS_COUNT + 1)
		cd /hd-media
		for dir in . *; do
			if [ -d "$dir" ]; then
				if [ "$dir" != "." ]; then 
					TOPLEVEL_DIRS_COUNT=$(expr $TOPLEVEL_DIRS_COUNT + 1)
				fi
				db_subst iso-scan/progress_scan DIRECTORY "$dir/"
				db_progress INFO iso-scan/progress_scan
				for iso in $dir/*.iso $dir/*.ISO; do
					if [ -e $iso ]; then
						log "Found ISO $iso on $dev"
						ISO_COUNT=$(expr $ISO_COUNT + 1)
						try_iso $iso $dev
					fi
				done
			fi
		done
		cd /
		umount /hd-media

		# It's possible that the ISO was written right to the front of a
		# device, and not to a filesystem. (Hey, we may even be spinning
		# a real CD here, though that would be pretty weird..)
		try_iso $dev $dev

		db_progress STEP 1
	done

	db_progress STOP

	OLDDEVS="$DEVS"
	DEVS=$(block_devices)
	if [ "$OLDDEVS" != "$DEVS" ]; then
		# Give USB time to settle, make sure all devices are seen
		# this time though.
		sleep 5
	else
		break
	fi
done

if [ "$MOUNTABLE_DEVS_COUNT" != 0 ]; then
	# Ask about the more expensive second pass.
	db_subst iso-scan/ask_second_pass NUM_FILESYSTEMS $MOUNTABLE_DEVS_COUNT
	db_subst iso-scan/ask_second_pass NUM_DIRS $TOPLEVEL_DIRS_COUNT
	db_input critical iso-scan/ask_second_pass || true
	db_go || true

	db_get iso-scan/ask_second_pass
	if [ "$RET" = true ]; then
		db_progress START 0 $TOPLEVEL_DIRS_COUNT iso-scan/progress_title
		log "Second pass: Search whole filesystems for ISOs."
		# To save time, only ones we mounted successfully before.
		for dev in $MOUNTABLE_DEVS; do
			if mount_device $dev; then
				db_subst iso-scan/progress_scan DRIVE $dev
				log "Mounted $dev for second pass"
				cd /hd-media
				for dir in *; do
					if [ -d "$dir" ]; then
						db_subst iso-scan/progress_scan DIRECTORY "$dir/"
						db_progress INFO iso-scan/progress_scan
						for iso in $(find $dir 2>/dev/null | grep -i '\.iso$'); do
							log "Found ISO $iso on $dev"
							ISO_COUNT=$(expr $ISO_COUNT + 1)
							try_iso $iso $dev
						done
						db_progress STEP 1
					fi
				done
				cd /
				umount /hd-media
			fi

		done

		db_progress STOP
	fi
fi

# Failure. Display the best message we can about what happened.
# Let them know the second pass failed too.
if [ "$ISO_COUNT" = 0 ]; then
	db_input critical iso-scan/no-isos || true
elif [ "$ISO_MOUNT_COUNT" != "$ISO_COUNT" ]; then
	db_input critical iso-scan/bad-isos || true
else
	db_input critical iso-scan/other-isos || true
fi
db_go || true
log "Failing with ISO_COUNT = $ISO_COUNT, MOUNTABLE_DEVS_COUNT = $MOUNTABLE_DEVS_COUNT, ISO_MOUNT_COUNT = $ISO_MOUNT_COUNT"
exit 1[/COLOR][/FONT]


Any ideas if the above code is responsible for not picking up the edgy .iso file?

---

### Post by RameshRao on 2006-11-19
I have had similar troubles](*,) . After I get the failure message, I switched to another console (Alt+F2) and examined the log files. It appears that the iso file is not getting mounted undet the /cdrom directory. I attempted a manual mount (mount -t iso9660 -o loop blah blah blah) and the mount fails complaining about the loop device not being present. Seems like a broken BusyBox ...

I guess the fix is generate another initrd with a working BusyBox, may be!?!

Ramesh

---

### Post by john_spiral on 2006-11-19
I also got a "couldn't setup loop device" error when attempting to mount the edgy iso file.

---

### Post by 20after4 on 2006-11-19
Exactly the same problem here. It seems like the hd-install images are out of date compared to the iso files. It's something to do with the losetup step for sure, I have been unable to get past that point.

The files at this url are dated  21-Oct-2006 01:43:
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/20060711ubuntu18/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/20060711ubuntu18/images/hd-media/)

While the ISO files are dated 25-Oct-2006 14:56:
[http://releases.ubuntu.com/edgy/](http://releases.ubuntu.com/edgy/)

Is there a more updated versoin of the initrd.gz file somewhere that I'm missing?

---

### Post by john_spiral on 2006-11-19
Anyone got a solution?

---

### Post by fiveseven on 2006-11-20
Just bumping the topic as its paramount for me (and many others) to getting ubuntu installed.

---

### Post by fiath on 2006-11-21
Just moving over to Ubuntu from SUSE, for obvious reasons, as I expect a lot of people are. Unfortunately I have hit this issue too. My laptop's external DVD is dead, and I can't afford a new one atm, especially as I haven't really needed it for >1 year. Now of course I have a problem because I can't install Ubuntu directly from the ISO...

Does anyone know of any alternative ways of installing? My only available USB key is 256Mb, so that option is out... Maybe there is some other way to first mount and the virtually boot from the ISO?

---

### Post by john_spiral on 2006-11-22
Hi,

what kernel is the installer using? If it's 2.6  it looks like we can get a mount going with a "-o ro" option.

See 'bcornec' posting on 02-21-06 02:03 on the bugs.busybox.net site:

[http://bugs.busybox.net/view.php?id=609](http://bugs.busybox.net/view.php?id=609)

Is it possible to mount the iso from a partition that's already been mounted on another mount point?

For example if I've mounted hda3 as /mnt/hda3

Can I mount the iso file /mnt/hda3/boot/filename.iso as /cdrom?

---

### Post by john_spiral on 2006-11-22
Again I couldn't get the mount going with the above options.

I tried:

mount -t iso9660 -o loop,ro /mnt/path_to_iso_file /mnt/cdrom

still gives:

Couldn't setup loop device

Edgy's installer has BusyBox version 1.1.3  & kernel 2.16.17-10-386

It might be possible to install BusyBox 1.2.2.1 (most recent version) inside the expanded initrd.gz file then return it back to it's compressed state?

any thoughts appreciated.

johne

---

### Post by john_spiral on 2006-11-23
Hi I've posted a question on busybox's mailing list about Ubuntu Installer's inability to mount the .iso file.

You can subscribe via the below address:

[http://busybox.net/cgi-bin/mailman/listinfo/busybox](http://busybox.net/cgi-bin/mailman/listinfo/busybox)

---

### Post by CarlosDC on 2006-11-24
Hi

After reading this thread and "If they configured busybox with "legacy devfs support" it'll look for /dev/loop/0 instead of /dev/loop0, which is sad." ([http://busybox.net/lists/busybox/2006-November/025368.html]("http://busybox.net/lists/busybox/2006-November/025368.html")).

I got it to work by doing the following:

Boot off the HD-MEDIA vmlinuz and initrd. Proceed as normal until you scan for the ISOs. It fails as mentioned previously then:

When the scan fails..

#Change to terminal 2 (Ctrl-Alt-F2)
#hit enter to activate this console...
#
#Then:
#
cd /dev
mkdir loop
mkdir 0
ln loop0 loop/0

#Change back to terminal 1 (Ctrl-Alt-F1)
#scan again and the ISO will be detected.

Cheers
Carlos

---

### Post by cjwatson on 2006-11-25
Yeah, um, oops. My fault. This is fixed in Feisty now ([https://launchpad.net/bugs/66220)](https://launchpad.net/bugs/66220)), although no test Feisty images are available yet. I've marked it as a candidate for backporting to Edgy, so that we can produce a fixed installer image; I'll look at this further when it isn't the weekend.

Carlos' fix looks reasonable to me, although the 'mkdir 0' step is incorrect and unnecessary. I'd abbreviate it to:

mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0

---

### Post by john_spiral on 2006-11-25
Hi,

I've made the /dev/loop directory and linked the /dev/loop0 directory to /dev/loop/0. Through the below commands:

mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0 

But the install still isn't finding the installation .iso file.

After running the above commands I can now mount the installation .iso file but the install still isn't completing.

A few questions cjwatson & Carlos,

(1) How does your menu.lst look?
(2) Where did you download the vmlinuz & initrd.gz files:

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/)

?
(3) What type of file system is your .iso, vmlinuz & initrd.gz files on?

(4) Did your install complete?

Has anyone else got the installation to work?

Thanks for all the effort 

Johne

---

### Post by fiath on 2006-11-26
Yup, I tried it using the same vmlinuz+initrd as you, and it mounted the ISO as expected, but it then "failed copying files from CDROM".

If you look at the attached logs (syslog, at the end) it seems to be looking for stuff that does not exist on my (desktop) edgy CD. Should I be using the alternate or something (a bit of a problem for me if I should! It took me weeks to get this one ;))

Anyway, an example error message is: "cdrom-retriever: warning: Unable to find main/debian-installer/binary-i386/Packages in /cdrom/dists/edgy/Release"

See attached logs for more details.

Anyone have any ideas what is wrong?

---

### Post by john_spiral on 2006-11-27
From your log files it looks like the mount is happening but the installer is failing to find the Packages or Packages.gz file/s.  

See lines dated Nov 26 01:52:49 in the above attached log file.

I'm not in front of my Ubuntu box, can someone mount the edgy .iso and see where the Packages/Packages.gz file/s are located?

---

### Post by fiath on 2006-11-27
From memory, I think it may have been something like 'main/binary-i386/Packages'. Problem was I wasn't sure how to change that...

---

### Post by CarlosDC on 2006-11-27
Sorry about the "mkdir 0" line - careless cut and paste.

Since I was installing onto a 128MB machine, I used the "ubuntu-6.10-alternate-i386.iso".

I got the hd-media vmlinuz and initrd.gz from:
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/]("http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/")

Checking the "ubuntu-6.10-desktop-i386.iso" the Packages file is in:
dists/edgy/main/binary-i386
dists/edgy/restricted/binary-i386

The install from the alternate ISO worked for me after that /dev/loop/0 fiddle.

Carlos

---

### Post by fiath on 2006-12-04
Yep! Installtion from the alt ISO worked for me too! Wahoo!

---

### Post by john_spiral on 2006-12-12
Hi,

I've taken the working method from this thread and posted a HOWTO:

HOWTO: Install Edgy 6.10 from an .iso file

[http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)

please join us.

Johne

---

