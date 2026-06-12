---
title: "(initramfs) _"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by st0n3cutt3r on 2008-03-09
I need help starting Ubuntu from busybox.  I just did an upgrade install, and I can still boot into the old version from yaboot, but the new version drops me at busybox with a prompt:

(initramfs) _  


anyone know how to boot to the gui from here?  I am almost positive everything in the OS is fine, the upgrade completed with no errors, just need to startx (I think)

Thanks!

---

### Post by Pumalite on 2008-03-09
Try:
Ctrl+Alt+F1 to get command line (I'm not sure is an xserver problem, but)
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as the driver, then: startx
(cross your fingers)

---

### Post by st0n3cutt3r on 2008-03-09
**ls** gets me:

```
dev      sbin      lib      init       var        etc      sys      tmp
root     conf      bin      scripts    modules    usr      proc
```

**env** gets me a whole list of info, but I can't see the first character in each row because of the screen offset, so I'll list what I see with _ in place of the first letter:

```
_initramfs) env
_OME=/
_PKG_ARCH=powerpc
_nit=/sbin/init
_ROGRESS_STATE=2
_S1=(initramfs)
_ebug=
_ERM=linux
_reak=
_uiet=y
_PATH=/usr/local/bin:usr/bin:/sbin:/bin
_esume=UUID=4209caf3-4de9-40ec-85d7-e2a9f80d82e3
_ryptopts=
_WD=/
_eadonly=y
_OOT=/ev/hda3
_ootmnt=/root
```



(same deal as above with the _ ) **mount** gets me:

```
_one on /sys type sysfs (rw,nosuid,nodev,noexec)
_one on /proc type proc (rw,nosuid,nodev,noexec)
_dev on /dev type tmpfs (rw)
_usectl on /sys/fs/fuse/connections type fusectl (rw)
```

any ideas?

---

### Post by st0n3cutt3r on 2008-03-09
> **Pumalite said:**
> Try:
Ctrl+Alt+F1 to get command line (I'm not sure is an xserver problem, but)
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as the driver, then: startx
(cross your fingers)

Sorry, didn't see your message while I was writing mine. 
when I did Ctrl+Alt+F1 it said:

```
Loading, please wait...
        Check root= bootarg cat /proc/cmdline
        or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/hd3a does not exist. Dropping to a shell!
        Check root= bootarg cat /proc/cmdline
        or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/hd3a does not exist. Dropping to a shell!
        Check root= bootarg cat /proc/cmdline
        or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/hd3a does not exist. Dropping to a shell!
```

I entered ```
sudo dpkg-reconfigure xserver-xorg
``` and nothing happened....

---

### Post by Pumalite on 2008-03-10
I'd check my drives with TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by st0n3cutt3r on 2008-03-10
I got it to start x with 

```
modprobe ide-core
exit
```

but GNOME Settings Daemon crashes on load....  not really sure what's going on there...

---

### Post by Pumalite on 2008-03-10
Post your specs.I'd download an Alternate CD iso, follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Start from scratch. Do md5sum on iso, burn at 4x or less, use CD-R and reinstall.

---

