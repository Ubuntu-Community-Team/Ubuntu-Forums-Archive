---
title: "Help: GRUB problems under Hardy: no /dev/hda anymore?"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by KeesM on 2008-04-26
Hi all,

Please note: I am barely more than a beginner...

I just updated to Hardy, in which process my menu.lst file was changed. I tried to correct it, however can not get GRUB to update. My normal process is: update menu.lst, then run 'sudo grub-install /dev/hda' (worked nice on previous Ubuntus). However, now I get an error message saying: '/dev/hda: Not found or not a block device.'. :confused:

I have an old PC (about 6 years, therefore needed to insert acpi=forced in boot lines), with 2 IDE hard disks, and no special hardware.

Some output which might be useful:
[FONT="Courier New"]
ubuntu@ubuntu-1ghz:~$ sudo grub-install /dev/hda
/dev/hda: Not found or not a block device.

ubuntu@ubuntu-1ghz:~$ sudo mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda2 on /media/hda2 type vfat (rw,utf8,umask=007,gid=46)
/dev/sdb1 on /media/hdb1 type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)

ubuntu@ubuntu-1ghz:~$ sudo grub-install /dev/sda
/dev/sda does not have any corresponding BIOS drive.
[/FONT]
Help would be appreciated...

---

### Post by tosoth on 2008-04-26
It won't work, because 8.04 named all disks as "sda, sdb, sdc...". I had problem with this too. Try running live cd, run terminal and try:

sudo grub

grub> find /boot/grub/stage1
(here you will see, where he's found grub, something like (hdX,X))

grub> root (hdX,X)

grub> setup (hd0)

grub> quit

in case it won't work, repeat everything but with "setup (hd1)"

good luck.

---

### Post by KeesM on 2008-04-26
Works for me. Fortunately, still had a 7.10 CD around. Thanks! :D

Anyone knowing how to do this directly from 8.4 (not from CD)?

---

### Post by guatebus on 2008-09-29
This thread might help you

[http://ubuntuforums.org/showthread.php?t=440752](http://ubuntuforums.org/showthread.php?t=440752)

:popcorn:

---

### Post by caljohnsmith on 2008-09-30
> **KeesM said:**
> Works for me. Fortunately, still had a 7.10 CD around. Thanks! :D

Anyone knowing how to do this directly from 8.4 (not from CD)?
You don't have to use a Live CD to run those Grub commands that tosoth gave, you can run them when you are in any Ubuntu (8.04 or any version). And of course you can run them from the 8.04 Live CD too. :)

---

