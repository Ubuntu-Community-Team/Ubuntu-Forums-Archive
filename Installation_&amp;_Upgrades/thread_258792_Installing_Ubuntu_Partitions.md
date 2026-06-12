---
title: "Installing Ubuntu Partitions"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by ART_Adventures on 2006-09-16
I've been trying to create a dual boot situation between Windows XP and Ubuntu. I have two physical hard disks, both of them clean. I inserted the Windows xp cd and created a suitably sized NTFS partition for it. I then booted with Ubuntu Desktop. I loaded the installer. It gave me the option to automatically arrange my paritions or do it manually, so I selected manual. I selected to create a swap partition and the rest was another partition of FAT32. This was for my first hard disk, and then I selected another whole FAT32 partition for second disk. On the next screen it shows me two drop down menus, each associated with a partition. It mentions about assigning "/" to a partition and it also assigns swap to the swap space. So, I selected "/" from the first drop down and assiociated with one of the FAT32 partitions, and click next. It then exits the install and says something like "invalid file system for this mount point".

Can anybody help me?

Thanks.

---

### Post by a-musing amazon on 2006-09-16
FAT32 file systems are not, by default, very good for linux /root and /boot. There are ways of booting off a FAT32 partition, and there are ways of hosting a root partition inside a FAT32 file but I don't believe they are available when installing from the Live CD.

You only need a small partition for /boot - it can be as little as 64 Mb, or you can co-locate it with you /root.

/boot can be formatted ext2 (as it is basically read-only there is no advantage of a journalling filesystem such as ext3).  

/ is the root partition and holds the operating system ("Dapper") and most of your programs. It can be formatted using a journalling filesystem such as ext3 or xfs or reiser (journalling filesystems are easy to recover if there is a crash). Ext3 is probably the 'safest'. It should be 5Gb-10Gb, though a basic install is only a few Gb best to have some room for expansion.

Its wisest to also create /home as a seperate partition - this is where your own stuff gets put - e.g. your music files. Keeping this in a seperate partition allows you to preserve it if you have to re-install the operating system of if you want to try other ones. Its actually a folder under /root but can be hosted on another partition.

Any FAT32 partitions you have also created will be mounted and are read/writable by Dapper as well as XP, so if you want to share stuff between Dapper and XP you can put then there (so you could also put your music/video here).

Standard FAT32 file-systems don't preserve proper unix-style file permissions though, so don't put your /home on one.

---

### Post by ART_Adventures on 2006-09-16
Thanks for the information :-)

That seemed to work. And now, things are up and running.

---

