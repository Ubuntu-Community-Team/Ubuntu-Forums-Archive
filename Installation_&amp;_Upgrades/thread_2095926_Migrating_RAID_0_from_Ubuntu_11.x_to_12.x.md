---
title: "Migrating RAID 0 from Ubuntu 11.x to 12.x"
date: 2012-12-18
forum: Installation &amp; Upgrades
---

### Post by Uberman on 2012-12-18
Hey, guys.

I have a software RAID 0 configuration with two 2TB drives (4TB RAID 0). My Ubuntu 11.x installation appears to have been hacked (my /etc/mtab file is hosed and inaccessible), so I am putting together a new OS installation with Ubuntu 12.x with which I plan to just "hot swap" the existing drive, which means it has all the installed software, configurations, IPv4 address and hostname.

However, I'm a little nervous with the software RAID. I'm going to run the mdadm command:

```
mdadm --assemble --scan --auto-update-homehost
```

to have the new OS automatically put the RAID drives back together ("fdisk -l" shows them as accessible in the 12.x OS). The data on the RAID is not irreplaceable, but it has literally taken me years to assemble its 3TB of data, and I'd rather not lose it.

My question is: If I run the above mdadm command within the new Ubuntu 12.x OS to test its ability to recover the RAID, and it overwrites the existing metadata, will that prevent me from using the RAID again with the original Ubuntu 11.x installation?

I'm assuming I could just run the mdadm assemble command again with the Ubuntu 11.x OS to revert the metadata, but I want to make sure that the actual data on the RAID is not going to be impacted by my testing actions during the incremental migration.

Thanks for your insights.

---

### Post by darkod on 2012-12-18
I don't think you need the last option. The --assemble --scan shouldn't touch any meta data or any data on the array.
What you should be careful about is running mdadm --create because that is used only once when the array is originally created and it destroys data in the process. Never use it on existing arrays.

Also, the live cd installer doesn't include the mdadm package and can't recognize the array during install. You can either boot into live mode, add the package and assemble the array, and only then start the installation with the desktop icon, or, simply install on another disk ignoring the array, and then add mdadm package and assemble it. You will also have to create a mount point for it and an entry in /etc/fstab.

I think you will also need to update the initramfs so that the array is assembled every time on boot, something like:
sudo update-initramfs -u

---

### Post by Uberman on 2012-12-18
I actually have /etc/init.d scripts that mount and unmount the RAID before (and after) dependencies when the operating system starts, and that has worked just fine for the 11.x version.  I've already migrated that over to 12.x.

Thanks for the info, though.  I'll give it a try -- I suppose I'll be holding my breath in any case.  :)

---

