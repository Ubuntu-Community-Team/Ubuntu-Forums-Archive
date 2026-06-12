---
title: "Serveral Bug/Config Issues with 6.10"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by sscotti on 2006-11-25
Hi,

I just installed 6.10 and things are good except for a few bugs or configuration issues.

1.  I have a Logitech Bluetooth mouse and keyboard, a MX5000 which works find on windows and which was working OK under 6.06.  When I installed 6.10 with a clean install I encountered an issue where the mouse and keyboard are unresponsive in the login screen.  I can usually type in part of the username and by that point they both die.  If I remove and reinsert the USB bluetooth receiver they both become responsive in about 20 seconds.

2.  I tried to edit my FSTAB file to mount 2 windows partitions that I have on another disk.  The FSTAB is here:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=3133e5e6-ac1d-4391-be7e-c307b9bc593c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=ce21fada-9ded-41fe-bb08-6766faaf52f5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1	/media/windowsos	ntfs-3g    defaults,locale=en_US.utf8    0    0
/dev/hda5	/media/windowsarchive	ntfs-3g    defaults,locale=en_US.utf8    0    0

The system added the UUID.  I added the section for ntfs-3g.  The driver and components are install, and the partitions references are correct.  I was hoping that this might just be a configuration problem.  Otherwise, I can revert back to the ntfs driver.  I wanted to try the 3g because I don't mind trashing my windows volumes and wanted to try the write function here.

3.  Trouble getting services and modules to load at boot time.  I was using Webmin to manage these, but Webmin isn't working (runlevel is stuck at 0) and I can't edit anything in Webmin.  This is in a another post.

Any help appreciated.

---

