---
title: "Moving from Ubuntu 7.10 to 8.04 + truecrypt + headaches"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by pgjensen on 2008-07-15
I'll start off with how my 7.10 system is setup:

truecrypt 4.3a built from source.  i have used multiple kernels, including 2.6.22 that came with 7.10, 2.6.24.4, 2.6.25.9, 2.6.25.10, 2.6.26.6 (currently using).

i have 2 highpoint hardware raid controllers setup as /dev/sda1 and /dev/sdb1, both with GPT partitions to break the 2tb limit.

i have an LSI SAS HBA that has multiple drives in an MD RAID6 volume, /dev/sd[c-r]1 with FD partition tables on each.

everything works ok as long as i'm using old truecrypt 4.3a and not truecrypt 5-6.0a (locks up when writing for long periods of time).



i now take this system, replace the hard drive to save the old install, and install 8.04.

i compile old truecrypt 4.3a, new 6.0a, the 2 hardware raid drivers so they'll show up, and the LSI SAS HBA (module in kernel).

when going to mount my truecrypt volumes, it now does not allow me to do it.  it says (invalid password or truecrypt device).  parted shows the devices have proper partitions setup.  nothing has been written to those drives since mounted on 7.10 (clean unmount).


if i mount NEW truecrypt volumes (XTS), created with 5.0+, they mount OK using 6.0a or 5.0+... however, if I use 6.0a to mount the old truecrypt 4.3a volumes, again, they are not recognized.


if i put the old hdd in, truecrypt 4.3a can still mount the drives using 7.10.




i really am having a tough time figuring out why 8.04 wouldn't mount the drives when 7.10 would.  I am testing with the SAME kernel versions.  could it be some program that is interfering with the raid devices?  ugh!



help if you can :confused:

---

### Post by pgjensen on 2008-07-20
no love?

---

