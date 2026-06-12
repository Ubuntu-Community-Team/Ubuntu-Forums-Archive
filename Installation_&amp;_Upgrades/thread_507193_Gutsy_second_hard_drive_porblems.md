---
title: "Gutsy second hard drive porblems"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by bdrevn on 2007-07-22
Hi.  I just stepped up to tribe 3.  While most things are going well, I have a drive that seems to have disappeared.  fstab looks fine, and I have tried...

$sudo mount /dev/hdb1 /media/hdb1
and I get...
mount: /dev/hdb1 already mounted or /media/hdb1 busy

Then I try...
$sudo umount /dev/hdb1
umount: /dev/hdb1: not mounted

$sudo umount /media/hdb1
umount: /media/hdb1: not mounted

Any ideas?  This has only been broken-ish since the upgrade.  Finally... it looks like /dev/hdb1 exists, as I think.  

$sudo fdisk -l
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9541    76638051   83  Linux
/dev/hda2            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              40        9729    77834925   83  Linux

Disk /dev/dm-0: 79.7 GB, 79702963200 bytes
255 heads, 63 sectors/track, 9690 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-0 doesn't contain a valid partition table

Thanks for any help.

---

### Post by Pumalite on 2007-07-22
Try 'mount' and see if it's mounted or not, and how, and where.

---

### Post by bdrevn on 2007-07-23
Result of:
$sudo mount /dev/hdb1

mount: /dev/disk/by-uuid/679d3eb7-53f5-4b45-94bb-69938dc4c777 already mounted or /media/hdb1 busy

whereas my normal drive gives me:
$ sudo mount /dev/hda1
mount: /dev/disk/by-uuid/267c6f7d-138f-41ce-95e7-87ae204f374f already mounted or / busy
mount: according to mtab, /dev/hda1 is already mounted on /

So, how do I un-busy, or unmount /dev/hdb1, given that I have tried umount?  Thanks for any help.

---

### Post by Pumalite on 2007-07-23
I said try: sudo mount.

---

### Post by bdrevn on 2007-07-23
Sorry for the confusion.  So:

$sudo mount

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-8-386/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/hdc on /media/cdrom1 type iso9660 (ro,noexec,nosuid,nodev,user=benedict)

So, it does not seem to show up in this result.  Any other ideas on how to check what is going on with the drive.  Recall that above fdisk -l seems to indicate that something exists at /dev/hdb.  Thanks so much for things so far.

---

### Post by Pumalite on 2007-07-23
Have you tried 'sudo mount -t ext3 /dev/sdb1 /media/sdb1'?

---

### Post by bdrevn on 2007-07-24
Thanks for the help, turns out that the drive seemed to be named something different in the /dev/ folder, seemingly turned to /dev/dm-0.  Not something I usually expect, but oh well.  I installed gparted and took a look at what it seemed to think was attached in terms of drives.  Again, thanks for the help.

---

### Post by hyperair on 2007-09-22
Thanks bdrevn that really helped! Mine's been switched from hdb1 to dm-1 and hda1 to dm-0 as well. Does anyone know what's going on? It seems to be something of the new kernel.

EDIT: Did you notice that you now have extra drives in your "Computer" window and drive mount applet?
EDIT: [http://ubuntuforums.org/showthread.php?t=257155](http://ubuntuforums.org/showthread.php?t=257155)

solution is:
```

sudo apt-get autoremove evms

```

---

### Post by Defrector on 2007-11-04
I've had similar problems described above; the solutions didn't hit the nail on the head but I stumbled on this on the hint you gave about names being changed:

'sudo mount /dev/mapper/sda1'

Now '/media/hda1' shows the fat fs on the drive! I wish I knew why this is.

Trying it with sdb1...

no dice.

hmm. Well, can't win em all.

---

### Post by Defrector on 2007-11-04
Ahh! Never mind on the sdbX problem- that drive is corrupt.

---

### Post by hyperair on 2007-11-04
Check your /etc/fstab for clues. on your hda1 problem.

---

