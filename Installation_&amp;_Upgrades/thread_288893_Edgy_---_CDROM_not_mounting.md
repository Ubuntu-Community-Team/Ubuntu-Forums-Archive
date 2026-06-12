---
title: "Edgy --- CDROM not mounting"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by arnor on 2006-10-30
hi, 
i have a problem with my cd-rom, it doesn't mount...its like edgy doesn't see it...
can you help me? here is my fstab...
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=a715d933-33ce-4158-9aef-578b1b32bc0c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=F08873FC8873C020 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=685D-3497  /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=388fb73d-10a7-48e7-97ca-a743a7e68d55 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


```

---

### Post by arnor on 2006-10-30
Ok,
i try mount /media/cdrom0 and it mount it...but its no auto...what can i do?

---

### Post by arnor on 2006-10-30
this is my mtab file 
```

/dev/hda6 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-generic/volatile tmpfs rw 0 0
/dev/hda1 /media/hda1 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/hda3 /media/hda3 vfat rw,utf8,umask=007,gid=46 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/hdb /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=arnor 0 0

```

---

### Post by arnor on 2006-10-30
is that a known edgy bug?
the automount doesn't work...i did gconf-editor, everything is on and ok...only it doesn't work, please help...

---

### Post by arnor on 2006-10-30
i installed "ivman" and it almost works...so its gvm who is buggy...

---

### Post by BLTicklemonster on 2006-10-30
I went straight to my device in media, and right clicked (while there was a disk in it) and clicked on mount. Ever since then, it's worked fine.

---

### Post by arnor on 2006-10-30
you went to /dev/hdb ? and mount it? with nautilus?
thx i try...
i did it...but when i eject it, the icon stay on the desktop...and when i reinsert nothing happened. what a hell...](*,)

---

### Post by arnor on 2006-10-30
would it change something if i install xubuntu? the bug is in the new Gnome 2.16?

---

### Post by cbrack on 2006-10-31
I'm having the same problem with Kubuntu... I assume it is Edgy specific.  I'm going to try some different stuff tonight and hopefully I can get it working.

---

### Post by BLTicklemonster on 2006-10-31
I have a dvd and a dvdrw, and have done nothing to them (other than putting a disk in each, then navigating to them and clicking "mount" ) and they both pop right up when I put a disk in them.

For once, I got lucky.

---

### Post by arnor on 2006-10-31
nothing made it ... yet ... i ll wait an idea or an update... ;-)

---

### Post by rvgarcia on 2007-03-19
Wow, same problem here with mounting. I tried installing Gnome and KDE and I got the same problem when installing (No Mounting) It totally seems like a bug. I might see if I can find a different distro too. Maybe Fedora. Any luck, please let me know.

---

