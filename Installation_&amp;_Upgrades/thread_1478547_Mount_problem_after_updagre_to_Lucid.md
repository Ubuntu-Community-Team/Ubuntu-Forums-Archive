---
title: "Mount problem after updagre to Lucid"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by edrojo on 2010-05-09
Mount problem after updagre to Lucid
Hi. I just installed Ubuntu 10.04. When PC rebooted it gave the next message:

Press S to skip mounting or M for manual recovery but it gave me no error. If I used S, my PC boots normally.



Here is my fstab:

/etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sdb1 during installation
UUID=cb37f231-68fd-452a-90e6-b16fee70e1aa / ext4 errors=remount-ro 0 1
# /home was on /dev/sda5 during installation
UUID=0d4c5629-c06c-4960-afbf-20c4c89e4a6a /home ext4 defaults 0 2
# swap was on /dev/sda6 during installation
UUID=0ed982c1-9990-4898-928a-fd4e605f4c9a none swap sw 0 0
#/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
#/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

Any help will be apreciated.

---

### Post by lemming465 on 2010-05-10
Could we also the the output of```

sudo -i
fdisk -lu
blkid
mount
df-m
```

---

### Post by edrojo on 2010-05-11
> **lemming465 said:**
> Could we also the the output of```

sudo -i
fdisk -lu
blkid
mount
df-m
```

Hi. here it is the output. Thanks for helping!!!!

edrojo@servidor:~$ sudo -i
[sudo] password for edrojo: 
root@servidor:~# fdisk -lu

Disco /dev/sda: 40.0 GB, 40020664320 bytes
255 cabezas, 63 sectores/pista, 4865 cilindros, 78165360 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x8ee08ee0

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63    20482874    10241406    7  HPFS/NTFS
/dev/sda2        20482875    78156224    28836675    f  W95 Ext'd (LBA)
/dev/sda5        20482938    78140159    28828611   83  Linux
/dev/sda6        78140223    78156224        8001   82  Linux swap / Solaris

Disco /dev/sdb: 30.0 GB, 30020272128 bytes
255 cabezas, 63 sectores/pista, 3649 cilindros, 58633344 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x72ae72ae

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1              63    58621184    29310561   83  Linux
root@servidor:~# blkid
/dev/sda1: UUID="78CC32D5CC328D7E" TYPE="ntfs" 
/dev/sda5: UUID="0d4c5629-c06c-4960-afbf-20c4c89e4a6a" TYPE="ext4" 
/dev/sda6: UUID="0ed982c1-9990-4898-928a-fd4e605f4c9a" TYPE="swap" 
/dev/sdb1: UUID="cb37f231-68fd-452a-90e6-b16fee70e1aa" TYPE="ext4" 
root@servidor:~# mount
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda5 on /home type ext4 (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
root@servidor:~# df-m
df-m: command not found
root@servidor:~# df-m
df-m: command not found
root@servidor:~# df -m
S.ficheros         Bloques de 1M   Usado    Dispon Uso% Montado en
/dev/sdb1                28174     20988      5756  79% /
none                       245         1       245   1% /dev
none                       249         1       249   1% /dev/shm
none                       249         1       249   1% /var/run
none                       249         0       249   0% /var/lock
none                       249         0       249   0% /lib/init/rw
/dev/sda5                27712     20034      6270  77% /home
root@servidor:~#

---

### Post by lemming465 on 2010-05-11
Hmmm.  I'm feeling stumped.  Everything in your /etc/fstab appears to be mounting normally.  The most common cause for this message for Lucid upgrades is apparently leftover usbfs junk in /etc/fstab related to the Virtualbox hypervisor, and you don't have that either.

Is there any more information during the boot about just what is refusing to mount?
For example, are there external USB disks plugged in?  Apparently with Lucid some of those don't come ready as fast as the kernel is expecting, and then upstart (I think) may give you such a message.

On the bright side, apparently just answering S for skip is getting you to a working system, so it's mostly an annoyance.

---

### Post by edrojo on 2010-05-12
It gave me no more errors. Thanks for your help, I'm very happy with lucid this is a minor bug that doesn't annoy me muchh

---

### Post by wayover13 on 2010-06-30
I have a problem something like this as well. This refers to a mythbuntu installation, btw, that was recently upgraded from 9.04 to 10.04.

I created 3 udev entries in /etc/udev.rules.d/10-local.rules for 3 drives that I occassionally hook up to this system when I want to store some program I've recorded. There are corresponding entries for the mount points for these drives in /etc/fstab.

This system has worked fine to date: when I plug in a drive, it is recognized and mounted at the approriate place, and its contents are then accessible to mythtv as recordings. But with the upgrade to Lucid, a problem has cropped up: when rebooting/restarting the system, at the mythbuntu splash screen, it detects that the drives are not present and expects me to press "S" or "M" before it will continue booting.

This is undesirable behavior. I know the drives are not present, and the way I've constructed the system, they're not supposed to be present most of the time (I use them only for occassional back-ups). The system doesn't need to and shouldn't prompt me about their absence every time the machine boots.

Granted, the system still boots. So long as I'm, there to press the "S" key at the appropriate point during the boot process, the system will continue and be up and running shortly after I've hit "S" three times. But it's an annoyance.

So, how can I get the system to stop checking for these 3 usually-absent disks each time it boots? Is there some config file I can edit to make the undesireable behavior stop?

Thanks,
James

---

### Post by wayover13 on 2010-06-30
I found the resolution to this problem in the bug thread at [https://bugs.launchpad.net/ubuntu-release-notes/+bug/510415](https://bugs.launchpad.net/ubuntu-release-notes/+bug/510415) . Briefly, the solution was to append a noobootwait option to the relevant fstab entries. Once I'd done that, the system no longer paused when booting up, awaiting key presses from me before it would continue. For more details, see the referenced thread.

James

---

### Post by wayover13 on 2010-07-01
Well, turns out this simple solution was too good to be true. Yes, appending the nobootwait option to relevant entries in my /etc/fstab file did stop the machine from pausing for user input during its boot process, but it created other problems--the likes of which I've not seen and cannot understand. You see, I have two capture cards in this computer, and with the nobootwait option appended to relevant entires in my /etc/fstab file, one of the two cards disappears, i.e., it either gives errors or simply registers as not present. So with nobootwait appended to relevant entries in my /etc/fstab file, I get a system where one of my two capture cards is disabled (!). As soon as I remove that option from /etc/fstab and reboot, I'm back to a system with two working capture cards. I've tested this twice now.

What in the world could be going on here?! This is frustrating.

James

---

### Post by wayover13 on 2010-07-04
With some help, I've managed to resolve these problems. See [http://ubuntuforums.org/showthread.php?t=1522827](http://ubuntuforums.org/showthread.php?t=1522827) for the resolution.

James

---

