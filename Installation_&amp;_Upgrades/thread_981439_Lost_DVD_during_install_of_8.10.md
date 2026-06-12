---
title: "Lost DVD during install of 8.10"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by Mrmilim on 2008-11-13
Just upgraded to latest version and now my DVD drive only accepts cds and causes the error

Unable to mount the volume


and a popup of the game title with

Dbus error org.freedesktop.Dbus.error.No Reply: Did not receive a reply


Tried sudo mount /media/cdrom and came back with

special device /dev/hdb does not exist, 


what did I do wrong and how do I fix it? Simplified answers would be appreciated as I'm new to Ubuntu (my son installed it for me the 1st time and I wasn't watching what he did lol)

---

### Post by alfa81 on 2008-11-15
Hi...I have the same problem too, I see this post fore the same problem...

[http://ohioloco.ubuntuforums.org/showthread.php?p=6183179#post6183179](http://ohioloco.ubuntuforums.org/showthread.php?p=6183179#post6183179)

Hanyone can help??

---

### Post by mc4man on 2008-11-15
If you did an upgrade (vs. fresh install) you may want to look at and compare fstab to lshw.
run 
```
cat /etc/fstab
``` and (looking at cdrom entry(s)```
sudo lshw -C disk
```

You may also want to look at this to see if your drive is listed twice

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

---

### Post by alfa81 on 2008-11-16
Thanks, I see that notting isn't changed for my old fstab (8.04).

fstab:
```

/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

lshw:

```

  *-cdrom:0               
       description: DVD reader
       product: DVD D LH-16D1P
       vendor: LITE-ON
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: TL13
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: DVD-RAM writer
       product: CD/DVDW SH-S182M
       vendor: TSSTcorp
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: SB03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

```

cd.rules:

```

# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# CDDVDW_SH-S182M (pci-0000:03:00.0-scsi-0:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:03:00.0-scsi-0:0:1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:03:00.0-scsi-0:0:1:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:03:00.0-scsi-0:0:1:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:03:00.0-scsi-0:0:1:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
# DVD_D_LH-16D1P (pci-0000:03:00.0-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:03:00.0-scsi-0:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:03:00.0-scsi-0:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"

```

I'am only a nooby, but for me nothing is changing....and you?

Thanks for help! :)

---

