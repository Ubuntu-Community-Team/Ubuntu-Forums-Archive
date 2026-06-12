---
title: "mdadm problems after upgrading to Dapper"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by kaam on 2006-08-06
Hi there,

I recently upgraded my COMPAQ ML370 server from Breezy to Dapper, and since then, mdadm has been hanging.  Following is a recent output after I ran apt-get upgrade:

[I]Setting up mdadm (1.12.0-1ubuntu5) ...
 * Starting RAID devices...                                                     dpkg: error processing mdadm (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 mdadm
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]

I also got an e-mail with the following message:

[I]WARNING! If you are using hard disks which have a md superblock from an
earlier installation in a different RAID array, you MUST zero the
superblock before activating the autostart feature.

To do this, do not start the RAID devices automatically. First, zero the
superblock (mdadm --zero-superblock /dev/mdX). Next, use `dpkg-reconfigure
mdadm` to reactivate the autostart feature.[/I]

A listing of my /dev directory shows I have md0 to md24, and besides, I'm not sure which of the md's to run the above command on.

By the way, I have two RAIDS on the server.  A RAID 0 drive 0 with two 9.1 GB SCSI disks for a total capacity of 8668 MB, and a RAID 1 drive 1 with four 36.1 GB SCSI disks for a total capacity of 102 GB.  The machine also has a Compaq Smart Array 3200 Controller.

I also tried to purge and re-install mdadm, without much success.

Please help.

---

