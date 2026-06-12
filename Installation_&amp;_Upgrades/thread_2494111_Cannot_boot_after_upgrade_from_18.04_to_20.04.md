---
title: "Cannot boot after upgrade from 18.04 to 20.04"
date: 2024-01-05
forum: Installation &amp; Upgrades
---

### Post by seandaug on 2024-01-05
I tried to perform a dist upgrade from Ubuntu 18.04 to 20.04 and now my machine will not boot.

The installation process was initiated with ```
sudo do-release-upgrade
```

Unfortunately, it hung and I had to kill dpkg in the middle of the install. To try to recover, I ran the following successfully before rebooting:
```

sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get dist-upgrade --fix-missing
sudo apt-get dist-upgrade --fix broken
sudo apt-get autoremove

```

Now when I boot it says the following:
```

Gave up waiting for root file system device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! UUID=6eab0001-2353-48fa-8abd-904351241659 does not exist. Dropping to a shell!

```

I tried using Boot-Repair from a 20.04 Live CD, but I got the same error message after rebooting. It generated the following pastebin: [https://paste.ubuntu.com/p/Ms5GSnkm7g/](https://paste.ubuntu.com/p/Ms5GSnkm7g/)

The ubuntu install is on nvme0n1p2, which has the UUID 6eab0001-2353-48fa-8abd-904351241659 according to info in the pastebin.

What should I try next?

---

### Post by #&amp;thj^% on 2024-01-05
I hate being the barer of bad news, 
**ALERT! UUID=6eab0001-2353-48fa-8abd-904351241659 does not exist**. Dropping to a shell! means that the disk or partition with that UUID is not visible to your system, and, you tried to boot from it. Either put the disk back online, or edit the "BOOT_IMAGE=... line to point to an actual system.

If it were me I'd just reinstall from your Live 20.04 installer, you will have a clean system installed and less left over cruft.
Be sure to have all you want to keep backed first for safety sake.

---

### Post by seandaug on 2024-01-05
I managed to fix it. The problem was that the default linux image was 5.4.0-1105-gke in grub. Choosing the second option in the Advanced grub menu (5.4.0-169-generic) was able to boot. After booting I used apt to purge the image, header, and module packages related to gke (I didn't seem to need them). I probably could have also rearranged the grub menu list or set a different default.

---

### Post by #&amp;thj^% on 2024-01-05
Nice Work! :)

---

