---
title: "HDD not showing up"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by azraelck on 2008-02-14
I've just built a new computer, and among other things decided (against sanity and better judgment) to run a dual boot WinXP/Ubuntu machine. This would let me play a number of games that Wine won't ever run. 

However, while the CD works fine (in fact, I used it two days ago to set up my old computer with a fresh install of Ubuntu for my nephew and niece) the disk partitioner is not finding my HDD. I have a Western Digital 250gb SATA drive. Windows is already installed, although doing it's usual thing of not working right, and will boot up somewhat fine (again, for Windows). 

Gnome also crashed when it booted up, but then loaded correctly, if in a odd resolution that I need a microscope to read the text. So I doubt that's any real problem. Thanks in advance.

---

### Post by jan quark on 2008-02-14
run these terminal commands to ckech if your driver is recognized by ubuntu in the first place

post the output please


```
mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by silviutp on 2008-02-25
Hi,

I have the same problem ( 250GB hdd not detected) so I can't install.

mount output:
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

fdisk -l : no output

/etc/fstab output:
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

I've also attached the lshw output.

---

### Post by ktmuffin on 2008-02-25
Does your motherboard detect the hard disk when you first power up the system?
The drive may be defective or you have power or cabling problems if it doesn't.

---

### Post by silviutp on 2008-02-25
The drive is detected by Windows Vista which is already installed on that drive, and it was also detected by Kubuntu Ultimate some time ago.

---

### Post by charlesbw on 2008-03-02
I have the same issue, ubuntu will not show my two disk drives while i am trying to install.  It showed it earlier tonight, but after showing it...it froze up during the install (when the screen said Scanning Mirrors).

---

