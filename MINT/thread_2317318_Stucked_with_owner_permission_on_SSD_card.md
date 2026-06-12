---
title: "Stucked with owner permission on SSD card"
date: 2016-03-15
forum: MINT
---

### Post by calimero59 on 2016-03-15
Hello everybody, 

First of all excuse y english but I'm not native ^^

I'm running a fresh install of linux Mint (qiana 17) and, everything works fine excepted for the SSD cards. Since the install I'm not the owner and I cannot write/delete on the SSD cards.

I've already posted on ubuntu.fr for the same problem, but without any solution so far.
Here is the discussion  [https://forum.ubuntu-fr.org/viewtopic.php?pid=21479042#p21479042]("https://forum.ubuntu-fr.org/viewtopic.php?pid=21479042#p21479042") 

Any help would be appreciated because my 4 SSD cards are actually unusable. I'll stay connected to give any information requested.

thanks in advance

---

### Post by howefield on 2016-03-15
Thread moved to the "*MINT*" forum.

---

### Post by ajgreeny on 2016-03-15
With an SSD card in the machine can you please show the output of terminal command ```
sudo parted -l
mount
```so we can see the filesystem on the card and where it is mounted in the OS filesystem.

It may also help to see the output of command ```
ls -l /media/$USER/*
```

---

### Post by calimero59 on 2016-03-15
First of all, it's not a SSD HDD but a SD card (the same one find in his APN for instance). Sorry for the mistake.

Thanks ajgreeny for your help. The output of the commande you asked is :

```
lelynx@lelynx-SATELLITE-C850-1M4 ~ $ sudo parted -l[sudo] password for lelynx: 
Modèle: ATA ST500LT012-1DG14 (scsi)
Disque /dev/sda : 500GB
Taille des secteurs (logiques/physiques): 512B/4096B
Table de partitions : gpt


Numéro  Début   Fin    Taille  Système de fichiers  Nom  Fanions
 1      1049kB  538MB  537MB   fat32                     démarrage
 2      538MB   496GB  495GB   ext4
 3      496GB   500GB  4172MB  linux-swap(v1)




Avertissement: Impossible d'ouvrir /dev/sdb en lecture-écriture (Système de
fichiers accessible en lecture seulement). [COLOR=#008000][B]/dev/sdb a été ouvert en lecture
seule.[/B][/COLOR]
Modèle: Generic- Multi-Card (scsi)
Disque /dev/sdb : 512MB
Taille des secteurs (logiques/physiques): 512B/512B
Table de partitions : msdos


Numéro  Début  Fin    Taille  Type     Système de fichiers  Fanions
 1      119kB  512MB  512MB   primary  fat32                démarrage

**[COLOR=#008000]/dev/sdb a été ouvert en lecture seule[/COLOR]** means **[COLOR=#0000FF]/dev/sdb is open on read-only mode[/COLOR]**


```

```
lelynx@lelynx-SATELLITE-C850-1M4 ~ $ mount/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /boot/efi type vfat (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lelynx)
/dev/sdb1 on /media/lelynx/MEM-STICK 1 type vfat (ro,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
```

```
lelynx@lelynx-SATELLITE-C850-1M4 ~ $ ls -l /media/lelynx/MEM-STICK\ 1/total 0

```
[B][COLOR=#008000]

[/COLOR][/B]

---

