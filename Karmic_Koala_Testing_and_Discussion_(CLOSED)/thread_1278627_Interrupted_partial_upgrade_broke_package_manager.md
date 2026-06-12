---
title: "Interrupted partial upgrade broke package manager"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Rippy on 2009-09-29
I have the latest version of Karmic, up to about two days ago when I last updated. Today there was a set of upgrades as usual so I accepted the partial upgrade, but while it was running I forgot about it and had to perform a hard reset.

I fear this must have happened during the installation phase, because the login screen is now different and no package managers work (they just don't come up at all). If I try to run an aptitude update or any command involving aptitude or apt-get, I get the error:

aptitude: error while loading shared libraries: /usr/lib/libapt-pkg-libc6.10-6.so.4.8: file too short

So I don't know what to do. I can't finish upgrading because the package managers have died on me. Is there any way to repair this? I won't have access to a cd burner for a little while so I can't just immediately re-install.

Thanks!

-Rippy

---

### Post by paul_in_london on 2009-09-29
Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=562324](http://ubuntuforums.org/showthread.php?t=562324)

Since I have apt-file installed, I did this to find out what package the file was in:

```
sudo apt-file update
apt-file search libapt-pkg-libc6
apt: /usr/lib/libapt-pkg-libc6.10-6.so.4.8
apt: /usr/lib/libapt-pkg-libc6.10-6.so.4.8.1
```

So it's in apt. Of course you may not have apt-file installed, but you could also do:

```
dpkg -S libapt-pkg-libc6
apt: /usr/lib/libapt-pkg-libc6.10-6.so.4.8.1
apt: /usr/lib/libapt-pkg-libc6.10-6.so.4.8
```

On my system, I see this in /usr/lib/:

```
ls -lart libapt*
-rw-r--r-- 1 root root 780984 2009-09-28 10:30 libapt-pkg-libc6.10-6.so.4.8.1
-rw-r--r-- 1 root root  71548 2009-09-28 10:31 libapt-inst-libc6.10-6.so.1.1.0
lrwxrwxrwx 1 root root     31 2009-09-28 21:59 libapt-inst-libc6.10-6.so.1.1 -> libapt-inst-libc6.10-6.so.1.1.0
lrwxrwxrwx 1 root root     30 2009-09-28 22:00 libapt-pkg-libc6.10-6.so.4.8 -> libapt-pkg-libc6.10-6.so.4.8.1
```

So you may be able to copy what you need from a live CD and/or sort out the sym links.

HTH

---

### Post by NormanFLinux on 2009-09-29
Never reboot before an upgrade is complete! You hose the OS if you do that and have to reinstall.

---

### Post by ranch hand on 2009-09-30
You could also try "sudo dpkg --configure -a"

This should install anything that dpkg has in its grubby little hands.

Does apt-get work?

---

