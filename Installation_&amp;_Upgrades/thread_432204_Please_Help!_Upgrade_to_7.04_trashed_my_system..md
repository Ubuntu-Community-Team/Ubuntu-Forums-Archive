---
title: "Please Help! Upgrade to 7.04 trashed my system."
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by john.wheeler on 2007-05-03
OK, so I was tempting fate: I kicked off an upgrade from Ubuntu 6.10 to 7.04 and had to go home before it finished. The result this morning....my PC won't start, even in recovery mode.

This is what I did:

1. Closed all running apps
2. Launched the updater
3. Downloaded the 718MB of files, and saw the start of the install. I had to confirm the overwrite of one file (can't remember which file unfortunately).
4. After a 20 minutes of installation I left my laptop PC. In a tragic fit of optimism, and unwarranted eco-friendliness, I unplugged the power adapter.
5. Something went wrong and the installation got stuck until my battery expired.

The situation now:

1. My boot menu doesn't show the updated kernel, so I tried to start up my previous install (v 6.10). 
2. The Ubuntu splash screen has been updated, but the progress bar stops almost immediately.
3. I tried starting in recovery mode, and saw that progress stops at the message "waiting for root file system". Sounds bad...

I re-booted into Windows XP (no, I will never turn to dark side!), which I had kept "just in case". Using "explore2fs" I am able to view the Linux partitions, which seem intact.

Could anyone please offer any advice on how I should proceed? I really don't want to have to do a fresh install - it took me a long time to get the system to its previous state.

If only I'd waited to finish the installation <sigh>.

Any ideas would be very much appreciated.

Best regards,

John Wheeler

---

### Post by john.wheeler on 2007-05-04
After upgrading my 6.10 installation to 7.04, my PC no longer boots

The boot seems to freeze immediately after displaying the Ubuntu splash screen. AFter about 4 minutes, it drops into some kind of built-in shell that displays the following:

-------------------------
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Buildt in shell (ash)

/bin/sh: can't access tty; job control turned off

(initramfs)

-------------
At the (initramfs) prompt I can enter a set of Linux commands and can see a file system, which appears to be a RAM disk.

At the root of the file system, there is an "init" command which I ran. This caused a reboot and after waiting the 4 minutes as before, I got the following output:

-----------------------------

mount: Mounting none on /sys failed : Device or resource busy
mount: Mounting none on /proc failed : Device or resource busy

ndevd[7815] init_udevd_socket: bind failed : Address already in user
error initializing udevd socket
ndevd[7815] main: error initializing udevd socket

Check root = bootarg cat /porc/cmdline
or missing modules, divces : cat /pro/modules ls/dev

ALERT! /dev/sda4 does not exist. Dropping to a shell!

/bin/sh: can't access tty; job control turned off

(initramfs)

------------------------

The fact that it says that it can't find /dev/sda4 is worrying - this is my primary Linux partition. I have heards that 7.04 has changed the way partitions are handled.

Any ideas how to proceed?

Your help is much appreciated!

John wheeler.

---

### Post by john.wheeler on 2007-05-04
After upgrading my 6.10 installation to 7.04, my PC no longer boots

The boot seems to freeze immediately after displaying the Ubuntu splash screen. AFter about 4 minutes, it drops into some kind of built-in shell that displays the following:

-------------------------
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Buildt in shell (ash)

/bin/sh: can't access tty; job control turned off

(initramfs)

-------------
At the (initramfs) prompt I can enter a set of Linux commands and can see a file system, which appears to be a RAM disk.

At the root of the file system, there is an "init" command which I ran. This caused a reboot and after waiting the 4 minutes as before, I got the following output:

-----------------------------

mount: Mounting none on /sys failed : Device or resource busy
mount: Mounting none on /proc failed : Device or resource busy

ndevd[7815] init_udevd_socket: bind failed : Address already in user
error initializing udevd socket
ndevd[7815] main: error initializing udevd socket

Check root = bootarg cat /porc/cmdline
or missing modules, divces : cat /pro/modules ls/dev

ALERT! /dev/sda4 does not exist. Dropping to a shell!

/bin/sh: can't access tty; job control turned off

(initramfs)

------------------------

The fact that it says that it can't find /dev/sda4 is worrying - this is my primary Linux partition. I have heards that 7.04 has changed the way partitions are handled.

Any ideas how to proceed?

Your help is much appreciated!

John wheeler.

---

### Post by noushi on 2007-05-04
hi John,

i had a similar problem with dapper, that got resolved with feisty.

my conf is an intel dual core 2.4ghz w/ sata hd and 1go ram.
the kernel started booting and then stopped really soon around slash mounting.
it dropped me w/ a shell later.

actually i could see the kernel messages because i removed "splash" and "quiet" options manually in the grub menu.
i think the problem is w/ acpi and smp (dual core) functionality.
the i386 kernel worked better than the generic one (for the same kernel version)

after i booted, i upgraded to feisty, and it works better, alas the machine is giving me headaches w/ spurious hangs and/or reboots both w/ linux and losedows... :(

you could get better help if you dumped your hw configuration and/or a log of something (by booting a livecd for ex. ;)

regards,
noushi

---

### Post by Dominus on 2007-05-04
Hi all,

this item has appeared a lot, maybe [this thread](http://ubuntuforums.org/showthread.php?t=424398) will help you.

I've the same problem on upgrade but I couldn't solve yet. :( 

Sorry for my poor english!!!

---

### Post by monaleilani on 2007-05-15
I had the exact same problem as this. I updated EE to FF. I tried changing hda1 to sda1 in grub, and that seemed to work.. Almost. Right now I get the backsplash and a cursor, but that's it. Oh well, back to the drawing board.

---

