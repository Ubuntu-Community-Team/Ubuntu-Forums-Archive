---
title: "mount disappears"
date: 2005-03-21
forum: Installation &amp; Upgrades
---

### Post by bonifacio on 2005-03-21
Prior the upgrade to Hoary I automounted my ntfs partition and the drive icon appears in my desktop.

Now the same ntfs partition is still mounted but the drive icon disappears from my desktop.

What should I do so that it behaves the same way?

---

### Post by ghostcom97 on 2005-04-05
It's a bug in the HAL / gnome-volume-manager. [See here](http://bugzilla.ubuntu.com/show_bug.cgi?id=7641).
I have the same problem with my NTFS/Fat32 partitions and everyting else (usb/Firewire Hdd's) being automounted in /media/<label> but not shoing up in on the desktop, in 'Places' or 'Computer'...

My temporary fix had been to run this in the terminal ```
sudo /etc/init.d/dbus-1 restart
```

---

