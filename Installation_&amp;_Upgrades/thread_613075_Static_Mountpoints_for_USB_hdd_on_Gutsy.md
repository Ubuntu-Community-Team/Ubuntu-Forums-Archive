---
title: "Static Mountpoints for USB hdd on Gutsy"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by dgray_from_dc on 2007-11-14
I'm using Gutsy in an attempt to put together a file server with a 4 x 250G RAID 5 array.  My problem is that I'm using IDE to usb interfaces and can't force Linux to assign static /dev/*** mountpoints.  As such, I can't configure mdadm to use my drives because they move around.  I found this thread.

[http://ubuntuforums.org/showthread.php?t=91948&highlight=static+mountpoint](http://ubuntuforums.org/showthread.php?t=91948&highlight=static+mountpoint)

But as my post there states, something has changed with the output of the udevinfo command.

```
udevinfo -a -p $(udevinfo -q path -n /dev/sda)
```

Once I get the mountpoint thing nailed down, I want to use EVMS (which I installed, used, and had problems with because of the mountpoints I think, and uninstalled) so that my array will be expandable.

At this point, I'm just playing with settings and programs to figure out what's best.  I'm using USB so that I'll have hot-swap capability without having to pop for SCSI drives.  I think I have everything else in hand, it's just this pesky mountpoint problem.

---

### Post by dgray_from_dc on 2008-01-13
Thought I'd revive the question.  As my post here indicates

[http://ubuntuforums.org/showpost.php?p=4105232&postcount=20](http://ubuntuforums.org/showpost.php?p=4105232&postcount=20)

I built my array without static mountpoints and used EVMS on Dapper.  The array turned out to be useable, but unstable when dealing with other USB drives.  I think that this is due at least in part to dynamic mountpoints when dealing with USB drives.

I'd like to tie down any loose ends I can before trying again.

---

### Post by dgray_from_dc on 2008-01-13
bump

---

