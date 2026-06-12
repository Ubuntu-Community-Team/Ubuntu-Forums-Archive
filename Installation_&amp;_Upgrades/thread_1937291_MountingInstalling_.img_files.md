---
title: "Mounting/Installing .img files"
date: 2012-03-07
forum: Installation &amp; Upgrades
---

### Post by mouse- on 2012-03-07
I have been attempting to install Papercut on my computer {Ubuntu 11.10}, however the people who created the papercut system I need to connect to only provide access to the .dmg and .exe versions of Papercut.  I downloaded the .exe version and ran it with wine, but it couldn't connect to the wireless printer system, so I attempted to mount the .dmg version.  I got as far as converting it to a .img file, but I can't get the .img file to mount.  I tried ```
sudo mount -t hfsplus  -o loop mac-papercut.img /mnt/img

```
and got back 
```
 wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
Which was perhaps the closest I got to the correct command.  Does anyone know what the correct fs type is or what I'm doing wrong?

---

