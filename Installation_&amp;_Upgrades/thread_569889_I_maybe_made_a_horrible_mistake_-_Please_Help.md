---
title: "I maybe made a horrible mistake - Please Help"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by acaby on 2007-10-07
I was a Die-Hard Windows Freak. Started with old DOS, Win3.1, Win95 and  Win98SE. UNTIL I found Linux back in Feb. Started with most of the distros until I found Ubuntu 7.04, Liked it and stuck with it. Then one Day I was Surfing the net and ran across openSUSE 10.3. Since I had a spare 20G HD (Slave) I was using for File storage in the IDE format (I have Win98SE and Ubuntu 7.04 on disk 1) I Gparted it 50/50 and installed openSUSE 10.3 on the last half of disk 2.

It wrote a different BOOT to my MBR (openSUSE GUI BOOT)

No problems here as every OS was listed and booted fine at start-up and All 3 OS's work Fine.
BUT openSUSE (on sdb2) would not read the 10Gig 1st partition (sdb1) It reads the partitions of HD1 (sda1,sda2) Ok with proper root access
This is where I start to really get confused:confused:
So
[B][COLOR="Red"]I look at the etc/fstab on partition 2 of 2nd HD (openSUSE) Empty??
I look at the etc/fstab on partition 2 of 1st HD (Ubuntu 7.04) ALSO Empty????(Partition 1 is Win98SE)[/COLOR][/B]
AND the Mount is REALLY screwed up (Came from mount hda2 Ubuntu 7.04)
-----------------------------------------------------------------------
:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sdb1 on /media/sdb1 type vfat (rw,utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
-------------------------------------------------------------------
I realize this is NOT Forum for openSUSE BUT I am concerned about my Ubuntu 7.04 installation and I cannot understand why it is working with the screwed up mount and the empty fstab's

Thanks,
Arthur

---

### Post by malangaman on 2007-10-08
Arthur,
Sorry, I can't help you with your problem. But the title of your post attracted my attention as I was browsing through the forum.
How much time did you invest in the Open Suse installation?

---

