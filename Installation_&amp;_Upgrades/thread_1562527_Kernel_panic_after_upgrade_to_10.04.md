---
title: "Kernel panic after upgrade to 10.04"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by akapi on 2010-08-27
Hello,
Since I upgraded my Dell XPS M1330 to Ubuntu 10.04, it doesn't boot anymore, but gives the following error message:

```
[   0.762279] kernel panic -not syncing: VFS: unable to mount root fs on unknow
wn -block(0,0)
```

If I try to boot in recovery mode, I get this:

```
libudev: udev_monitor_new_from?netlink: error getting socket: invalid argument
[    19.092186] wait-for-root[916]: segfault at 00000030 eip b7709f2b esp bff55eb
0 error 4
Segmentation fault
Gave up waiting for root device. Common problems:
 - Boot args (cat/proc/cmdline)
   - Check rootdelay= (did the system wait too long?)
   - Check root= (did the system wait for the right device?)
 - missing modules (cat/proc/modules: ls /dev)
Alert! /dev/disk/by-uuid/06731e27-47ac-4a83-aa05-b5cf2bb61748 does not exist. Dropping to shell!
```

I'm not quite sure what I did to cause that problem, but I think I may have upgraded directly from Ubuntu 8 to 10 without going through 9 first. Also, I used the automatic upgrade button rather than a complete re-install, which I understand now to be a bad thing. Do you have any advice for me?

I tried a couple of solutions suggested in other threads on this forum with similar problems, but without success.

For example, when I put 
```

sudo dpkg --configure -a
```
into the terminal, it just doesn't react at all.

Whereas 
```
sudo grub -install /dev/sda
```
gives me this:
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

The other stupid thing I did is not to backup my files before the upgrade. Is there any chance of getting at them from the live session?

Many thanks in advance!

---

### Post by akapi on 2010-08-28
Just to say that meanwhile I found the reply to my last question in the absolute beginners forum> [http://ubuntuforums.org/showthread.php?t=1236742&page=3](http://ubuntuforums.org/showthread.php?t=1236742&page=3)
:-\"
So, after getting myself a live CD with the latest Ubuntu version I was able to see my homefolder again, and with 
```
gksudo nautilus 
```
I was able to copy the data to an external drive. So I think I'll stop bothering about why the upgrade went wrong and why my computer won't boot and just do a clean install.

---

