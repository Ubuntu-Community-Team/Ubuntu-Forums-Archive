---
title: "Distro Upgrade Failed Miserably"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by anachronon on 2011-06-03
Hey All,

Yesterday, I tried to upgrade to v10.04 ("Lucid").  After nearly 15 hours of painfully slow downloading and installing, my computer froze, just as the upgrade was almost complete.  Needless to say, my Linux kernel is now wasted.

So, what is the best way to proceed?  I would like to get the OS going again, without losing any of my data or files.  I also have a Windoze partition on that HD, which needs to be preserved.  Any suggestions?  I would really like to avoid another 15-hour marathon session.  I suspect that insanely long time is what caused my computer to finally freeze.

Thanks everyone.

---

### Post by Joe of loath on 2011-06-03
Boot into a live CD, and try rescue the system using chroot. Open a terminal, and type:

sudo -i
mount -t proc proc /*partition*/proc
mount -t sysfs sys /*partition*/sys
mount -o bind /dev /*partition*/dev
chroot /*partition*/
cat nameserver 8.8.8.8 > /etc/resolv.conf
apt-get update
apt-get upgrade

Then go from there, as you would fix a borked installation normally.

---

### Post by anachronon on 2011-06-03
OK, I booted up with an old live CD.

I got as far as typing "mount -t proc proc /*partition*/proc"

And, the response was "/*partition*/proc does not exist"

---

### Post by Joe of loath on 2011-06-03
Well, yeah, it shouldn't :p. I forgot to mention that you should mount the hard drive, but once it's mounted, you need to replace *partition* with the mount point (Will be /media/(Disk-uuid)) :D

---

### Post by anachronon on 2011-06-03
OK, I got the mount commands working.  The Properties dialog box defined the mount point as simply "/media/disk"--no need for the long uuid.

However, when I got to the "chroot" command, I got "permission denied".  I was never prompted for a password.  Nor, could I find any way to enter one.  All the while, I was working under root--the "#" prompt.

---

### Post by Joe of loath on 2011-06-04
Could you post the full output of what you typed and what you got in response, please?

---

### Post by anachronon on 2011-06-04
Here is a copy of my terminal screen:



```
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount -t proc proc /media/disk/proc
root@ubuntu:~# mount -t sysfs sys /media/disk/sys
root@ubuntu:~# mount -o bind /dev /media/disk/dev
root@ubuntu:~# chroot /media/disk/
chroot: cannot run command `/bin/bash': Permission denied
root@ubuntu:~# 
```

---

### Post by Joe of loath on 2011-06-04
How strange... Maybe bash got corrupted?

---

### Post by anachronon on 2011-06-04
> **Joe of loath said:**
> How strange... Maybe bash got corrupted?
Any suggestions?

---

### Post by tukuyomi on 2011-06-04
Long shot: You try to use bash 64 bit on a livecd 32 bits?

---

### Post by anachronon on 2011-06-04
> **tukuyomi said:**
> Long shot: You try to use bash 64 bit on a livecd 32 bits?
No, I have no 64-bit stuff.  Only 32-bit i386.  Could it be because I am using two different versions of Ubuntu?  The live CD is an old v7.

---

### Post by Joe of loath on 2011-06-04
Although it shouldn't matter, I'd try a newer CD.

Also, if you use the same version, try copying /bin/bash from the live CD to the disk, and making sure the permissions are 655 and that it is executable.

---

### Post by anachronon on 2011-06-04
> **Joe of loath said:**
> Although it shouldn't matter, I'd try a newer CD.

Also, if you use the same version, try copying /bin/bash from the live CD to the disk, and making sure the permissions are 655 and that it is executable.
Unfortunately, I don't have a live CD, newer than v7.  Since getting that one, all upgrades and updates have been handled by the package manager.

One possibility, could I have gotten a corrupted file?  That day, it took 12 hours to download the upgrade, when it should have only taken one or two.  Honestly, it was hardly better than dial-up, and AT&T seems to have no intention of fixing the messed-up internet in this hick town.

---

### Post by kansasnoob on 2011-06-05
Using the Live CD please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by anachronon on 2011-06-05
> **kansasnoob said:**
> Using the Live CD please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Here is what hppened:  I downloaded and extracted Boot Info Script onto a thumb drive.  I then booted the computer with the live CD, and mounted both the thumb drive and the Linux partition.  I then ran boot_info_script.sh, and got thise error message:

```
"gawk" not found
please install missing program(s), and run boot_info_script.sh again
```

No results file was produced.

---

