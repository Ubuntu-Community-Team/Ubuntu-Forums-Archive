---
title: "Software RAID and Upgrade from 6.06 to 6.10"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by ezaton on 2006-10-29
Hi all.
I have passed through this forum yesterday, searching for a possible cause for a problem I have had. 
The theme was almost well known - after upgrade from 6.06 to 6.10 the system won't boot. Lilo (I use Lilo, not Grub) would load the kernel, and after a while, never reachine "init" the system would wait for something, I didn't know what.

I tried disconnecting USB, setting different boot parameters, even virified (using the kernel messages) that disks didn't replace their locations (and they did not, although I have additional IDE controller). Alas, it didn't seem good.

The weird thing is that the during this wait (there was keyboard response, but the system didn't move on...), the disk LED flashed in a fixed rate. I though it might have to do with RAID rebuild, however, from live-cd, there was no signs of such a case.

Then, on one of the "live-cd" boots, accessing the system via "chroot" again, I have decied to open the initrd used by the system, in an effort to dig into the problem. 
Using the following set of commands did it:
cp /boot/initrd.img-2.6.17-10-generic /tmp/initrd.gz
cd /tmp && mkdir initrd.out && cd initrd.out
gzip -dc ../initrd.gz | cpio -od

Following this, I've had the initrd image extracted, and I could look into it. Just to be on the safe side, I have looked into the image's /etc, and found there mdadm/mdadm.conf file.
This file had different (wrong!) UUIDs for my software RAID setup (compared with "mdadm --detail /dev/md0" for md0, etc).
I have located the origin of this file to be the system's real /etc/mdadm/mdadm.conf, which was originated a while ago, before I've made many manual modifications (changed disks, destroyed some of the md devices, etc). I have fixed the system's real /etc/mdadm/mdadm.conf file to reflect the correct system, and recreated the initrd.img file for the system (now with the up-to-date mdadm.conf). Updated Lilo, and the system was able to boot correctly this time.

The funny thing is that even using the previous kernel, which had its initrd.img built long ago, and which worked fine for a long while failed to complete the boot process altogether using the upgraded system. 

My system relevant details:
/dev/hda+/dev/hdc -> /dev/md2 (/boot), /dev/md3 
/dev/hde+/dev/hdg -> /dev/md1 
/dev/md1+/dev/md1 -> LVM2, including the / on it
Lilo is installed on /dev/hda and /dev/hdc altogether.

I want to share this knowledge here, so that the next person with such a weird system setup (and working well, too) would know what to do.

A copy of this post can be found in my blog as well, at 
[http://www.tournament.org.il/run/index.php?/archives/106-Upgrading-Ubuntu-6.06-to-6.10-with-software-non-standard-RAID-configuraion.html](http://www.tournament.org.il/run/index.php?/archives/106-Upgrading-Ubuntu-6.06-to-6.10-with-software-non-standard-RAID-configuraion.html)

---

### Post by dik666 on 2006-10-30
Hi,

I had the same problem trying to upgrade to 6.10.  I did a fresh install of Edgy last weekend.  After using apt-get to install mdadm my system won't boot.  It seems to hang after setting up the USB ports.  The harddrive light flashes rapidly but the system never boots.  If I then uninstall mdadm the system will boot as normal but then of course I don't have software raid anymore.

Has anyone successfully set up software raid on Edgy yet?

dik666

---

### Post by teknologist on 2006-10-30
Same problem here with a Dapper setup using LVM2 and Raid1 on /
(Used the official wiki on LVM2+raid to setup at the time I installed Dapper).

Exact same diagnosis as you guys. blinking IDE led at stable rate and boot stop at mdadm.

Weird thing is that when I boot the same machine with my old 2.6.15-27-686 kernel it works like a charm.

FS layout:

LVM2+raid1 (XFS) md0 for /

---

### Post by dallingham on 2006-10-30
I've had a similar problem. After upgrading to 6.10, my RAID 1 setup (2 SATA drives) would hang for a long period of time on boot. After about 7 or 8 minutes, the boot would complete. However, the system was highly unstable.

I rebuilt the system with a clean install, and it would never allow me to boot from a RAID 1 setup. I eventually had to rebuild the system without RAID 1, and the system now works.

---

### Post by teknologist on 2006-10-30
Just to be clear the problem is after upgrading that Dapper to Edgy....
Anyway averythings works perfectly when I stayl with the old 2.6.15-27 ubuntu kernel...

The problem has definitely something to do with the new Edgy kernel 2.6.17 generic, not the wholde Edgy distro itself...

---

### Post by teknologist on 2006-10-31
Just solved the problem!

I did a mdadm --detail --scan /dev/md0 and replaced the UUID in my existing /etc/mdadm/mdadm.conf by the one from the scan output (they were different)

Then I did a dpkg-reconfigure mdadm...it recreated the initrd.

rebooted and now it would stop further for a couple of minutes at EVMS... 

I removed evms from startup services ( I don't need it, I just need lvm and raid) and everyhting works like a charm!!


Hope it helps you out guys because the solution of reinstalling clean is not a solution for me...never has been... ;-)

Cheers!

---

### Post by rootchick on 2006-11-09
I had a similar problem with a fresh install of Xubuntu 6.10 with RAID1 and grub.  After the installation the system wouldn't boot, saying something about /dev/hda1 not existing.  The problem was that grub was trying to boot from /dev/hda1 instead of /dev/md0.  I edited the entry in the grub boot menu, which allowed me to boot, but that doesn't get saved permanently, so I had to edit /boot/grub/menu.lst to change all entries of /dev/hda1 to /dev/md0 to permanently fix the problem.  Just thought I'd record it for posterity.  ;)

---

### Post by simidau on 2006-11-29
This thread saved me so much pain. For some reason it changed the uuids and a simple dpkg-reconfigure mdadm in a chroot from boot disk brought me back to life.

Cheers
Simon

---

