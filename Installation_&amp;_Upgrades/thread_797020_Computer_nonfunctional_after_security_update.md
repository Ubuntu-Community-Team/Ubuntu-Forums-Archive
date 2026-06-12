---
title: "Computer nonfunctional after security update"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by karldiechmann on 2008-05-16
I recently did a simple security update of my Ubuntu.  Though I can't know for sure that's what caused the problem, my installation is now seriously messed up.  The Desktop Environment won't load, and apt-get and gdebi, and probably other programs, refuse to function.  Also, Lynx won't connect to the internet.

Gdebi and apt-get complain about a problem in loading, if I recall correctly, /usr/lib/libgthread-2.0.0.so.2.  Even if I missed a few letters or digits, the problem is definitely libgthread, which is a part of gconftool, the configuration program for Gnome.  This would explain why my computer is so thoroughly hosed.

I imagine that what would fix the computer would be replacing libgthread.  The problem: how am I supposed to do this without using deb packages?  Remember, gdebi doesn't work, so I either need a different tool or I need a tarball.

I'm sorry I couldn't dig up more information.  All I know for sure is this:
* After I tried to update Ubuntu, Checkgmail, Gnome Terminal, and the System Monitor refused to launch.  Also, the update manager failed to finish installing the next item, nautilus-data.
* When I restarted the computer, the GUI failed to load and apt-get complained about the lack of the libgthread so.

---

### Post by Aearenda on 2008-05-16
I suggest you boot into recovery mode, get into the root command line and do this:
```
ls -l /usr/lib/libgth*
```
The output on Hardy looks like this:
```
lrwxrwxrwx 1 root root     26 2008-04-10 09:40 /usr/lib/libgthread-2.0.so.0 -> libgthread-2.0.so.0.1600.3
-rw-r--r-- 1 root root  14296 2008-04-09 00:59 /usr/lib/libgthread-2.0.so.0.1600.3
-rw-r--r-- 1 root root 505748 2008-04-10 08:36 /usr/lib/libgthumb.so

```

If yours is different, please post it.

---

### Post by karldiechmann on 2008-05-16
It's exactly the same.  However, further research suggests that libgthread might not be the root problem.  The original error message:
```
sudo gdebi /var/cache/apt/archives/nautilus-data*0ubuntu6*.deb
...
gdebi: error while loading shared libraries: /usr/lib/libgthread-2.0.so.0: invalid ELF handler
```

New message:
```
vim
vim: error while loading shared libraries: /usr/lib/libgobject-2.0.so.0: invalid ELF handler
```

---

### Post by Aearenda on 2008-05-16
Doesn't sound good. Are you able to reboot into an earlier kernel from the GRUB menu?

---

### Post by karldiechmann on 2008-05-16
No earlier kernels.  There used to be older kernels listed, but they've disappeared from the menu at some unknown point in the past.  (Windows XP would disappear from time to time to, though it hasn't done so in a while.)

---

### Post by Aearenda on 2008-05-16
So maybe it was the kernel upgrade that has failed, and things are confused. My Hardy has 2.6.24-16 currently, and older ones are present - but I installed alpha 6. What does 'ls /boot' show?

---

### Post by karldiechmann on 2008-05-16
For some context on installation I'll list what I've had before.  I started with a clean install of Gutsy, then upgraded a few weeks ago to Hardy.  As for /boot, I have:
```
karldickman@karldickman-laptop$ ls /boot
abi-2.6.22-14-generic
abi-2.6.24-16-generic
config-2.6.22-14-generic
config-2.6.24-16-generic
grub
initrd.img-2.6.22-14-generic
initrd.img-2.6.24-16-generic.bak
initrd.img-2.6.22-14-generic
initrd.img-2.6.24-16-generic.bak
memtest86+.bin
system.map-2.6.22-14-generic
system.map-2.6.24-16-generic
vmlinuz-2.6.22-14-generic
vmlinuz-2.6.24-16-generic

```

I had to copy it all manually (I'm posting using my Windows partition), so any typing errors are my problem, not the OS's.

---

### Post by Aearenda on 2008-05-17
I think you have one .bak in the wrong place, and it probably really looks like this:```
karldickman@karldickman-laptop$ ls /boot
abi-2.6.22-14-generic
abi-2.6.24-16-generic
config-2.6.22-14-generic
config-2.6.24-16-generic
grub
initrd.img-2.6.22-14-generic
initrd.img-2.6.24-16-generic
initrd.img-2.6.22-14-generic.bak
initrd.img-2.6.24-16-generic.bak
memtest86+.bin
system.map-2.6.22-14-generic
system.map-2.6.24-16-generic
vmlinuz-2.6.22-14-generic
vmlinuz-2.6.24-16-generic

```
Sadly, it doesn't offer us much to work with. I would try this next:
```
mv /boot/initrd.img-2.6.24-16-generic /boot/initrd.img-2.6.24-16-generic-bad
mv /boot/initrd.img-2.6.24-16-generic.bak /boot/initrd.img-2.6.24-16-generic

```
And then reboot. This drops back to the older initrd. It's worth trying just in case, but I don't really think it will work, since the problem seems to be the kernel's ELF handler, and I don't think this will fix it.

If that does not work, I would go into /boot/grub/menu.lst and add the gutsy kernel in, and try booting that. Here's what I would add, below the Hardy entries:
```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (fix this to be the same as Hardy)
kernel          /boot/vmlinuz-2.6.22-14-generic root=(same as Hardy) ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (same as Hardy)
kernel          /boot/vmlinuz-2.6.22-14-generic root=(same as Hardy) ro single
initrd          /boot/initrd.img-2.6.22-14-generic

```

If it works, then you can try fixing the failed updates, perhaps with 'sudo apt-get -f'. However, this way of booting may also not work, since the kernel modules for Gutsy might have been deleted in the upgrade -  'ls /lib/modules' will tell whether it is worth trying.

After these, the next thing I would try is to start up on the Desktop live CD, mount the hard drive's / partition (and /boot if it separate), chroot into / and try reinstalling the kernel. More details if you want.

I suspect with persistence the problem is fixable, but you may save time and effort by reinstalling. If you have /home on a different partition, this will be straightforward (reinstall with a new /home in the / partition, and mount the old /home afterwards); otherwise you will need to copy it somewhere else first. The method depends on how big it is.

---

### Post by Aearenda on 2008-05-17
Perhaps we should have done this sooner - does yours match: ```
 ls -l /usr/lib/libelf*
lrwxrwxrwx 1 root root    15 2008-04-03 19:31 /usr/lib/libelf.so.0 -> libelf.so.0.8.6
lrwxrwxrwx 1 root root    15 2008-04-03 19:31 /usr/lib/libelf.so.0.8 -> libelf.so.0.8.6
-rw-r--r-- 1 root root 76572 2007-10-03 05:53 /usr/lib/libelf.so.0.8.6

```

---

### Post by karldiechmann on 2008-05-17
The only difference is that my dates for libelf.so.0 and libelf.so.0.8 are 2007-10-24 19:09.  Everything else is the same.

---

### Post by Aearenda on 2008-05-17
OK, that just reflects the installation date - mine was a new installation of Hardy Alpha 6.

---

### Post by Aearenda on 2008-05-17
If you want to have a go at recovering using the chroot method, I've found a howto at [http://sudan.ubuntuforums.com/showthread.php?t=743658](http://sudan.ubuntuforums.com/showthread.php?t=743658). I'd try the method in post 3. To make this work, you boot on the liveCD, then start a terminal and do
```
sudo -i
mkdir /chroot
# Note: Replace /dev/sdxy in the following with your root partition, eg sda1
# This assumes you do NOT have a separate /boot partition
mount /dev/sdxy /chroot
chroot /chroot
mount /proc
mount /sys
mount -t devpts none /dev/pts

# Note: now you can do whatever you need to recover the system
# I suggest this for starters:
apt-get -f

# What comes next depends on what apt-get did. There will probably be more to do, such as 
apt-get remove linux-image-2.6.24-16-generic

# Note what gets uninstalled automatically, and add them to the next one...
apt-get install linux-image-2.6.24-16-generic

# Really can't say what else will be needed yet...

# When finished...
umount -lf /proc
umount -lf /sys
umount -lf /dev/pts
exit
umount /chroot

# And reboot to see if it works!

```
You don't have to copy the comments, of course. And I haven't tested any of this :-)

---

### Post by karldiechmann on 2008-05-17
I tried changing /boot/grub/menu.lst to boot to an earlier kernel.  To my surprise, version 2.6.22-14 was the default kernel, rather than the later one.  Unfortunately, booting into the later kernel did not remove the ELF problem.  Is it possible that there's something wrong with libelf that ls -l didn't detect?

---

### Post by karldiechmann on 2008-05-17
I'm trying the chroot method now.  I assume that by /dev/sdxy you mean whichever hard drive my Ubuntu is on, which is /dev/sda1.

---

### Post by karldiechmann on 2008-05-17
Two problems, though I am trying to figure them out independently:
```

root@ubuntu:~# mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
root@ubuntu:~# chroot /chroot
chroot: cannot run command `/bin/bash': No such file or directory

```

---

### Post by karldiechmann on 2008-05-17
Ahh, silly me.  Should have used
```

root@ubuntu:~# mount /dev/sda1 /chroot

```

When all else fails, follow the directions.

---

### Post by karldiechmann on 2008-05-23
Sorry for not replying sooner.  I still wasn't able to fix anything, so I decided to reinstall.  Unfortunately, the chroot method did not work because apt-get was also affected by the problem with ELF headers, and couldn't reinstall the kernel.  Thank you so much for your help, anyway.

---

### Post by Aearenda on 2008-05-23
Oh well - it's a trade-off of time in the end - I hope the updates run properly for you this time!

---

