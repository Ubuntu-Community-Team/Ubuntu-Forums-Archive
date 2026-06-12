---
title: "upgrading 9.04"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by MikRose on 2009-11-25
I have been with Ubuntu since 5.1 and have used CDs mailed from Linux for successive upgrades since then. Six months ago I installed 9.04 with no problems since.  Yesterday I decided to upgrade to 9.1 using the Upgrade Manager.

Before upgrading I checked my version with command line and it was 9.04.

After installing all updates to 9.04 I upgraded from 9.04 to 9.1.
All went well until the Restart, then my terminal screen showed:

init: spreadsheet main process (2607) terminated in status 1
mountall: /process: unable to mount: Device or resource busy
mountall: /process/self/mountinfo: No such file or directory
mountall: root file system isn't mounted
init: mountall main process (2608) terminated with status 1
General error mounting file systems
A main shell will now be started
Control-D will terminate this shell and re-try
root@mik-desktop:~#

I have read multiple posts which were identical to my terminal results (although the process numbers are different), but nothing suggested will work.  The suggestion I saw the most is:

"Boot into a Live session of Ubuntu and then open a terminal and mount your installed Ubuntu partition. (I'll use /dev/sda1 as your root.)

# mkdir /mnt/ubuntu
# mount /dev/sda1 /mnt/ubuntu
# mount -t proc none /mnt/ubuntu/proc
# mount -o bind /dev /mnt/ubuntu/dev
# chroot /mnt/Ubuntu
# apt-get update
# apt-get upgrade"

But the results are the same terminal message listed above. 

I can use Live CD from 9.04 or fresh install, but wondered if there is a way to correct the mountall and missing files.

---

### Post by amittal on 2009-11-28
Hi All,

Even I upgraded recently and I got the similar messages as above though my process numbers are 2633 and 2634.

Any pointers to solve this issue?

Regards,
-Amit

---

