---
title: "Boot problems after regular update Natty programmes"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by edfast on 2011-06-10
Haven't found anyone on the forums with a similar problem, so starting this thread for advice. I have been happily running natty/unity on a macbook 2,1 for a couple of months now. Occasional glitches but no major issues. After last regular update (June 9) I had difficulties shutting down, so I forced the system down (maybe this was a mistake) through an 'American reboot' as it's known in Europe, ie; by pulling the plug. No processes were active that I could detect. On restart, I get the message 'no bootable device, pls insert boot disc' and have tried since to go via various acrobatics in the terminal of the disk-booted system to try and get at what's on the hard drive, but no such luck. I have tried to mount the drive through the terminal on the CD, but the unit is not found - but I am not quite sure if I enter the correct commands, being a Ubuntu newbie.  So what are my options now? Is there any known way by which I can restore my original system, rescue the drive or even just retrieve my data (not much)? Most of the programmes were canonical, in addition I ran Skype beta, Gmediaplayer, PlayDownloader through Java, Spotify preview, an OpenVPN utility that I never got to working properly. The last update installed updates for Chrome and possibly Skype, other than that I'm not quite certain. Ideas? Help someone?!
Cheers! P.

---

### Post by edfast on 2011-06-10
I'd like to add and clarify. I tried to mount my SSD from the terminal of the live-install CD. This is what was returned:

ubuntu@ubuntu:~$ mount /dev/hda
mount: can't find /dev/hda in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ mount /dev/hdb
mount: can't find /dev/hdb in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
ubuntu@ubuntu:~$ mount /dev/sda
mount: can't find /dev/sda in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ find sda
find: `sda': No such file or directory
ubuntu@ubuntu:~$ mount sda
mount: can't find sda in /etc/fstab or /etc/mtab

It seems it doesn't see my hard drive at all? Yet, when I tentatively go ahead with the install process, it correctly identifies the drive as /dev/sda - and then the name of the device. Why not from the terminal? I would prefer to repair rather than fresh install, for all the usual reasons...

---

