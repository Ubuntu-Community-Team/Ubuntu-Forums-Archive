---
title: "Desktop 6.06 - Failed to create filesystem"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by dariusq2km on 2006-06-06
Hi,

Just trying out 6.06 on a spare HP ML110 with 2610SA adaptec raid controller. 

Server 6.06 installs flawlessly from CD.

Desktop 6.06 has a problem while creating filesystems (again installing from CD).

As much detail as I have time to type right now is attached below;

I am new to ubuntu and linux so any help, suggestions, constructive feedback etc is appreciated.

Thanks,
Darius

--------------------

With existing partitions the manual partitioning tool shows 'locks' against all existing partitions with no apparent means of changing filesystem or mount points, even if a partition is unformatted (after repartiitioning with fdisk) but set as bootable.

Otherwise, (on Step 5 of 6), Selecting 'Erase entire disk: SCS1 (0,0,0) (sda) - 80.0 GB CERC Array 0' results in two partitions (shown on the config summary dialog);
   #1 of /dev/sda as ext3
   #5 of /dev/sda as swap

Clicking the 'install' button kicks off formatting partition #1 (~70GB) with ext3 but gets to 20% and dies with 'Failed to create file system'. The installer attempts to continue after the error dialog is dismissed.

At this point fdisk is used to write an empty partition table to /dev/sda, then boot from the CD again.

Then, selecting 'manual' partitioning and creating a 3GB partition for /, 1Gb for swap and 15GB for /usr, the formatiing process begins for partition #1 (only 3GB now) and about 15-20% the way thru again; 'Failed to create file system'.

Now for at some logs;

First /var/log/installer/syslog;

After 'switched to page stepPartAuto' there are 21 lines of text made up multiple occurances of the following 2 lines (mostly the 2nd one);

/lib/partman/recipes.sh: line 31: local: `-': not a valid identifier

or this 

/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier

Followed by;
ubiquity: Starting up '['/usr/share/ubiquity/summary']' for ubiquity.components.summary.Summary
ubiquity: Watching for questions patterns ^ubiquity/summary$
swapon: /dev/sda5: Device or resource busy

(note that removing the `-' from lines 31 and 114 makes the parse error go away but the general problem remains)

In /var/log/messages, /var/log/syslog, /var/log/user.log

ubuntu kernel: ... Adding .. swap on /dev/sda5
ubuntu partman: /sbin/tunefs: Filesystem revision too high while trying to open /dev/sda1
ubuntu partman: Couldn't find valid system superblock
ubuntu partman: mke2fs 1.38 (30- Jun- 2005)
ubuntu partman: /dev/sda1 is mounted; will not make a filesystem here!

In /var/log/partman;
.
.
parted_server: main_loop: iteration 48
parted_server: Opening infifo
/lib/partman/commit.d/50format_ext3: IN: CREATE_FILE_SYSTEM =dev=sda 32256-76889917439 ext2 (sic)
parted_server: Read command: CREATE_FILE_SYSTEM
parted_server: Note =dev=sda as changed
parted_server: Opening outfifo
parted_server: command_create_filesystem(32256-76889917439,ext2)
parted_server: parition_with_id(32256-768889917439)
parted_server: OUT: Timer
parted_server: OUT: 0 (null)
/lib/partman/commit.d/50format_ext3: error_handler: exception with type Timer
parted_server: OUT: 0 (null)
parted_server: OUT: 0 writing per-group metadata
parted_server: OUT: 0 writing per-group metadata
parted_server: OUT: 2 writing per-group metadata
.
.
.

---

### Post by Imre Mehesz on 2006-06-10
hi,

I have the exact same problem. first i downloaded kubuntu (i am sorry but i am that kinda guy :) ) an tried to install it 4-5 times. didn't work (same error message) so i downloaded ubuntu, but a receive the same again...

i have a compaq armada M700 laptop w/ PIII 650MHz, 13GB hdd...

everything was working on the live version ( it even recognized my linksys W45G etc wireless network card!!!) so that's why i am trying to install it for good and leave MS behind :D !

h e l p!

em

---

### Post by Pirulo2003 on 2006-06-25
Hi !!!!!

I had the same problem in a Compaq 1200XL-111 notebook, but i resolved it changing the disk file system option in the bios of this machine from "DOS" to "Other"

---

### Post by dancin_fool on 2006-10-07
I got this message trying to install ubuntu on top of an existing Red Hat Fedora Core 5 install on a Dell Inspiron laptop, and was able to fix it by using fdisk to delete all my partitions prior to installing.

For details see [this other thread]("http://www.ubuntuforums.org/showthread.php?t=235147").

---

