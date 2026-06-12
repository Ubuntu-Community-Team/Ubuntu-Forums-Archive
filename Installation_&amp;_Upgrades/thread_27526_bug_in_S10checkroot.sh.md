---
title: "bug in S10checkroot.sh"
date: 2005-04-16
forum: Installation &amp; Upgrades
---

### Post by suoko on 2005-04-16
Hi, 
I guess I have a buggy S10checkroot.sh since auto fsck doesn't work for me (I use reiserfs).
When I uncorrectly shutdown my machine causing a non clean filesystem I get not auto fsck at boot at all (with no meassages at boot).
And if I shutdown the machine with the command "shutdown -F -r now" I got a message "Fast boot, no file system check" during boot !!!

since i installed hoary when it was in develpment maybe the S10checkroot.sh I have is buggy. Cuold anyone provide me this script taking it from a fresh install of a stable hoary installation?


thanks

---

### Post by suoko on 2005-04-18
THIS IS MY FSTAB
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               reiserfs notail,user_xattr          0       1
/dev/hda8       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0
/dev/hda6       /mnt/arch       reiserfs defaults       0       0
/dev/hda1       /mnt/win        vfat    defaults        0       0
/dev/hda5       /mnt/vfat       vfat    iocharset=iso8859-1,codepage=850,uid=1000,gid=1000,umask=2 0 0


Attached you can find my S10checkroot.sh:

---

### Post by suoko on 2005-04-25
NEWS:
automatic check at boot has worked today (still have to double check if it was an "accident" or it's now working).

The main change I've done recently is enabling the root user.

---

