---
title: "Trouble getting NTFS partitions working"
date: 2005-04-15
forum: Installation &amp; Upgrades
---

### Post by pdpi on 2005-04-15
Hi all, and sorry if this was already adressed, but a quick search for NTFS here didn't yield results on my problem.

Introductions aside, my problem is that my NTFS partitions mount properly, but only root can read them. My default user acct gets permission denied when trying to access those partitions. The problem only applies to NTFS partitions, as the fat32 ones work just fine.

This is my partition table:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   83  Linux
/dev/sda2   *           8        6087    48837600    7  HPFS/NTFS
/dev/sda3            6088        9735    29302560   83  Linux
/dev/sda4            9736       19457    78091965    5  Extended
/dev/sda5            9736        9860     1004031   82  Linux swap / Solaris
/dev/sda6            9861       11077     9775521    b  W95 FAT32
/dev/sda7           11078       15941    39070048+   7  HPFS/NTFS
/dev/sda8           15942       19457    28242238+   b  W95 FAT32

```

and my fstab follows:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /boot           ext2    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/sda2       /media/windows  ntfs    defaults,ro     0       2
/dev/sda6       /media/incoming vfat    defaults        0       2
/dev/sda7       /media/music    ntfs    defaults,ro     0       2
/dev/sda8       /media/share    vfat    defaults        0       2
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

I essentially copied the /dev/sda3 entry for the remainder of the FSes, adding ro to the ntfs ones.

Thanks for the attention

---

### Post by accuser on 2005-04-15
Try:
```
/dev/sda2       /media/windows  ntfs    ro,user     0       0

```

---

### Post by alastair on 2005-04-15
Show an "ls -l" of the relevant NTFS mount :

ls -l /media/
ls -l /media/windows

You might just need to add "uid","gid" and/or "umask" to your mount options for the NTFS partition in the fstab file. See : man mount (and look for the NTFS) section).

---

### Post by pdpi on 2005-04-15
[QUOTE=alastair]Show an "ls -l" of the relevant NTFS mount :

ls -l /media/
ls -l /media/windows

You might just need to add "uid","gid" and/or "umask" to your mount options for the NTFS partition in the fstab file. See : man mount (and look for the NTFS) section).[/QUOTE]
 Ok, thanks.

From a bit of man reading, I assume that I should just set umask to 555 for both filesystems (as NTFS is read-only, that seems about good). Any loose ends I should take care of?

EDIT: Aparently, my optimism was ill-founded. Though I can full well ls my ntfs mounts, actually reading them is another matter. I double-checked with the chmod manpage, and 555 is indeed r-x for everybody, so I didn't screw up there. ideas?

---

### Post by Dr Gonzo on 2005-04-15
Here's the relevant part of my /etc/fstab:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

# Windows filesystems
/dev/hdb1       /c              vfat    umask=000       0       0
/dev/hdb3       /g              ntfs    ro,umask=0222   0       0
/dev/hdb4       /f              vfat    umask=000       0       0
```These umasks work fine.  /dev/hdb3 is mounted ntfs ro, and the other two are readable and writable by everyone.

---

### Post by pdpi on 2005-04-16
[QUOTE=Dr Gonzo]Here's the relevant part of my /etc/fstab:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

# Windows filesystems
/dev/hdb1       /c              vfat    umask=000       0       0
/dev/hdb3       /g              ntfs    ro,umask=0222   0       0
/dev/hdb4       /f              vfat    umask=000       0       0
```These umasks work fine.  /dev/hdb3 is mounted ntfs ro, and the other two are readable and writable by everyone.[/QUOTE]
 Thanks. That worked wonders for me.
Fully functioning Ubuntu system for me! Yay!

---

