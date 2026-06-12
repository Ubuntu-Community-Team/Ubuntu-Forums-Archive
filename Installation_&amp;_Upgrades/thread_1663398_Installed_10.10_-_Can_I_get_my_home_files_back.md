---
title: "Installed 10.10 - Can I get my /home files back?"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by landsg on 2011-01-09
Hi All:

After installing Ubuntu 10.10 yesterday (previously 9.04), my /home folder is empty.  My /home folder under 9.04 was already on its own partition.  I left it that way during the install, but I did change it to ext4.  

My question is did I accidentally erase everything by doing that?  I have rebooted via the live CD and used gparted to make the partition ext3 again to see if anything would change, but no luck.

I didn't have a lot on this particular computer, so it's not a huge loss, but if anyone can help out I would appreciate it.  Can I revert back to my old install?

See output below:

FSTAB

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
/dev/sda5       /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=63cd9c37-0a0c-4ba9-bf41-1cf1e68dcc1a none            swap    sw              0       0


FDISK

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
/dev/sda5       /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=63cd9c37-0a0c-4ba9-bf41-1cf1e68dcc1a none            swap    sw              0       0

---

### Post by BicyclerBoy on 2011-01-09
If you changed the filesystem of the old "home" partition, I would think you trashed it..

Try changing the filesystem back & see if you can access any data.
I wouldn't rate your chances tho'.

Why did you not just backup the /home folder to DVD/other partition ?

---

### Post by ottosykora on 2011-01-09
the change to ext4 did format the partition, this is why you dont see any data there now. 

But the hope is not lost! The data is still there (most of it), only the file system did change and so it can not be displayed.

Now you could try something like testdisk and recover the original ext3 partition, this could bring the data back. Formating does not wipe the data, just the file directory. So files are sill here. Try to run testdisk from some boot media. PartedMagic for example or similar.
But you could well use also some data recovery software tools to find 'deleted' files ( Photorec)

[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)



[http://www.linuxdiskrecovery.com/](http://www.linuxdiskrecovery.com/)

[http://www.r-tt.com/data_recovery_linux/](http://www.r-tt.com/data_recovery_linux/)

[http://www.easeus-linuxrecovery.com/](http://www.easeus-linuxrecovery.com/)

[http://www.freeware-download.com/downloaddetails/15296.html](http://www.freeware-download.com/downloaddetails/15296.html)

---

### Post by landsg on 2011-01-09
Thanks so much!  I will give these things a try and see what happens.

---

