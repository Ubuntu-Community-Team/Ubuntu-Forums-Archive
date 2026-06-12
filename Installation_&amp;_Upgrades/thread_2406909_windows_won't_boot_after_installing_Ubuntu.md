---
title: "windows won't boot after installing Ubuntu"
date: 2018-11-27
forum: Installation &amp; Upgrades
---

### Post by reut2 on 2018-11-27
I'm running Ubuntu 18.04.1 LTS on a Toshiba Satellite C875-S7205 Laptop with dual boot.

The laltop was originally Windows7, and it was updated to Windows10.  I did not realize  that the default was hibernation mode when shutting down Windows.  Also in order to re-partition the hard drive, I deleted the recovery partition.  After installing Ubuntu, the grub menu cam up with Windows10, Windows7, and the usual ubuntu boot options.  

When I select windows 10 from the grub menu, Ii loops back to the grub menu.  I have created a windows10 recovery usb stick.  It boots up.  I tried every option on the menu, but I get messages to the effect that it cannot fix the system.  I tried the reinstall windows option, and now i get a blank screen with a blinking cursor at top.

Does anybody know how I can get windows working again on this laptop?

fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installationuN
UUID=bbcfa370-972b-40a3-9602-7db31bc47a8e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=6afb7ff8-3d2c-4f47-86f6-f8458a7ce1bc /home           ext4    defaults        0       2
# /home/MyDocuments was on /dev/sda6 during installation

UUID=5CD7D62C79361B95 /home/MyDocuments ntfs-3g   permissions     0       1
# /home/Windows10 was on /dev/sda1 during installation

UUID=F6B4C7B8B4C77A1F /home/Windows10    ntfs-3g   permissions     0       1
# /home/windows7 was on /dev/sda2 during installation
UUID=C470EDD770EDD06A /home/windows7  ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda7 during installation
UUID=2a4c7082-92ca-4898-8694-7a575ce61ce0 none            swap    sw              0       0                      
```

---

