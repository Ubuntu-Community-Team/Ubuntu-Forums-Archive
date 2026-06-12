---
title: "Problem upgrading from CD and ISO"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by Jason Spaceman on 2008-11-01
I'm trying to upgrade Ubuntu 8.04 to 8.10 via the alternate CD.  I downloaded the CD, burned it to a disc and tried to run 'sudo cdromupgrade', but I get the following error:

 > snozzy@loonix:/media/cdrom$ sudo ./cdromupgrade
tar: ./dists/stable/main/dist-upgrader/binary-all//intrepid.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
Could not find the upgrade application in the archive, exiting

I get the same error if I try to mount the .iso file and run 'sudo cdromupgrade'.  What am I doing wrong?  It seems to be complaining about not being able to find 'intrepid.tar.gz', but that file is on the disc.  Did Ubuntu screw up and put a '//' where just '/' should have been?

---

### Post by Earl_Maroon on 2008-11-01
Are you able to access that file manually? There might have been an error in the download that renders the file unreadable.

---

### Post by Jason Spaceman on 2008-11-01
> **Earl_Maroon said:**
> Are you able to access that file manually? There might have been an error in the download that renders the file unreadable.

Yeah, this is what the cdromupgrade file contains:

> snozzy@loonix:/media/cdrom$ cat cdromupgrade
#!/bin/sh
#
# "cdromupgrade" is a shell script wrapper around the dist-upgrader
# to make it possible to put it onto the top-level dir of a CD and
# run it from there
#
# Not that useful unfortunately when the CD is mounted "noexec".
#
# WARNING: make sure to call it with a absolute path!
#          (e.g. /cdrom/cdromugprade)

# the codename is AUTO-GENERATED from the build-host relase codename
CODENAME=intrepid
UPGRADER_DIR=dists/stable/main/dist-upgrader/binary-all/

cddirname="${0%\/*}"
fullpath="$cddirname/$UPGRADER_DIR"

# extrace the tar to a TMPDIR and run it from there
if [ ! -f "$fullpath/$CODENAME.tar.gz" ]; then
    echo "Could not find the upgrade application archive, exiting"
    exit 1
fi

TMPDIR=$(mktemp -d)
cd $TMPDIR
tar xzf "$fullpath/$CODENAME.tar.gz"
if [ ! -x $TMPDIR/$CODENAME ]; then
    echo "Could not find the upgrade application in the archive, exiting"
    exit 1
fi
$TMPDIR/$CODENAME --cdrom "$cddirname" $@

I wonder if it is [the same as this bug.]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/277873")

---

