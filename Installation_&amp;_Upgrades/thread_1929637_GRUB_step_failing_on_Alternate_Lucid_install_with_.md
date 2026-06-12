---
title: "GRUB step failing on Alternate Lucid install with RAID1"
date: 2012-02-22
forum: Installation &amp; Upgrades
---

### Post by gmoore777 on 2012-02-22
Trying to install LucidLynx 10.04.4 via the Alternate CD along with
trying to get RAID1 for my two hard drives.

I am following these instructions:
[https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)

The installation fails at the point of: 
"Install the GRUB boot loader on a hard disk".

If I hit <CTL><<ALT><F2>, I can get to the console, to enter commands.
If I hit <CTL><ALT><F4>, the /var/log/syslog is being tailed.
<CTL><ALT><F1> is the Alternate CD "GUI" install and currently I'm at the
screen where I can attempt to install Grub or to move on down the list.

When I get to the Grub-like screen asking me for device names,
it is already populated with these 2 device names: "/dev/sda /dev/sdb".
This is correct in my eyes, but evidently not.

In desperation, I have tried these single choices as well:
 /dev/sda, /dev/sdb, /dev/sda1, /dev/sda2, /dev/sdb1, /dev/sdb2, 
 /dev/md, /dev/md0, /dev/md1, /dev/disk/by-uuid/<32-digit UUID number>

All fail.
I've Googled around and am tired as well as not smart enough to
understand all this RAID stuff. (first time doing this)

I've blanked out both partitions in both drives using the LiveCD
and have attempted the Alternate CD installation again, but
with the same exact outcome.
So I feel like I've followed the instructions perfectly and since
this is version 10.04.4, all the bugs and kinks must have been worked
out by now and it must be something unique to my hardware. Which is unfortunate for me.

In the tty2 screen, if i run `mdadm -D /dev/md0`, it prints out
a bunch of stuff, namely at the bottom it lists /dev/sda2 and
/dev/sdb2 as being "active sync".
Ditto for /dev/md1, it shows, /dev/sda1 and /dev/sdb1 as being 
"active sync".

Yes, there are multitude of errors in the tty4 syslog window.
Too many for me to type, but I'll type a few:

grub-installer: no mapping exists for "md0"
grub-installer: Auto-detection of a file system module failed
Please specify the module with the option "--modules" explicitly.

So hopefully someone can tell me what to put with the "--modules" flag
and then I am hoping that when that GRUB screen comes up, that
it will take options and the device names.

There is no "grub-install" binary in the PATH.
There is this /usr/bin/grub-installer 1299 line Shell script that
the Alternate Installer is running for this Grub step.
I could edit this file if I knew what editor to use, as there is no `vi` available either.

Thank you.

---

### Post by gmoore777 on 2012-02-22
In the tty console window, I just ran this:

chroot /target grub-install --no-floppy --force --modules="raid mdraid" /dev/sda

(it seems everything is under the /target mount)


Numerous errors occurring more than once:

 /proc/devices: fopen failed: no such file or directory

 Is device-mapper driver missing from kernel?

 Failed to set up list of device-mapper major numbers

 /usr/sbin/grub-probe: error: no mapping exists for 'md0'

 You attempted a cross-disk install, but the filesystem containing  
 /boot/grub does not support UUIDs.

---

### Post by gmoore777 on 2012-02-26
So after reading these links:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/701351](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/701351)
[http://forums.funtoo.org/viewtopic.php?id=467](http://forums.funtoo.org/viewtopic.php?id=467)

it suggests that any CD that is using GRUB with a version less
than 1.99, that GRUB will not install when using RAID
since GRUB can't handle the mdadm metadata versions at 1.0 or higher.

This release note from GRUB 1.99,
[http://lists.gnu.org/archive/html/grub-devel/2011-05/msg00032.html](http://lists.gnu.org/archive/html/grub-devel/2011-05/msg00032.html)
mentions this fix:
    * Support 1.x versions of mdadm metadata.
and that is the fix that I supposedly need.

On a different machine that I have Lucid Lynx running, I see that
grub-common and grub-pc is at version 1.98-1ubuntu13.

I also see on the Lucid Lynx 10.04.4 Alternate CD, that the
same 2 packages are at the same 1.98-1ubuntu13 version.

So even though GRUB 1.99 came out in May 2011, the LucidLynx
platform and Alternate CD, (with a build date of Feb 14, 2012)
are still using GRUB that was built prior to May 2011 (10+ months ago)
(i'm a bit disappointed with this since LucidLynx is the latest LTS
version that is current and should be better supported than this.)

Coincidently today, I notice the PrecisePangolin Alternate CD, has
finally been built with a size less than 700 MB, such that I can
burn this on a CD (not a DVD) and that my old computer can now
read this and run an installation from it.

I successfully installed PrecisePangolin (and GRUB) with the same 
exact RAID instructions that I mentioned in comment #1.

The grub version on this PrecisePangolin installation is 1.99-14ubuntu2,
which is supposedly the solution to this whole situation.

I would have liked have gotten this to work with LucidLynx 10.04.4
out of the box, but this is a reasonable alternative since PrecisePangolin
is the next LTS, and is almost ready. (Beta 1 in 3 days on March 1)

---

