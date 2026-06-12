---
title: "Upgrade from 16.04/10 causes Packages to remain unconfigured"
date: 2016-10-15
forum: Installation &amp; Upgrades
---

### Post by os2 on 2016-10-15
I'm trying to upgrade from 16.04.1 (LTS) to 16.10.

I have changed all xenial keywords to yakkety in /etc/apt/sources.list. Then i did apt-get update && apt-get upgrade.

Most packages have installed correctly. But the following key packages remain unconfigured. Apt just hangs.

```

 friendly-recovery
 linux-image-4.8.0-22-generic
 linux-image-extra-4.8.0-22-generic
 linux-image-4.8.0-22-lowlatency
 linux-signed-image-generic
 linux-signed-image-4.8.0-22-generic
 linux-signed-generic
 initramfs-tools

```


Does anyone have a clue what is happening?

---

### Post by Gridwalker on 2016-10-15
I recently had an issue where many of those packages failed to upgrade because my boot partition was full.

Have you tried removing your older linux images to free up some space? Simply running *apt-get autoremove* could do the trick ...

---

### Post by os2 on 2016-10-15
There's plenty of free space on /boot.

If I (auto)remove some of the packages like friendly-recovery say, apt just hangs at this point.

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  friendly-recovery
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
17 not fully installed or removed.
After this operation, 47.1 kB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 324002 files and directories currently installed.)
Removing friendly-recovery (0.2.33) ...

```

---

### Post by os2 on 2016-10-15
I had to chroot from a Live CD and dpkg --configure -a.

It's a mystery why it didn't work first time around. I suspect that libc6 needed updating first and when that didn't happen and as some other packages were upgraded and restarted some of the scripts and utilities crashed or went into an endless loop.

:/

---

### Post by ian-weisser on 2016-10-15
> **os2 said:**
> I'm trying to upgrade from 16.04.1 (LTS) to 16.10.

I have changed all xenial keywords to yakkety in /etc/apt/sources.list. Then i did apt-get update && apt-get upgrade.

That seems like a rather unwise way of upgrading to the next release of Ubuntu.
Is there a reason you don't simply use the intended tool (do-release-upgrade)?

---

### Post by os2 on 2016-10-16
There is the wise (or unwise for that matter) way of doing it. And then there is the natural way of doing it.

;)

---

### Post by ian-weisser on 2016-10-16
That not-quite-Debian natural way missed deleting 139 obsolete packages...and missed installing their replacements.

---

### Post by os2 on 2016-10-16
Ah ha, you are mistaken Sir. Obsolete packages were id'd and removed. But not quite in the desired order.

Running:

```

sudo aptitude search ?obsolete

```

only lists the remaining packages that I have created and installed myself. Ones which are full of viruses, contagions, trojan-horses and whatnot. Mind.

:D

---

### Post by ian-weisser on 2016-10-16
I bow to you, sir

---

