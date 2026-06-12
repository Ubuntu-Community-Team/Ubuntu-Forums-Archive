---
title: "Help with -INIT: Failed to spawn ureadahead main process. No such file or directory"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by windeguy on 2011-02-03
I have an Acer 9410Z laptop that I believe is running the Maverick Meerkat version of Ubuntu Studio. I just did an upgrade using Synaptic. I get to GRUB, but When I try to boot 2.6.35-22 (or the recovery mode or a real time kernel I had installed )  I get the error

INIT: Failed to spawn ureadahead main process. No such file or directory

I then get the Ubuntu Studio splash screen for 2 seconds but then instead of a normal boot I end up in the terminal.  

Any suggestions on how to proceed?

---

### Post by windeguy on 2011-02-04
I tried to use the installation disk in "Rescue" mode. It is not as straight forward as I would have hoped. 

I get to the point where I can choose to try and execute a shell in /dev/sda1 but that does not work. 

If I then choose the option "Execute a shell in the installer environment"  I get to the shell but have no idea how to proceed with the rescue operation.  Any ideas?

---

### Post by windeguy on 2011-02-05
fsck from util-linux-ng 2.17.2

/dev/sdb5: Superblock last mount time is in the future.

	(by less than a day, probably due to the hardware clock being incorrectly set)  FIXED.

/dev/sdb5: clean, 432313/14852096 files, 36015530/59395840 blocks

init: dbus pre-start process (607) terminated with status 2


 * Setting parameters of disc       [180G 
[174G[ OK ]

 * Activating swap...       [180G 
[174G[ OK ]

mount: you must specify the filesystem type

 [31m*[39;49m Cannot check root file system because it is not mounted read-only.

 * Starting Braille terminal driver brltty       [180G 
[174G[ OK ]

 * Activating lvm and md swap...       [180G 
[174G[ OK ]

 * Checking file systems...       [180G fsck from util-linux-ng 2.17.2


[174G[ OK ]

Rather than invoking init scripts through /etc/init.d, use the service(8)

utility, e.g. service S30procps start



Since the script you are attempting to invoke has been converted to an

Upstart job, you may also use the start(8) utility, e.g. start S30procps

start: Unknown job: S30procps

 * Mounting local filesystems...       [180G 
[174G[ OK ]

 * Activating swapfile swap...       [180G 
[174G[ OK ]

 * Cleaning up temporary files...       [180G 
[174G[ OK ]

Rather than invoking init scripts through /etc/init.d, use the service(8)

utility, e.g. service S39ufw start



Since the script you are attempting to invoke has been converted to an

Upstart job, you may also use the start(8) utility, e.g. start S39ufw

start: Unknown job: S39ufw

 * Cleaning up temporary files...       [180G 
[174G[ OK ]

 * Setting sensors limits       [180G 
[174G[ OK ]

Starting polipo: polipo.

speech-dispatcher disabled; edit /etc/default/speech-dispatcher

Raising maximum number of filedescriptors (ulimit -n) to 32768.

Starting tor daemon: tor...

Feb 05 10:08:49.710 [notice] Tor v0.2.1.26 (r7998a25fc4bfbf47). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)

Feb 05 10:08:49.712 [notice] Initialized libevent version 1.4.13-stable using method epoll. Good.

Feb 05 10:08:49.712 [notice] Opening Socks listener on 127.0.0.1:9050

done.

 * Starting the Winbind daemon winbind       [180G 
[174G[ OK ]

Rather than invoking init scripts through /etc/init.d, use the service(8)

utility, e.g. service S50cups start



Since the script you are attempting to invoke has been converted to an

Upstart job, you may also use the start(8) utility, e.g. start S50cups

start: Unknown job: S50cups

saned disabled; edit /etc/default/saned

Rather than invoking init scripts through /etc/init.d, use the service(8)

utility, e.g. service S89cron start



Since the script you are attempting to invoke has been converted to an

Upstart job, you may also use the start(8) utility, e.g. start S89cron

start: Unknown job: S89cron

 * Enabling additional executable binary formats binfmt-support       [180G 
[174G[ OK ]

/etc/rc2.d/S99acpi-support: line 7: /usr/share/acpi-support/power-funcs: No such file or directory

/etc/rc.local: 1: !/bin/sh: not found

vm.swappiness = 10

 * Starting TiMidity++ ALSA midi emulation...       [180G 
[174G[ OK ]

---

### Post by windeguy on 2011-02-07
Since I could not figure out hot to recover from this issue, I decided to start over using 10.04 LTS version.  

I am on my second attempt to get 10.04 LTS working. There is a major bug with the wireless connection.

---

