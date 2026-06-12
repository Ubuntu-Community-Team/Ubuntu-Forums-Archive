---
title: "zfs. Recovery from drive clone gone wrong."
date: 2023-09-14
forum: Installation &amp; Upgrades
---

### Post by TeslaCoils on 2023-09-14
zfs. Recovery from drive clone gone wrong.
zfs: The following words in your search query were ignored because they are too common words: zfs.
You must specify at least one word to search for. Each word must consist of at least 4 characters and must not contain more than 84 characters excluding wildcards.

I was looking for options to 
clone/silver/mirror a ZFS dive 
Mint 21.2 mate w/ ZFS & no encryption
Dell Latitude e6540
(& then expand the 480 SSD to 960)

1st thought was Clonezilla / UBCD & was a no-go.
Then the ZFS mirroring thought popped in.

This ZFS cloning topic has writeups from many w/ assumptions that gloss over details.

Every article assumed that you needed to install tools for ZFS commands.
Found an ubuntu writeup w/ simple, laid out details.

& when installing, I noticed libraries had been removed.
Took a screenshot..but.. 
Now booting into a dead end w/ a flashing 
[Failed] Failed to start Bluetooth service.

LiveUSB I can see the drive in GParted,
(bpool & rpool)
but can't figure a way in.


Thanks folks!

---

### Post by MAFoElffen on 2023-09-14
To "cloned" your drive before trying to repair it, I would use 'dd'.

Have you done a boot-repair report? Has it ever booted at all? Have you tried to boot from an Ubuntu LiveUSB, and tried
```

[code]
sudo su
apt update
apt install -y zfs-initramfs zfsutils-linux
zpool export -a
zpool import -N -R /mnt rpool
zpool import -N -R /mnt bpool

```
HERE, list the datasets of ZFS and modify The next 4 lines after that to what your system says. I have this for the way Ubuntu installs from their installer...  

```

## Added line for you:
zfs list | grep -m 1 'rpool/ROOT/  ## Check the output from this.
# UUID=$(zfs list | grep -m 1 'rpool/ROOT/ubuntu_' | cut -b 19-24 )
# Modify the dataset name in red below to what the above output says...
zfs mount rpool/ROOT/[COLOR=#ff0000]ubuntu_$UUID[/COLOR]
zfs mount bpool/BOOT/[COLOR=#ff0000]ubuntu_$UUID[/COLOR]
zfs mount -a
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount -t tmpfs tmpfs /mnt/run
mkdir /mnt/run/lock
chroot /mnt /bin/bash --login
mount -a

apt update

```
You will be chrooted into the system...

From there you can make snapshots of the pools or datasets, send recieve  to where you want to, or make repairs to the installed system

---

### Post by MAFoElffen on 2023-09-15
All of my system here are ZFS-On-Root... I glossed over cloning a drive, because I feel that

#1. As your system is not booting, that is not your priority at the moment.

#2. I feel that cloning a drive with a ZFS System installed on it, is not the way to go... You can do it, but why?

Let me explain why cloned ZFS drives are not smart. When you create a ZFS Pool, I create it with unique disk identifiers, so cloning a drive with ZFS pools on it will not work, if unique disk identifiers are used i creation. Now if you use unique labels, it would, if you kept track of those UID labels are relabeled for the replacement partitions... But that is not how I usually do business with that. There are other ways.

With ZFS, You can do backups with Snapshots, Send and Receive. I use  sanoid/syncoid to help me do my backups. That way I can backup pools or datasets and send them to another pool. (local & remote)
RE:
[https://manpages.ubuntu.com/manpages/focal/en/man8/syncoid.8.html](https://manpages.ubuntu.com/manpages/focal/en/man8/syncoid.8.html)
[https://github.com/jimsalterjrs/sanoid](https://github.com/jimsalterjrs/sanoid)

Painless. You can logically restore snapshots to the same system, or to other systems.

With ZFS, if you keep pools kept in partitions, then you can physically migrate them to other systems, using export and import. In the import command, you can even import a pool, with a different name (renamed), so it can exist on the same system, without a conflict. That way you can copy or sync between pools.

If you are going to use ZFS, learn what it's abilities and strengths are, and use them.

You could always use tradition file diff based backup solutions along with that... My suggestion on that is to do a Forums search on "Incremental Backup rdiff-backup" for User "TheFu"... Such as these jewels: 
[https://ubuntuforums.org/showthread.php?t=2384864&p=13739441#post13739441](https://ubuntuforums.org/showthread.php?t=2384864&p=13739441#post13739441) 
[https://ubuntuforums.org/showthread.php?t=2484498](https://ubuntuforums.org/showthread.php?t=2484498)

I respect and recommend what this User has to say about backups as very good reads. Take what he says about freezing the filesystem with LVM2, and apply it as ZFS SnapShots. 

The key thing about ZFS Snapshots, is that they are immutable, meaning, once created, they are read-only and immune from being corrupted by viruses and attacks.

---

### Post by TheFu on 2023-09-15
3 backup commands for simple, backups: [https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329](https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329)

[LIST=1]
[*]Same system - source and target storage are on the same system. No LVM snapshots. Ensure the target storage is a different physical device and has a native Linux file system.  This can also be used with NFS, but malware/cryptoware knows about CIFS and NFS, so best not to use them for backup storage, ever.
[*]pushed backups - Client sends the backup to a remote server. Same caveats for "same system" backups apply.
[*]pulled backups - Server "pulls" backups from remote clients. Same caveats for "same system" backups apply.
[/LIST]

Backups can become complex, but doing simple stuff is often necessary in the beginning. That's the point of the link above.  The push/pull backups need more setup, like a root-equivalent account that supports ssh between the system that initiates the backups and the other side. All backups probably need to be run as 'root' to maintain owner, group, permissions.  Just sayin'.  Without that information, you have data which may not actually be useful.

---

### Post by #&amp;thj^% on 2023-09-15
> **MAFoElffen said:**
> 
**#2. I feel that cloning a drive with a ZFS System installed on it, is not the way to go... You can do it, but why?**

+1 Why Indeed.
> **MAFoElffen said:**
> 
Let me explain why cloned ZFS drives are not smart. When you create a ZFS Pool, I create it with unique disk identifiers, so cloning a drive with ZFS pools on it will not work, if unique disk identifiers are used i creation. Now if you use unique labels, it would, if you kept track of those UID labels are relabeled for the replacement partitions... But that is not how I usually do business with that. There are other ways.

With ZFS, You can do backups with Snapshots, Send and Receive. I use  sanoid/syncoid to help me do my backups. That way I can backup pools or datasets and send them to another pool. (local & remote)
RE:
[https://manpages.ubuntu.com/manpages/focal/en/man8/syncoid.8.html](https://manpages.ubuntu.com/manpages/focal/en/man8/syncoid.8.html)
[https://github.com/jimsalterjrs/sanoid](https://github.com/jimsalterjrs/sanoid)

If you are going to use ZFS, learn what it's abilities and strengths are, and use them.
The old adage learn to walk before you run. 
> **MAFoElffen said:**
> 
You could always use tradition file diff based backup solutions along with that... My suggestion on that is to do a Forums search on "Incremental Backup rdiff-backup" for User "TheFu"... Such as these jewels: 
[https://ubuntuforums.org/showthread.php?t=2384864&p=13739441#post13739441](https://ubuntuforums.org/showthread.php?t=2384864&p=13739441#post13739441) 
[https://ubuntuforums.org/showthread.php?t=2484498](https://ubuntuforums.org/showthread.php?t=2484498)
+1
> **TheFu said:**
> 3 backup commands for simple, backups: [https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329](https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329)

[LIST=1]
[*]Same system - source and target storage are on the same system. No LVM snapshots. Ensure the target storage is a different physical device and has a native Linux file system.  This can also be used with NFS, but malware/cryptoware knows about CIFS and NFS, so best not to use them for backup storage, ever.
[*]pushed backups - Client sends the backup to a remote server. Same caveats for "same system" backups apply.
[*]pulled backups - Server "pulls" backups from remote clients. Same caveats for "same system" backups apply.
[/LIST]

Backups can become complex, but doing simple stuff is often necessary in the beginning. That's the point of the link above.  The push/pull backups need more setup, like a root-equivalent account that supports ssh between the system that initiates the backups and the other side. All backups probably need to be run as 'root' to maintain owner, group, permissions.  Just sayin'.  Without that information, you have data which may not actually be useful.

+1
Nice thread, even though the OP seems absent.
```
cd /Backups && ls
etc  home  rdiff-backup-data  root  usr

```
ADDITIONAL EDIT:
Like MAFoElffen I like and use sanoid/syncoid for my zfs pools, I still copy over /Documents on all systems for safety. (3-5 Copies)

---

### Post by TheFu on 2023-09-15
My use of ZFS is completely novice level.  

The systems where I have ZFS don't use anything special about it for backups.

---

### Post by TeslaCoils on 2023-09-16
I'm not gently tapping my head against the wall & had to step away to regroup(wry grin)
Any light shone for currently blind eyes is appreciated&#128579;

sudo su
root@mint:/home/mint# apt install -y zfs-initramfs zfsutils-linux
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
zfs-initramfs is already the newest version (2.1.5-1ubuntu6~22.04.1).
zfsutils-linux is already the newest version (2.1.5-1ubuntu6~22.04.1).
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
root@mint:/home/mint#
root@mint:/home/mint# ^C
root@mint:/home/mint# exit
exit
mint@mint:~$ zpool export -a
mint@mint:~$ zpool import -N -R /mnt rpool
no pools found: some devices require root privileges
cannot import 'rpool': no such pool available
mint@mint:~$ sudo zpool import -N -R /mnt rpool

## Added line for you:
zfs list | grep -m 1 'rpool/ROOT/  ## Check the output from this.no
just sits there w/
>
& no output to the LiveUSB root dir (or spot I can discern)

~~~~~~~
notes & finding info
Gparted shows
sda4 as bpool
sda5 as rpool

zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              257M  1.50G       96K  /mnt/boot
bpool/BOOT                                         257M  1.50G       96K  none
bpool/BOOT/ubuntu_3xxe3q                           257M  1.50G      257M  /mnt/boot
rpool                                              410G  16.4G       96K  /mnt
rpool/ROOT                                        10.6G  16.4G       96K  none
rpool/ROOT/ubuntu_3xxe3q                          10.6G  16.4G     8.40G  /mnt
rpool/ROOT/ubuntu_3xxe3q/srv                        96K  16.4G       96K  /mnt/srv
rpool/ROOT/ubuntu_3xxe3q/usr                       260K  16.4G       96K  /mnt/usr
rpool/ROOT/ubuntu_3xxe3q/usr/local                 164K  16.4G      164K  /mnt/usr/local
rpool/ROOT/ubuntu_3xxe3q/var                      2.15G  16.4G       96K  /mnt/var
rpool/ROOT/ubuntu_3xxe3q/var/games                  96K  16.4G       96K  /mnt/var/games
rpool/ROOT/ubuntu_3xxe3q/var/lib                  2.14G  16.4G     1.99G  /mnt/var/lib
rpool/ROOT/ubuntu_3xxe3q/var/lib/AccountsService    96K  16.4G       96K  /mnt/var/lib/AccountsService
rpool/ROOT/ubuntu_3xxe3q/var/lib/NetworkManager    172K  16.4G      172K  /mnt/var/lib/NetworkManager
rpool/ROOT/ubuntu_3xxe3q/var/lib/apt              88.9M  16.4G     88.9M  /mnt/var/lib/apt
rpool/ROOT/ubuntu_3xxe3q/var/lib/dpkg             66.0M  16.4G     66.0M  /mnt/var/lib/dpkg
rpool/ROOT/ubuntu_3xxe3q/var/log                  12.9M  16.4G     12.9M  /mnt/var/log
rpool/ROOT/ubuntu_3xxe3q/var/mail                   96K  16.4G       96K  /mnt/var/mail
rpool/ROOT/ubuntu_3xxe3q/var/snap                  128K  16.4G      128K  /mnt/var/snap
rpool/ROOT/ubuntu_3xxe3q/var/spool                 112K  16.4G      112K  /mnt/var/spool
rpool/ROOT/ubuntu_3xxe3q/var/www                    96K  16.4G       96K  /mnt/var/www
rpool/USERDATA                                     399G  16.4G       96K  /mnt
rpool/USERDATA/abby_lllv3u                         399G  16.4G      399G  /mnt/home/abby
rpool/USERDATA/root_lllv3u                        1.47M  16.4G     1.47M  /mnt/root

# UUID=$(zfs list | grep -m 1 'rpool/ROOT/ubuntu_' | cut -b 19-24 )
# Modify the dataset name in red below to what the above output says...
~~~~~~~~~~~~~
mint@mint:~$
sudo zpool import
   pool: bpool
     id: 11642700140327160655
  state: ONLINE
status: Some supported features are not enabled on the pool.
    (Note that they may be intentionally disabled if the
    'compatibility' property is set.)
 action: The pool can be imported using its name or numeric identifier, though
    some features will not be available without an explicit 'zpool upgrade'.
 config:

    bpool                                   ONLINE
      fa22f187-f4d1-6f40-bce8-4ba97f08def9  ONLINE

   pool: rpool
     id: 1660075175366193066
  state: ONLINE
 action: The pool can be imported using its name or numeric identifier.
 config:

    rpool                                   ONLINE
      8f791bcc-75c9-8f40-9fe1-6bc39b446fbe  ONLINE

~~~~~~~~~~~~~
(should bpool be loaded before due to SDA position?)
~~~~~~~~~~~~~
No joy from
sudo zfs mount rpool/ROOT/1660075175366193066
cannot open 'rpool/ROOT/1660075175366193066': dataset does not exist
sudo zfs mount rpool/ROOT/8f791bcc-75c9-8f40-9fe1-6bc39b446fbe
cannot open 'rpool/ROOT/8f791bcc-75c9-8f40-9fe1-6bc39b446fbe': dataset does not exist

Pondered variants w/ sda
sudo zfs mount rpool/sda5/ROOT/1660075175366193066
sudo zfs mount rpool/sda5/ROOT/1660075175366193066
sudo zfs mount sda5/rpool/ROOT/1660075175366193066

sudo zfs mount bpool/BOOT/ubuntu_$UUID
sudo zfs mount bpool/BOOT/fa22f187-f4d1-6f40-bce8-4ba97f08def9
cannot open 'bpool/BOOT/fa22f187-f4d1-6f40-bce8-4ba97f08def9': dataset does not exist

Pondered variants w/ sda
sudo zfs mount bpool/sda4/BOOT/11642700140327160655

---

### Post by MAFoElffen on 2023-09-16
Would rather be
```

sudo zfs mount rpool/ROOT/ubuntu_3xxe3q

```
But let me explain some things... Right before that you said "exit", which exited from being root, so from then on, you had to add sudo prefaced to all the commands. When you change back and forth from your user to root, you lose some things in the environment. Either stay as your own username or as root. Next, you are not necessarily required to mount "bpool/BOOT/ubuntu3xxe3q", (but is a good pracice to keep with,) as after mounting the rpool main dataset, you immediately do (as root)
```

zfs mount -a

```
Which tells ZFS to remount all it's internal mounts...

Importnt that when you are posting in this Forum, as it is their policy, to post all commands and output within CODE Tags. If you go back to your last post, you can go to "Edit Post" > Advanced Edit... Select the text of the commands and output, then select the "#" icon. That will wrap the highlighted text with CODE Tags. When replying to a post, you can get to the same editor by instead of going to "Quick Reply", instead go to "Adv Reply", where you can use the advanced editor buttons to help you with your formatting.

---

