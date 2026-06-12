---
title: "DVD not recognized after 14.04 installation"
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by mauritzvdworm on 2014-08-25
I've been searching the forums and trying a couple of different things the last two days but to no avail...  

I recently upgraded from 12.04 to 14.04 using the update manager, but the installation did not go well.  After the installation usb and dvd automount are not working any more.  

```
sudo lshw -C disk
``` gives an output

```
 *-disk                  
       description: ATA Disk
       product: ST9320325AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 0002
       serial: 6VE65LLW
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=00038503
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ892AS
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       logical name: /media/external
       version: 1.00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/external
          configuration: mount.fstype=iso9660 mount.options=ro,relatime state=mounted


```

and eject also works perfectly.  I can mount both the usb and dvd using

```
sudo mount -t auto /dev/dvd /media/external
```

but, I want to do a fresh installation from either a live usb or live cd.  I have tried both methods and have not managed to boot up from either of the two devices.

I'd appreciate ANY ideas on how to proceed.

---

### Post by mauritzvdworm on 2014-08-26
I found some handy information here

[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

I can locate the grub folder in the boot directory containing all the mod files.  I also moved the iso into the boot directory but running

```
set prefix=(hd[COLOR=Red]X,Y[/COLOR])/<path to modules>


```

with or without different combinations of X and Y followed by

```
insmod linux
```

gives the "no such file in directory" error message even though the file is located in that directory.

My HDD is not partitioned and I also tried (hd0), but still doesn't work.

If I can manage to set the prefix and initiate the mod files then maybe I can boot straight from the iso and do a clean install...

Any help?

---

### Post by varunendra on 2014-08-26
> **mauritzvdworm said:**
> ..I want to do a fresh installation from either a live usb or live cd.  I have tried both methods and have not managed to boot up from either of the two devices.

The OS installed on the hard disk or the changes to it have nothing to do with the booting in Live mode. If the Live DVD/USB were bootable, they should boot the computer even if there is no hard disk at all.

Can you confirm that the DVD/USB are bootable by booting another computer with them? How did you create them? Have you tried setting the DVD drive as the first boot device in the Boot Device Priority in BIOS?

---

### Post by mauritzvdworm on 2014-08-26
> Can you confirm that the DVD/USB are bootable by booting another computer with them?

I can confirm they are bootable.

> How did you create them?

DVD was created from .iso using a mac. For the flash I used netbootin.

> Have you tried setting the DVD drive as the first boot device in the Boot Device Priority in BIOS?

Jup, I tried to force a boot from the DVD and Flash by changing the preferences in the BIOS.  Also tried it with grub, but didn't work.

---

### Post by varunendra on 2014-08-26
> **mauritzvdworm said:**
> I can confirm they are bootable.

How did you confirm that?

If setting the DVD drive as first boot device in BIOS doesn't let you boot from it, it can mean only and only two things - 1) DVD is either not bootable, or badly written/scratchy/incompatible etc., and 2) The DVD drive is dying/has died.

Not being able to boot from USB is not strange, but not being able to boot from a 'tested ok' bootable DVD means only above things.

What speed did you write the DVD at?
What kind of DVD disc it is? DVD-R, +R, something else?

---

