---
title: "Installer wrote grub into mdadm disk"
date: 2012-10-27
forum: Installation &amp; Upgrades
---

### Post by gururug on 2012-10-27
Upgrade from 10.x to 12.x trashed my OS > Re-install fresh 12.x. 

Disabled my 3 mdadm disks in bios prior to install > Ubuntu installer still "sees" them.

Manually tell it to repartition the SSD/OS drive ( sdd ) > OK

Write grub? Yes > Writing to /dev/sda !!!!!!!!!! WTF!!! You'd think it would've figured out I wanted the OS etc. in sdd...... > Bummer.

Boot recovery > Tell it root is /dev/sda1 > Write grub to /dev/sdd > OK.


Question______________________

Will my 3 disk raid0 mdadm array be trashed now that the installer wrote grub into the MBR?

Fix linky?


Cheers All.

---

### Post by darkod on 2012-10-27
Are you installing the server version or desktop? Because if you installed the desktop and used manual partitioning, at the bottom of the partitioning step is the drop down box for bootloader destination. If left at /dev/sda, that's what it will do.

No, I don't think the array is messed up because a bootloader was written. It shouldn't be related to the health of the array.

Assemble the MD devices and see. I guess you would want to activate them now. If you don't know, don't use the --create command in mdadm. Now that you have existing array you use --assemble, like:
sudo mdadm --assemble --scan

That will scan all disks for mdadm data and assemble all devices found.

---

### Post by gururug on 2012-10-27
Update: Mdadm array has been automatically detected and mount and seems ok.

Thanks darkod for the help. Install was Server 64 12.x. 

Maybe something for the installer devs to do some tweaking on.

Note to self and others....DISCONNECT all drives before running install.

---

### Post by darkod on 2012-10-27
I haven't tried it, but I think that if you want to control the bootloader device you need to do this during the server install:
When it asks if you want to install the bootloader (towards the end), say NO. Yes, of course you want a bootloader, but I think saying No will make it ask you where you want it installed.

---

### Post by gururug on 2012-10-28
THanks again darkod

---

