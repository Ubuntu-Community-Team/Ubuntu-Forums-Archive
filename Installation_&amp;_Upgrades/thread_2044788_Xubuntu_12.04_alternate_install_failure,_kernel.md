---
title: "Xubuntu 12.04 alternate install failure, kernel"
date: 2012-08-20
forum: Installation &amp; Upgrades
---

### Post by sippyCUP on 2012-08-20
Hi all,

Just got Ubuntu 12.04 up and running on my main box, now I'm trying to install Xubuntu 12.04 on my HP Mini netbook.

Created a live usb thumbdrive with startup disk creator, I manually set up my partitions (large ext4 root, 2gb swap, and I left the HP recovery partition alone at the end of the disk).

Ubiquity crashed while I was noodling around my the webcam feed for the user profile. Seems like it's a known bug, I found mention of it on forums, and it didn't crash immediately so I tried it a few more times. The next two times, installer crashed right before I was able to get to the create user profile screen, so I decided to move on to the alternate iso.

Downloaded that, created alternate install usb drive, got on with my install. Now on installing the base components, it crashes seemingly on installing the kernel

I've attached a photo of the terminal outpot. I think there is a log file too, I'm going to try to pull that out and post it now. I checked the MD5sum on the iso I downloaded and it matches the Ubuntu website's.

Any ideas? I'm doing my darndest to make my house an Ubuntu one but I'm running into installation issues at an alarming rate :p

Here's the final 30 or so lines from the syslog:

> Aug 20 04:42:25 in-target: Unpacking wireless-regdb (from .../wireless-regdb_2011.04.28-1ubuntu3_all.deb) ...
Aug 20 04:42:26 in-target: Selecting previously unselected package crda.
Aug 20 04:42:26 in-target: Unpacking crda (from .../crda_1.1.2-1ubuntu1_i386.deb) ...
Aug 20 04:42:26 in-target: Selecting previously unselected package linux-image-3.2.0-23-generic.
Aug 20 04:42:26 in-target: Unpacking linux-image-3.2.0-23-generic (from .../linux-image-3.2.0-23-generic_3.2.0-23.36_i386.deb) ...
Aug 20 04:42:27 in-target: Done.
Aug 20 04:42:52 in-target: Selecting previously unselected package linux-firmware.
Aug 20 04:42:52 in-target: Unpacking linux-firmware (from .../linux-firmware_1.79_all.deb) ...
Aug 20 04:42:52 in-target: dpkg: error processing /media/cdrom//pool/main/l/linux-firmware/linux-firmware_1.79_all.deb (--unpack):
Aug 20 04:42:52 in-target:  trying to overwrite '/lib/firmware/brcm/bcm43xx-0.fw', which is also in package firmware-brcm80211 0.28+squeeze1
Aug 20 04:42:52 in-target: No apport report written because MaxReports is reached already
Aug 20 04:42:52 in-target: dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Aug 20 04:42:52 in-target: Selecting previously unselected package linux-image-generic.
Aug 20 04:42:52 in-target: Unpacking linux-image-generic (from .../linux-image-generic_3.2.0.23.25_i386.deb) ...
Aug 20 04:42:53 in-target: Selecting previously unselected package linux-generic.
Aug 20 04:42:53 in-target: Unpacking linux-generic (from .../linux-generic_3.2.0.23.25_i386.deb) ...
Aug 20 04:42:53 in-target: Errors were encountered while processing:
Aug 20 04:42:53 in-target:  /media/cdrom//pool/main/l/linux-firmware/linux-firmware_1.79_all.deb
Aug 20 04:42:53 in-target: E: Sub-process /usr/bin/dpkg returned an error code (1)
Aug 20 04:42:55 in-target: Reading package lists...
Aug 20 04:42:55 in-target: 
Aug 20 04:42:55 in-target: Building dependency tree...
Aug 20 04:42:55 in-target: 
Aug 20 04:42:55 in-target: You might want to run 'apt-get -f install' to correct these:
Aug 20 04:42:55 in-target: The following packages have unmet dependencies:
Aug 20 04:42:55 in-target:  linux-headers-generic : Depends: linux-headers-3.2.0-23-generic but it is not going to be installed
Aug 20 04:42:55 in-target:  linux-image-generic : Depends: linux-firmware but it is not going to be installed
Aug 20 04:42:55 in-target: E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
Aug 20 04:42:55 base-installer: error: exiting on error base-installer/kernel/failed-install
Aug 20 04:43:17 init: starting pid 298, tty '/dev/tty2': '-/bin/sh'
Aug 20 04:43:33 kernel: [ 3275.295818] atkbd serio0: Unknown key pressed (translated set 2, code 0x92 on isa0060/serio0).
Aug 20 04:43:33 kernel: [ 3275.295833] atkbd serio0: Use 'setkeycodes e012 <keycode>' to make it known.
Aug 20 04:43:34 kernel: [ 3275.327591] atkbd serio0: Unknown key released (translated set 2, code 0x92 on isa0060/serio0).
Aug 20 04:43:34 kernel: [ 3275.327602] atkbd serio0: Use 'setkeycodes e012 <keycode>' to make it known.
Aug 20 04:45:25 kernel: [ 3386.592726] mount: sending ioctl 5310 to a partition!
Aug 20 04:45:25 kernel: [ 3386.592737] mount: sending ioctl 5310 to a partition!

Thanks,
Eric

---

### Post by 2F4U on 2012-08-20
Are you sure that the downloaded iso file of the alternate install image is ok? Did you verify the checksum? How did you create the usb install media?

---

### Post by sippyCUP on 2012-08-20
I checked the md5sum of the downloaded ISO against the one on the ubuntu website, they match. I don't really have a way of checking the ISO checksum against the USB drive.

I created the USB bootable drive using startup disk creator in mint 9.

---

### Post by sippyCUP on 2012-08-21
Went ahead and installed 11.10, then upgraded to 12.04. Pretty inelegant solution but it worked.

---

### Post by Bucky Ball on 2012-08-21
Yea, not great and didn't really solve the issue but you're at 12.04 so good. Direct release upgrades can be problematic, though, in unexpected ways. Having said that, could you mark as solved from Thread Tools if you're satisfied with this result, please, and start new threads for any consequent probs? ;)

For future reference; torrent is preferred, fastest, most reliable way to get the ISO. Checksum dealt with during download and doesn't tie up servers too severely. Links are on Xubuntu download page.

---

