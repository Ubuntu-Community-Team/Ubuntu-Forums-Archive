---
title: "Partition mounting and naming issues."
date: 2006-05-29
forum: Installation &amp; Upgrades
---

### Post by sudomania4 on 2006-05-29
I have dapper and windows installed, and lately, when i log into dapper, my "computer" looks like the screenshot (see below). 

Everything not in squares shouldn't be in "computer", ever. The things in blue squares should only show up when the device is plugged in, otherwise they should be invisible. The things in red squares are shown in my /etc/fstab:  
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5    /media/shared   vfat   iocharset=utf8,umask=0000   0   0
```

/etc/mtab:  
```

/dev/hda4 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-23-386/volatile tmpfs rw 0 0
/dev/hda5 /media/shared vfat rw,iocharset=utf8,umask=0000 0 0

```
Also, the "51.9 GB Volume: Root Volume" is the same as "Filesystem", and im not sure why they both show. 

One more issue: the one partition in green, should be there, and is, but i wasnt to change the name. I dont know how. The name used to be "14.0 GB Volume: shared" and is mounted in /media/shared. However, it is named _PNG with a box.

So, please help me hide the drives that are in blue unless they are plugged in, and help me hide the partitions without squares, and help me rename _PNG, the partition in green. Sorry this is so confusing, if you need any more information, fell free to ask.

These people seem to struggle with similair problems: [http://ubuntuforums.org/showthread.php?t=181923](http://ubuntuforums.org/showthread.php?t=181923)

---

### Post by sudomania4 on 2006-05-30
By the way, i found a bug report on the  issue in launchpad: [https://launchpad.net/distros/ubuntu/+bug/47349](https://launchpad.net/distros/ubuntu/+bug/47349), so maybe its not somethhing i did...or can fix...

---

### Post by sudomania4 on 2006-05-30
Also i was informed that the date modifyed on _PNG was wrong, and it is.

---

### Post by sudomania4 on 2006-05-30
the _PNG naming issue resolved itself. I think that removing everythingg for the "system volume information" folder inside that partition fixed it. The problem of duplicate mounts and unneeded mounts persists.

---

### Post by Shawn Yarbrough on 2006-06-12
I too am having upgrade problems, related to PCMCIA.  This is a server box and as far as I know it doesn't even support PCMCIA, but when the upgrade process reached "configuring pcmcia-cs support" (I think was what it said) was when it locked up.

Eventually (half an hour ago) I gave up waiting and rebooted cold.  Now the system gives many errors during the boot process and finally fails trying to start up PCMCIA services.

So now I'm embarassed because the SuSE fanatics I work with have another reason to slam Ubuntu.  I'm going to try burning an Ubuntu CD on another box but... oops... the Ubuntu server was also my primary CD burning box.

Maybe people should try disabling PCMCIA before installation?

---

