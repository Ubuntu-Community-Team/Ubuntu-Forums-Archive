---
title: "Just compiled a new kernel have two problems relating to hard drive."
date: 2005-12-05
forum: Installation &amp; Upgrades
---

### Post by Royle on 2005-12-05
I just compiled a new kernel.  I used the vanilla-sources-2.6.14 and the ck patchset.  I copied my old config from the latest ubuntu image.  When I boot I get an error saying that mounting file systems fail, but it keeps on booting.  When it finally boots, my ntfs drive is not mounted even though I never removed ntfs support.  Also, DMA is not enabled and when I try to do so I get this: 

mike@ubuntu:~$ sudo hdparm -d1 /dev/hdb
Password:

/dev/hdb:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

Can someone help me with these too problems?  Any help is greatly appreciated.

---

### Post by az on 2005-12-05
[QUOTE=Royle]I just compiled a new kernel.  I used the vanilla-sources-2.6.14 and the ck patchset.  I copied my old config from the latest ubuntu image.  When I boot I get an error saying that mounting file systems fail, but it keeps on booting.  When it finally boots, my ntfs drive is not mounted even though I never removed ntfs support.  Also, DMA is not enabled and when I try to do so I get this: 

mike@ubuntu:~$ sudo hdparm -d1 /dev/hdb
Password:

/dev/hdb:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

Can someone help me with these too problems?  Any help is greatly appreciated.[/QUOTE]

Any details of how the mounting fails?  Look in the logs.  Use the log tool.

---

### Post by Royle on 2005-12-05
I just looked through the log for the terms mount and failed separetly, I couldn't find any error about it.

---

### Post by az on 2005-12-05
What about in dmesg

Type:
dmesg


And what happens when you try to mount the drives by hand?

---

### Post by Royle on 2005-12-05
error from desg: 

[4294694.349000] cdrom: open failed.
[4294694.352000] cdrom: open failed.
[4294694.560000] device-mapper: dm-linear: Device lookup failed
[4294694.560000] device-mapper: error adding target to table
[4294694.569000] device-mapper: dm-linear: Device lookup failed
[4294694.569000] device-mapper: error adding target to table
[4294694.579000] device-mapper: dm-linear: Device lookup failed
[4294694.579000] device-mapper: error adding target to table
[4294694.588000] device-mapper: dm-linear: Device lookup failed
[4294694.588000] device-mapper: error adding target to table
[4294694.597000] device-mapper: dm-linear: Device lookup failed
[4294694.597000] device-mapper: error adding target to table
[4294694.607000] device-mapper: dm-linear: Device lookup failed
[4294694.607000] device-mapper: error adding target to table
[4294694.616000] device-mapper: dm-linear: Device lookup failed
[4294694.616000] device-mapper: error adding target to table
[4294694.626000] device-mapper: dm-linear: Device lookup failed
[4294694.626000] device-mapper: error adding target to table
[4294694.635000] device-mapper: dm-linear: Device lookup failed
[4294694.635000] device-mapper: error adding target to table
[4294694.644000] device-mapper: dm-linear: Device lookup failed
[4294694.644000] device-mapper: error adding target to table
[4294694.654000] device-mapper: dm-linear: Device lookup failed
[4294694.654000] device-mapper: error adding target to table
[4294694.663000] device-mapper: dm-linear: Device lookup failed
[4294694.663000] device-mapper: error adding target to table
[4294694.672000] device-mapper: dm-linear: Device lookup failed
[4294694.672000] device-mapper: error adding target to table
[4294694.682000] device-mapper: dm-linear: Device lookup failed
[4294694.682000] device-mapper: error adding target to table
[4294694.699000] device-mapper: dm-linear: Device lookup failed
[4294694.699000] device-mapper: error adding target to table
[4294694.814000] device-mapper: dm-linear: Device lookup failed
[4294694.814000] device-mapper: error adding target to table

This is what I get when I try to mount it

mike@ubuntu:~$ sudo mount /dev/hda1
mount: /dev/hda1 already mounted or /media/hda1 busy

but there are no files in /media/hda1

Thanks for your continued support.

---

### Post by az on 2005-12-06
Other than a config problem, did the patchset apply cleanly?  Can you try with a 2.6.12 kernel?

---

