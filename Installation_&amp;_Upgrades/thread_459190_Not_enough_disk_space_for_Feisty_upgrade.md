---
title: "Not enough disk space for Feisty upgrade"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by dblbogey on 2007-05-30
I recently tried to upgrade from Edgy via the Upgrade Manger, and I received the following error message:

"Not enough free disk space.

The upgrade aborts now. Please free at least 412M of disk space on /var/cache/apt/archives. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean' "

I have done all the above, but I still get the same message. File browser says that I have 3G free space on hda1, but it also says that there is only approx. 260M of free space in the above-referenced '...../archive' subdirectory. There are currently 1 file and 1 folder in that subdirectory, but they are showing using 0 disk space.

I have run Filelight, which show in that "..../archive" subdirectory 20.8 MiB (53%), Files: 14 (82%), but I don't know how to interpret that data to use to fix my problem.

I'm a relative newbie with Ubuntu, so  I'll really appreciate your patience and specifics on ideas for a fix. Thanks.

---

### Post by taurus on 2007-05-30
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```
Perhaps you need to clean out some old archives with

```
sudo aptitude autoclean
```

---

### Post by stchman on 2007-05-30
> **dblbogey said:**
> I recently tried to upgrade from Edgy via the Upgrade Manger, and I received the following error message:

"Not enough free disk space.

The upgrade aborts now. Please free at least 412M of disk space on /var/cache/apt/archives. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean' "

I have done all the above, but I still get the same message. File browser says that I have 3G free space on hda1, but it also says that there is only approx. 260M of free space in the above-referenced '...../archive' subdirectory. There are currently 1 file and 1 folder in that subdirectory, but they are showing using 0 disk space.

I have run Filelight, which show in that "..../archive" subdirectory 20.8 MiB (53%), Files: 14 (82%), but I don't know how to interpret that data to use to fix my problem.

I'm a relative newbie with Ubuntu, so  I'll really appreciate your patience and specifics on ideas for a fix. Thanks.

Feisty only needs about 3G for a complete install.  I recommend a clean install rather than an upgrade.  I tried the upgrade path and it gave me problems.  Clean install, no problems.

Do a sudo fdisk -l

This will tell you about all your partitions and how much is free.

---

### Post by dblbogey on 2007-05-30
df -h says:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             2.4G  2.2G  136M  95% /
varrun                252M   68K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M   80K   10M   1% /proc/bus/usb
udev                   10M   80K   10M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  235M   7% /lib/modules/2.6.17-11-generic/volatile
/dev/hda1              13G  9.8G  3.0G  77% /media/hda1

Autoclean freed 0 diskspace.

---

### Post by taurus on 2007-05-30
> **dblbogey said:**
> df -h says:

Filesystem            Size  Used Avail Use% Mounted on
**[COLOR="Blue"]/dev/hda3             2.4G  2.2G  136M  95% /[/COLOR]**
varrun                252M   68K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M   80K   10M   1% /proc/bus/usb
udev                   10M   80K   10M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  235M   7% /lib/modules/2.6.17-11-generic/volatile
/dev/hda1              13G  9.8G  3.0G  77% /media/hda1

Autoclean freed 0 diskspace.

You don't give yourself a lot of disk space when you first installed Ubuntu?  If you installed Gnome (desktop versioon), it would take almost all of your allow disk space there, 2.4GB.

---

### Post by dblbogey on 2007-05-30
fdisk -l shows:

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1660    13333918+   7  HPFS/NTFS
/dev/hda2            2371        2434      511841   82  Linux swap / Solaris
/dev/hda3            2053        2370     2554335   83  Linux

---

### Post by dblbogey on 2007-05-30
> **taurus said:**
> You don't give yourself a lot of disk space when you first installed Ubuntu?  If you installed Gnome (desktop versioon), it would take almost all of your allow disk space there, 2.4GB.

What can I do now? Is it possible to increase the size of hda3?

---

### Post by taurus on 2007-05-30
You can try using gparted from GParted LiveCD to resize your ntfs and merge that space to /dev/hda3.  And of course, _always_ backup important stuff in Windows first before you decide to play around with resizing.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

