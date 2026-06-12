---
title: "HELP!  Migrate working single disk system to existing RAID array using disk UUIDs"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by nstenz on 2010-08-01
I had done a new lucid install to a 1 TB RAID 1 array using the alternate CD a few weeks back.  I messed up that system trying to some hardware working that lucid doesn't have drivers for yet, so I gave up on it and reinstalled to a single 80 GB disk that I now want to move over to the RAID array.

I moved all of the existing files on the array to a single folder, then copied all of the folders from the 80 GB disk over to the array with permissions and symlinks (minus the contents of /proc and /sys, which I created empty).

These are the commands I used:
> p -a -d -R -v -t /media/raid_array /b*
cp -a -d -R -v -t /media/raid_array /d*
cp -a -d -R -v -t /media/raid_array /e*
cp -a -d -R -v -t /media/raid_array /h*
cp -a -d -R -v -t /media/raid_array /i*
cp -a -d -R -v -t /media/raid_array /l*
cp -a -d -R -v -t /media/raid_array /mnt
cp -a -d -R -v -t /media/raid_array /opt
cp -a -d -R -v -t /media/raid_array /root
cp -a -d -R -v -t /media/raid_array /sbin
cp -a -d -R -v -t /media/raid_array /selinux
cp -a -d -R -v -t /media/raid_array /srv
cp -a -d -R -v -t /media/raid_array /tmp
cp -a -d -R -v -t /media/raid_array /usr
cp -a -d -R -v -t /media/raid_array /v*
mkdir /media/raid_array/sys
chmod 755 /media/raid_array/sys
mkdir /media/raid_array/proc
chmod 555 /media/raid_array/proc


After copying everything, I replaced the fstab that I copied over from the 80 GB disk with the fstab from my backup of the RAID array, shut down, and unplugged the 80 GB disk.  When I try to boot from the array, I get an error that the UUID that's in fstab can't be located (/dev/disk/by-uuid/412d...).

*mdadm --detail --scan* gives me UUID=689a..., and *blkid* shows UUID=689a... for both of the raid members, too.

I tried to change fstab to use the 689a... for root, but when I try to boot, it's still trying to open /dev/disk/by-uuid/412d...

So then I booted from the single disk again and chrooted into the array, then ran *update-initramfs -u*.  I got 3 "grep: /proc/modules: No such file or directory" errors, and "cat: /proc/cmdline: No such file or directory"- so I created directory /proc/modules, created an empty file /proc/cmdline, and ran the initramfs update again.  Then I tried to shut down, which hung (probably because I was doing all of this from a terminal window in Gnome), so I killed the power after a couple of minutes.

It's still trying to use /dev/disk/by-uuid/412d... to boot.

What am I missing?  I assume I just have to change the UUID to mount as root, but I don't know how.  Help!

---

### Post by nstenz on 2010-08-01
I just looked in /dev/disk/by-uuid, and I see 412d... is a symlink to /dev/sda1- which is one of the array members.  Obviously that won't work as the root filesystem- I need the array.

I don't see 689a... at all in there (what mdadm gives as the UUID for the array).  I **do** see fa68... pointing to /dev/md0, and that's the UUID blkid shows for /dev/md0 as well.

Do I need to get rid of the fa68... symlink and create a 689a... one pointing at /dev/md0 instead?  I don't really know what I'm doing here, so I don't want to mess with it anymore without explicit instructions.

---

### Post by nstenz on 2010-08-15
OK- can anybody point me toward someplace where I can find some more technical users knowledgeable about the boot sequence who would be willing to help me out?

---

