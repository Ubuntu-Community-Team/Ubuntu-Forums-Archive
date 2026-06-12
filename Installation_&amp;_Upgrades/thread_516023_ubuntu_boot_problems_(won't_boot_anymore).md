---
title: "ubuntu boot problems (won't boot anymore)"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by macaholic on 2007-08-02
I have had ubuntu 7.04 installed for 3 days now on my mac pro and it has more or less been working fine. However now when I boot, the Ubuntu logo comes up and the loading bar takes forever to finish. Once ot does it shpws this white-on-black text screen which is what appears to be what is happening during the boot. All the lines have an [Ok] going down except when It gets to:

* Mounting local filesystems...
[mntent] : line 8 in /etc/fstab is bad
* Activating swapfile swap...                                   [OK]
* Configuring network interfaces...                         [OK]
- runit : leave stage : /etc/runit1
- runit : enter stage : /etc/runit2

After that it just sits there and you can type stuff as if it were a command line but it is unresponsive. I booted from the live cd and this is what my /etc/fstab reads (blank space marks end of a line not there in reality) :

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda3

UUID=3c827c78-9194-48b1-94a9-4829cd499630 /               ext3    defaults,errors=remount-ro 0       1

# /dev/sda1

UUID=2860-11F4  /media/EFI      system  partition       vfat    defaults,utf8,umask=007,gid=46 0 1

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

That would make line 8 this :
UUID=2860-11F4  /media/EFI      system  partition       vfat    defaults,utf8,umask=007,gid=46 0 1
I have no idea what to do and I would rather not reinstall ubuntu completly so any help on this matter would be very much appreciated. 
I also read somewhere that a similar problem can be fixed by deleting the comments? If that holds any truth how would I edit it if it is a read only document unless I am logged in? 
Thanks in advance.

---

### Post by macaholic on 2007-08-02
Oh well I'm just going to start over again with ubuntu studio instead

---

