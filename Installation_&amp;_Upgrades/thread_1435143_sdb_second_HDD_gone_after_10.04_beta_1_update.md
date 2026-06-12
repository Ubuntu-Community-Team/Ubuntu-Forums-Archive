---
title: "sdb/ second HDD gone after 10.04 beta 1 update"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by failmerc on 2010-03-21
Hey guys,

Last night I updated my 9.10 to 10.04 beta 1 and at first I got a few errors here and there which I managed to get rid of. There's one left though and that is my sdb not appearing now. It's still recognized though here's what I get from fdisk -l.

```
Schijf /dev/sda: 41.2 GB, 41174138880 bytes
255 koppen, 63 sectoren/spoor, 5005 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Schijf-ID: 0x30d430d3

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1        4794    38507773+  83  Linux
/dev/sda2            4795        5005     1694857+   5  Uitgebreid
/dev/sda5            4795        5005     1694826   82  Linux wisselgeheugen

Schijf /dev/sdb: 160.0 GB, 160041885696 bytes
255 koppen, 63 sectoren/spoor, 19457 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Schijf-ID: 0xc394c394

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1   *           1       19457   156287999+   7  HPFS/NTFS
```

What's wrong that it's not appearing anymore? It did the first time I was on 10.04 but after it it just disappeared. 

It also says in GParted -> Properties that the HDD is not coupled... I guess that might be the problem. How do I do that?

---

### Post by failmerc on 2010-03-21
I tried sudo mount /dev/sdb1 but I get some error saying that "mount: can't find /dev/sdba1 in either /etc/fstab nor /etc/mtab".

---

### Post by coffeecat on 2010-03-21
If you 'sudo mount /dev/sdb1' you need a mountpoint defined in /etc/fstab, otherwise mount doesn't know where to mount it. Alternatively, you can create a mountpoint and do 'sudo mount /dev/sdb1 /path/to/mountpoint'. Or, if you don't want sdb1 mounted on boot you can simply go to the Places menu and mount it by clicking on it.

But that's all a bit moot. You said it was mounted in Karmic. Do you mean mounted on bootup? Because, if so, then there must have been an entry in /etc/fstab and that should not have been touched by the dist-upgrade.

Post the contents of /etc/fstab to see what's there.

---

### Post by failmerc on 2010-03-21
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=88ca005d-ae4a-4fac-b49b-c8a3e4c56228 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9d98e23d-08ec-438d-8de7-84d817c92e54 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```That's what's in fstab.

In 9.10 the sdb2 which we are talking about was listed in "Computer". When I clicked on it I had to give my password and then I was able to enter it. I guess it wasn't mounted on bootup then.

Earlier my sdb2/2nd HDD was found under "/media/520C48250C480707/" but the only thing in /media now is the cdrom0.

---

### Post by failmerc on 2010-03-21
Alright I figured it out already thanks for the help :)

---

