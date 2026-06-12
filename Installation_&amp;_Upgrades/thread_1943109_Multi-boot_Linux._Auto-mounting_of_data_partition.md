---
title: "Multi-boot Linux. Auto-mounting of data partition?"
date: 2012-03-19
forum: Installation &amp; Upgrades
---

### Post by scruffyeagle on 2012-03-19
I've got a Toshiba A205 Satellite notebook w/ 1GB RAM & 120GB HD. It's my "project" machine, for playing & learning with. I've set it up with 4 installed OS's: Debian Squeeze, Ubuntu, Kubuntu, & Xubuntu. All the Untu's are v10.04LTS 32-bit. All 4 OS's use their own partition as the location of their respective "home" directories. I've set up 2 extra partitions on the HD, formatted as Ext4 & FAT32. What I'd like to do, is have all/each of the OS's automatically mount the Ext4 data partition (but not the FAT32), so it shows up under "Places" &/or on the desktop as available.

I know there's a way to do this, via an editing solution - but, I don't even know where to begin for that, much less how to proceed once I start.

Can anybody guide me through this?
TIA!

---

### Post by malspa on 2012-03-19
Make sure you have mount points for the data partitions. In Ubuntu, I have them in /media. In Squeeze, I have them in /mnt.

My /etc/fstab entries in Ubuntu 10.04 for my data partitions:

```
/dev/sda7 /media/sda7 ext3 defaults 0 0
/dev/sda8 /media/sda8 ext3 defaults 0 0
```

And in Debian Squeeze:

```
/dev/sda7 /mnt/sda7 ext3 defaults 0 2
/dev/sda8 /mnt/sda8 ext3 defaults 0 2
```

My data partitions are ext3, so you'd just have to change it to ext4. See **man fstab** for details.

---

### Post by oldfred on 2012-03-19
I prefer NTFS over FAT after I lost some files over 4GB that I did not know FAT32 could not save and my copy did not give an error.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Splitting home directory discussion - data in separate partition(s):
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

I also have multiple installs and after making the same edits multiple times I decided to do as much as possible from command line. I then copied to a bash file, cleaned it up and had a semi-automatic way to create mounts and auto-edit fstab.

---

### Post by scruffyeagle on 2012-03-20
_**malspa**_ & _**oldfred**_: Thank you each for the replies & info you provided. I'll be pursuing this during the next week, reading up via the links, and eventually trying to do it without crashing whichever installation I'm experimenting with. I'll come back after I've succeeded or failed, to update you.

---

