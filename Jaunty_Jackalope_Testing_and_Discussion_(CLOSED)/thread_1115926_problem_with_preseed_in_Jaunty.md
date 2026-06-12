---
title: "problem with preseed in Jaunty ?"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dorfsmay on 2009-04-04
I am trying to install Jaunty with my Intrepid preseed file, and it does not recognize my partman-auto rule:

d-i partman-auto/disk string /dev/sda

d-i partman-auto/method string lvm

d-i partman-lvm/device_remove_lvm boolean true

d-i partman-lvm/confirm boolean true

d-i partman-auto/choose_recipe select atomic
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true

The presee install stops and ask me for information about the partition:
------------------------------------------------------------------
Partition disks

You may use the whole volume group...
.../...
Amount of volume group to use for guided partitioning:
------------------------------------------------------------------

Is the atomic recipe broken ? Is this a bug, or is there a new syntax for this ?


Thanks.

---

### Post by dorfsmay on 2009-04-04
I changed:

> **dorfsmay said:**
> 

d-i partman-auto/method string lvm



to:

d-i partman-auto/method string regular

And now it works. "lvm" worked for sure with Intrepid, I think this is a bug, and will log it in launchpad, unless somebody can come up with an explanation here...

---

