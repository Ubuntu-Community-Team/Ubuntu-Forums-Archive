---
title: "bootup up error after upgrade ot feisty"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by prezbedard on 2007-11-24
ok at first I thought this had to do with the problem with being unable to see my ntfs partitions after upgrading to feisty but that is fixed (thanks to you guys) but I still get his error every time I reboot though a ctrl-alt-del forces it to boot normally.

This is in the log and also appears at bootup

/var/log/fsck/checkfs

```
Log of fsck -C -R -A -a 
Sat Nov 24 14:31:13 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/hda2

/dev/hda2: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Sat Nov 24 14:31:13 2007
----------------
```

Here is my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b /               ext3    defaults,,errors=remount-ro 0       1
/dev/hda2 /support ext3 rw,auto,acl,errors=remount-ro 0       1
# /dev/hda1


/media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

# /dev/hdb1
/media/hdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdb2

                      /media/hdb2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=6e258be1-05a5-409f-be55-abd0f203a514 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

Here is the log from

/var/log/fsck/checkroot

```
Log of fsck -C -a -t ext3 /dev/sda2 
Sat Nov 24 14:31:13 2007

fsck 1.40-WIP (14-Nov-2006)
/dev/sda2: clean, 145984/6406144 files, 1792837/12799788 blocks

Sat Nov 24 14:31:13 2007
----------------
```

it appears they are both referring to the same device but as I have learned the s is new in feisty and replace  h so somehow something still see that volume as hda2 instead of sda2 which btw is my main Linux partiton

---

### Post by prezbedard on 2007-11-30
ok I was browsing my system and I'm pretty sure I'm correct that start up scripts are in 

```
/etc/init.d
```

I found the script that generates the log checkfs conveniently named checkfs.sh so I believe there is something in this script that still sees hda2 instead of sda2. I however don't have enough knowledge to know whether or not it is this file directly or indirectly. Here is the checkfs.sh

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          checkfs
# Required-Start:    modutils checkroot
# Required-Stop:
# Should-Start:      lvm cryptdisks
# Should-Stop:
# Default-Start:     S
# Default-Stop:
# Short-Description: Check all filesystems.
### END INIT INFO

PATH=/sbin:/bin
FSCK_LOGFILE=/var/log/fsck/checkfs
[ "$FSCKFIX" ] || FSCKFIX=no
. /lib/init/vars.sh

. /lib/lsb/init-functions

# Always output fsck progress
stdin=`readlink /proc/self/fd/0`
if [ "${stdin#/dev/null}" != "$stdin" ]; then
    exec </dev/console >/dev/console 2>&1
fi

do_start () {
	# See if we're on AC Power
	# If not, we're not gonna run our check
	if which on_ac_power >/dev/null 2>&1
	then
		on_ac_power >/dev/null 2>&1
		if [ $? -eq 1 ]
		then
			[ "$VERBOSE" = no ] || log_success_msg "Running on battery power, so skipping file system check."
			BAT=yes
		fi
	fi

	#
	# Check the rest of the file systems.
	#
	if [ ! -f /fastboot ] && [ ! "$BAT" ] && [ "$FSCKTYPES" != "none" ]
	then
		if [ -f /forcefsck ]
		then
			force="-f"
		else
			force=""
		fi
		if [ "$FSCKFIX" = yes ]
		then
			fix="-y"
		else
			fix="-a"
		fi
		spinner="-C"
		case "$TERM" in
		  dumb|network|unknown|"")
			spinner=""
			;;
		esac
		[ "$(uname -m)" = s390 ] && spinner=""  # This should go away
		FSCKTYPES_OPT=""
		[ "$FSCKTYPES" ] && FSCKTYPES_OPT="-t $FSCKTYPES"
		handle_failed_fsck() {
			log_failure_msg "File system check failed. 
A log is being saved in ${FSCK_LOGFILE} if that location is writable. 
Please repair the file system manually."
			log_warning_msg "A maintenance shell will now be started. 
CONTROL-D will terminate this shell and resume system boot."
			# Start a single user shell on the console
			if ! sulogin $CONSOLE
			then
				log_failure_msg "Attempt to start maintenance shell failed. 
Continuing with system boot in 5 seconds."
				sleep 5
			fi
		}
		if [ "$VERBOSE" = no ]
		then
			log_action_begin_msg "Checking file systems"
			logsave -s $FSCK_LOGFILE fsck $spinner -R -A $fix $force $FSCKTYPES_OPT
			FSCKCODE=$?
			if [ "$FSCKCODE" -gt 1 ]
			then
				log_action_end_msg 1 "code $FSCKCODE"
				handle_failed_fsck
			else
				log_action_end_msg 0
			fi
		else
			if [ "$FSCKTYPES" ]
			then
				log_action_msg "Will now check all file systems of types $FSCKTYPES"
			else
				log_action_msg "Will now check all file systems"
			fi
			logsave -s $FSCK_LOGFILE fsck $spinner -V -R -A $fix $force $FSCKTYPES_OPT
			FSCKCODE=$?
			if [ "$FSCKCODE" -gt 1 ]
			then
				handle_failed_fsck
			else
				log_success_msg "Done checking file systems. 
A log is being saved in ${FSCK_LOGFILE} if that location is writable."
			fi
		fi
	fi
	rm -f /fastboot /forcefsck
}

case "$1" in
  start|"")
	do_start
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	# No-op
	;;
  *)
	echo "Usage: checkfs.sh [start|stop]" >&2
	exit 3
	;;
esac

:
``` 

any ideas?

Thanks.

---

