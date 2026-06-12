---
title: "Hardy x86 and AMD installs, One USB Drive"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by JDex on 2008-05-08
Hello all,

First post, though I've lurked since Heron was released.  This is really my first distro since walking away from it back at Suse 6.

I have a handful of systems that I'll be trying different setups for and I'd like to tidily have installable ISOs on one USB Drive... but I can only seem to find instructions for one distro per drive.

I'll be using a 80Gig laptop drive in USB/FW400 enclosure to install Ubuntu Desktop and Server on AMD, Intel and possibly PPC systems.

If I partition the drive (likely Logical Drives on Ext Partition) and use the instructions [here](http://www.teamteabag.com/2008/03/07/install-ubuntu-804-hardy-heron-from-usb/) to setup bootable drives for each, is it likely that I'll be able to choose from the distros... or is this something I'll just need to try to find out.

Thanks for the great support and warm atmosphere the Ubuntu community provides.

---

### Post by garyedwardjohnston on 2008-05-08
Not sure why you'd want to install from this instead of a tidy small book of cd's, or a network install but...

I don't think what you're trying to do is possible because this boot option is set in BIOS.  Unless your BIOS can do something mine can't.  I can choose to boot from USB, but its that simple.  I wouldn't be able to choose a partition on the USB to boot from.

Good luck

---

### Post by JDex on 2008-05-08
Thank for the reply.

Some of the systems do not have cdrom/dvdroms and others do not have network boot in the options.  All have USB booting...

Beyond that though... testing it took less time than I thought... and the answer, at least with my configs is no.  It doesn't work.  May need to go grab a handful of 1G USB Drives.

Thank you.

---

### Post by garyedwardjohnston on 2008-05-08
I wonder if you can't install one operating system on this drive, then all of the partitions, then a distro on each, THEN just change the mount point when you want to switch distros.

Hmmm

---

