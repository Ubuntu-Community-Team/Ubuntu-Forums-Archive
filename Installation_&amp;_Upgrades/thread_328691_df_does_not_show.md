---
title: "df does not show /"
date: 2006-12-31
forum: Installation &amp; Upgrades
---

### Post by justfred on 2006-12-31
This is the second Efty Edge installation I perform. Unlike the first one that went flawlessly, this one seems to have been more problematic. The difference between the two PC's is that this one has two sata drives whereas the first one only had one IDE drive.

First note that I needed to patch /boot/grub/menu.lst manually as  the as the path to root was not correct by default : installation used root=/dev/hda1 in lines :
> kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
I patched it to root=/dev/sda1.

note that I had to redo this after the updates where installed. I now also changed the line :
> # kopt_2_6=root=/dev/hda1 ro
to
> # kopt_2_6=root=/dev/sda1 ro
Now, as far as I can tell,  I'm left with the problem that df does not show /, e.g.

> $ df 
Filesystem           1K-blocks      Used Available Use% Mounted on
varrun                  387404        84    387320   1% /var/run
varlock                 387404         0    387404   0% /var/lock
procbususb               10240       136     10104   2% /proc/bus/usb
udev                     10240       136     10104   2% /dev
devshm                  387404         0    387404   0% /dev/shm
lrm                     387404     17580    369824   5% /lib/modules/2.6.17-10-generic/volatile
/dev/sdb1             58990648  52462420   6528228  89% /media/sdb1
/dev/hdc               3921760   3921760         0 100% /media/cdrom0

however when explicitly requested it seems to work :

> $ df /
Filesystem           1K-blocks      Used Available Use% Mounted on
-                     76557088   6411208  66256948   9% /
but note that the filesystem only shows as '-' and not as e.g. '/dev/sda1'

I found this (relatively old (2001)) debian bug -[here]("http://groups.google.be/group/debian.bugs.dist/browse_frm/thread/65ddcb698c151456/45602de5028d249f%2345602de5028d249f")-  but I am not sure that this applies (and how).

My /etc/fstab file looks like this :

> $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1bd613e5-99ef-4bb9-9c09-a6c57f629960 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b903d098-819f-40d9-8566-60d397559202 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

# /dev/sdb1
UUID=C688A41C88A40D4D   /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

Any ideas ?

---

