---
title: "cd rom drive"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by edwin2105z on 2008-07-18
okay i think i really messed up now. when i try to play a cd of a dvd the computer tells me that i have no cd rom drive can some help me.  something happened to it when i was removing plugins or something.

---

### Post by johnnybravo666 on 2008-07-18
Is the drive mounted? And can you view files on the cd in nautilus?

---

### Post by edwin2105z on 2008-07-18
yes it is mounted but what is nautilus is that a program? i tried to view the song on the rhythmmusic player provided by ubuntu but nothing comes up.

---

### Post by johnnybravo666 on 2008-07-18
Nautilus is the gnome file manager. Open up the file manager, browse to where the cdrom is mounted (/media/cdrom0 on my computer) and see if you can see the files on the CD there.

---

### Post by soxs on 2008-07-18
> **edwin2105z said:**
> okay i think i really messed up now. when i try to play a cd of a dvd the computer tells me that i have no cd rom drive can some help me.  something happened to it when i was removing plugins or something.

What did you remove?
And what does not work?
Does this apply to any cds/dvds or only with special ones(VCD/Movie DVDs?)

---

### Post by edwin2105z on 2008-07-18
tryed looking for it but i'm new to ubuntu and i have no idea how to find it can you tell me how to get there

---

### Post by johnnybravo666 on 2008-07-18
Make sure the CD is in the drive, then open a terminal and type ```
mount
```. This will give a list of all mounted devices and where they are mounted. Post the results here

---

### Post by edwin2105z on 2008-07-18
> **johnnybravo666 said:**
> Make sure the CD is in the drive, then open a terminal and type ```
mount
```. This will give a list of all mounted devices and where they are mounted. Post the results here


edwin2105z@edwin2105z-desktop:~$ mount
/dev/sde1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/edwin2105z/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=edwin2105z)
edwin2105z@edwin2105z-desktop:~$

---

### Post by johnnybravo666 on 2008-07-18
Your cdrom is not mounted. Post the results of this command ```
cat /etc/fstab
```

---

### Post by edwin2105z on 2008-07-18
> **johnnybravo666 said:**
> Your cdrom is not mounted. Post the results of this command ```
cat /etc/fstab
```

edwin2105z@edwin2105z-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2c10b2cc-d6ce-4fbc-9f0d-8151bf139b0b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=752cd084-e6bb-4b30-b7a0-4d2e8b498801 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
edwin2105z@edwin2105z-desktop:~$

---

### Post by johnnybravo666 on 2008-07-18
I'm not sure why the cdrom is not mounting automatically but you can mount it with ```
sudo mount /media/cdrom0
``` from a terminal

---

### Post by bsmith1051 on 2008-07-27
I have the same problem (and the same fstab) and when I try to mount an Audio CD it reports, "wrong fs type, bad option, bad superblock on /dev/scd0"

---

