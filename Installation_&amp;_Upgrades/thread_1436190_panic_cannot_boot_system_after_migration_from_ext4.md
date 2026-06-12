---
title: "panic: cannot boot system after migration from ext4 down to ext3"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by semi-newbie on 2010-03-22
I have been able to get most of the way through the process of changing from using ext4 back to using ext3, but something is not quite right so my system does not boot properly.

I have a system that was running Karmic Koala 9.10 as a server (no graphical environment).  I had two drives using RAID1 with LVM on top, where the logical volumes of oldvg (old volume group) were using mostly ext4.  /boot was not part of the RAID: it's on a separate physical drive and uses ext2.

I recently added two more drives and used RAID1 and LVM, and made all lv partitions (/, /usr, /var, /tmp, /opt, /home, /srv) ext3.  I used rsync to duplicate the contents onto the logical volumes of newvg (new volume group).  I was careful with rsync's option switches, and this part seems to be fine.

I also edited (the new) /etc/fstab and changed the UUIDs of the seven mount points to point to the logical volumes that are part of newvg instead of oldvg, and added new entries to (the new) /boot/grub/menu.lst to refer to newvg in addition to those that I left around to refer to oldvg.

This wasn't sufficient: rebooting here failed, but I went in with a rescue disk, and first updated /boot/grub/device.map to include the new physical drives.  I then mounted all the new logical volumes, mounted boot also at its proper place, and entered a chroot of the new system as it should be mounted.  Once there, (and after making a backup of /boot) I ran "update-initramfs -k all -c" to rebuild the initrd images that were stored on /boot.  Finally, I also edited /etc/mtab so that the two entries that referred to oldvg now refer to newvg instead.

Now, the machine begins to boot from newvg, but the console text includes messages like:

mount: mount point /var/run does not exist
mountall: mount /var/run [642] terminated with status 32
mountall: Filesystem could not be mounted: /var/run
mount: mount point /var/lock does not exist
mountall: mount /var/lock [643] terminated with status 32
mountall: Filesystem could not be mounted: /var/lock
mount: mount point /var/run does not exist
mountall: mount /var/run [645] terminated with status 32
mountall: Filesystem could not be mounted: /var/run
mount: mount point /var/lock does not exist
mountall: mount /var/lock [646] terminated with status 32
mountall: Filesystem could not be mounted: /var/lock

and a bit later,

init: mountall main process (637) terminated with status 4
Mount of root filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.

now, at this shell if I type mount, I see:

/dev/mapper/newvg-root on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/mapper/newvg-var on /var type ext3 (ro)

cat /etc/mtab reveals very similar data, and no other entries (e.g., /dev/mapper/newvg-usr, /dev/mapper/newvg-tmp).

I am actually confused as to why there are only entries for /root and /var in /etc/mtab, actually, instead of entries for all of the main mount points.  I am thinking it must be part of the boot staging process, because there are entries for newvg-usr, newvg-tmp, etc. in /etc/fstab.

sfdisk --list reveals all physical drives are visible and fine.
mdadm --detail /dev/md* reveals all raid drives are visible and fine.

When I type any of pvdisplay, vgdisplay, or lvdisplay, I get

File descriptor 8 left open
  Locking type 1 initialisation failed.

In fact, even if I run lvm, I get a similar error:

root@machine:~# lvm
File descriptor 8 left open
lvm> help
  Locking type 1 initialisation failed.
lvm> help
  Locking type 1 initialisation failed.

However, if I go back to the rescue cd, pvdisplay, vgdisplay, and lvdisplay do show that all of the partitions from both the old and new volume groups are available.

So, I'm stuck at this point, not knowing how to complete fixing my system so that it boots properly.  Can someone advise me how to proceed?

---

### Post by semi-newbie on 2010-03-25
I was able to solve this problem by doing a few things:
- ensuring that /etc/mdadm/mdadm.conf specified ARRAY /dev/md0 for my new raid1 pair (I disconnected the old drives)
- reboot, reaching busybox with my root partition up but with /var missing despite it supposedly being there
- remounting all file systems that were supposed to be present in the end as read-write
- not trusting the /etc/mtab contents, I removed /etc/mtab and symlinked it to /proc/mounts
- I then removed /boot/initrd-* (I had a backup of these) and invoked update-initramfs -k all -c.

This appears to have restored full boot functionality.  I might try to switch back to a normal /etc/mtab later, though some people apparently leave it symlinked to /proc/mounts all the time.

---

