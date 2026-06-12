---
title: "Clean install without losing everything?"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by ideitt on 2011-10-25
Ok so i've been using ubuntu on my Dell XPS M1210 since 10.04 and it was working flawlessly up until 11.04. Now with 11.04 it randomly hangs for minuets on end and I cant seem to find a direct cause of it. Just today though, I started reading into the processor of my computer and apparently it is a 64bit processor and this whole time I have been running a 32 bit version. I'm not sure if this could be causing the freezing issue, but at any rate I would like to install the 64bit version. I have an 11.04 64bit live cd (i really don't want to upgrade to 11.10 as I just can't seem to warm up to unity) but my question is how can I do a clean install to the 64bit version and not have to reconfigure cairo dock, compiz and all my preferences. Also all my music and pictures are on my ubuntu partition but im just assuming i would have to transfer those all to an external HD prior to the upgrade. 
Thanks for any help.

---

### Post by critin on 2011-10-25
I imagine you'll need to reconfigure those things.  
Good choice--11.04 is a great system imo.

---

### Post by raja.genupula on 2011-10-26
clean install means its gonna take everything but if you take the backup of those files then in your home folder at hidden files these configuration files will be there and you can replace them with old one.

if you wanna keep the current version also means then install the ubuntu by placing the mounting point at the /home .

all the best man.

---

### Post by oldfred on 2011-10-26
A lot easier if you have a separate /home. But you can back up all of /home including the hidden files & folders that are your user settings. You may have a few system settings in /etc if you manually set anything system wide like special drivers or settings.

I do clean installs, but have all data in other partitions often on other drives. Since it is only a home system my recovery plan is just to do a clean install and restore from backups.

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications 

I include these also:
cp /etc/apt/sources.list ~/sources.list.backup
apt-key exportall > ~/repositories.key
Various hardware listings/configurations
dpkg --get-selections > ubuntu-files
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script.sh
lshw -html > ~/hardware_info.html
udevadm info --export-db > file.txt
dmidecode > bios.txt

Other applications if data not separate
apache, any sqldb, tomcat

---

### Post by rplantz on 2011-10-26
I assume that the most important things are those in your /home directory. I use a bash script that uses rsync to make a snapshot of my /home directory. I use an external hard disk for my backups. One of the nice things about using rsync is that the backed up files can be easily accessed one at a time from the hard disk.

Below is a copy of my script in case you would like to adapt it to your needs. Simply copy it into a file, say 'makesnapshot.sh'. Then make is executable with ```
chmod +x makesnapshot.sh
``` After mounting your external disk (e.g., plugging in a usb disk) simply execute the script with ```
./makesnapshot.sh
```

Make sure that your important files are copied correctly onto the external disk before you do the clean install. ;-)

```

#!/bin/bash
# ----------------------------------------------------------------------
# Shell script to use rsync for making a snapshot backup to an external
# hard disk.
#
# Adapted from mike's handy rotating-filesystem-snapshot utility
# www.mikerubel.org/computers/rsync_snapshots/
# 
# by: Robert Plantz - 05 June 2009
# ----------------------------------------------------------------------

# -------------- File and directory locations --------------------------
# Assume that the destination volume is mounted. I use an external
# usb disk that mounts automatically when plugged in.
DESTINATION=/media/Verbatim_Linux

# Default is to backup my home directory.
SOURCE=/home/bob/

# Other files and directories excluded or included are listed in the
# following file. See "FILTER RULES" and "INCLUDE/EXCLUDE PATTERN RULES"
# sections in the rsync man page for the format of this file.
# Examples are:
# - .mozilla/firefox/eyo8gt4n.default/Cache
# - .opera/cache4
# - .evolution/cache
EXCLUDES=backup_exclude

# -------------- System commands used by this script -------------------
unset PATH    # to make sure we use the right programs
ECHO=/bin/echo;
RM=/bin/rm;
MV=/bin/mv;
TOUCH=/bin/touch;
RSYNC=/usr/bin/rsync;
MKDIR=/bin/mkdir;

# -------------- Make the snapshot -------------------------------------
# Move existing snapshots back one.
if [ -d $DESTINATION/snapshot_4 ] ; then
   $RM -rf $DESTINATION/snapshot_4
   $ECHO "Deleted snapshot_4"
fi

if [ -d $DESTINATION/snapshot_3 ] ; then
   $MV $DESTINATION/snapshot_3 $DESTINATION/snapshot_4
   $ECHO "Created new snapshot_4"
fi

if [ -d $DESTINATION/snapshot_2 ] ; then
   $MV $DESTINATION/snapshot_2 $DESTINATION/snapshot_3
   $ECHO "Created new snapshot_3"
fi

if [ -d $DESTINATION/snapshot_1 ] ; then
   $MV $DESTINATION/snapshot_1 $DESTINATION/snapshot_2
   $ECHO "Created new snapshot_2"
fi

if [ -d $DESTINATION/snapshot_0 ] ; then
   $MV $DESTINATION/snapshot_0 $DESTINATION/snapshot_1
   $ECHO "Created new snapshot_1"
fi

# rsync from SOURCE to DESTINATION.
# rsync behaves like cp --remove-destination by default, so the destination
# is unlinked first.  If it were not so, this would copy over the other
# snapshot(s) too!
# See rsync man page for options. The time saver here is
# --link-dest. If a file has not changed from the copy in
# the specified directory, a hard link is created to the
# already existing copy rather than recopy the entire file.
# This saves both time and disk space.
if [ -d $DESTINATION/snapshot_1 ] ; then
   $ECHO "Creating snapshot_0 based on snapshot_1 on $DESTINATION"
   $RSYNC -a -v --delete    \
        --exclude-from=$EXCLUDES           \
        --link-dest=$DESTINATION/snapshot_1    \
        $SOURCE $DESTINATION/snapshot_0/
else
   $ECHO "Creating a new snapshot_0 on $DESTINATION"
   $MKDIR $DESTINATION/snapshot_0
   $RSYNC -a -v --delete    \
        --exclude-from=$EXCLUDES           \
        $SOURCE $DESTINATION/snapshot_0/
fi
$ECHO "rsync exit code is "$?
# update the mtime of snapshot_0 to reflect the snapshot time
$TOUCH $DESTINATION/snapshot_0

```

---

### Post by Mark Phelps on 2011-10-26
I seriously doubt your changing to 64-bit is going to do anything positive about the random hangs.  I'm running 32-bit OSs on a 64-bit machine, as well as 64-bit OSs, and see absolutely no differnces between the two versions.

---

