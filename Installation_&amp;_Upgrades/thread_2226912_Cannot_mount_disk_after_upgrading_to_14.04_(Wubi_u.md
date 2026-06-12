---
title: "Cannot mount disk after upgrading to 14.04 (Wubi ubuntu)"
date: 2014-05-29
forum: Installation &amp; Upgrades
---

### Post by Feroslav on 2014-05-29
Hello. I recently upgraded from 12.04 -> 12.10 -> 13.10 -> 14.04. My ubuntu is installed from Windows with WUBI. When I'm trying to boot ubuntu, I get these errors. I also tried to rewrite "ro" to "rw" but still doesn't work.
Do you have any idea how to fix it? I was wondering abou something like reinstalling wubi to 12.04, backup root.disk and then copy that disk without losing data. But is that possible? Will I loose all the data ?

Thanks

```

mount: mounting ... failed: Invalid argument
mount: mounting /dev on /root/dev failed ...
mount: mounting /sys on /root/sys failed ...
mount: mounting /proc on /root/proc failed: ...
Target filesystem doesn't have requested /sbin/init
No init found. Try passing init= bootarg.

(initramfs)
```

---

### Post by TheFu on 2014-05-29
WUBI support ended with 12.04.  It is pass time to take off the training wheels and switch to a real installation on separate partitions, IMHO.

All your personal settings are in your HOME, so if you back that up, then you'll have everything. 
Other system personalization is stored elsewhere - where depends on many, many, many things that only you know.  Start by backing up /etc/ and creating a list of installed packages (dpkg --get-selections).  With these things and whatever data that is stored outside those already saved areas - you are golden and read for a fresh 14.04 install into separate partitions.  [http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview) provides an overview of migrating systems.

---

### Post by Feroslav on 2014-05-30
I'm not exactly sure, what HOME do you think. I cannot mount into ubuntu, so that I cannot backup my files.

---

### Post by TheFu on 2014-05-30
Google found this: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) Hope it helps you recover.

After following that ...  [http://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/](http://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/) explains which files are where under Linux. HOME means "$HOME or ~/ or where you get if typing 'cd' alone in a terminal window.

At this point, you have nothing to loose - install 12.04 as you propose, then backup everything possible. I have no idea whether data loss will happen or not. Sorry.  If you don't try, the data is gone away.  OTOH, if backups were performed, then you'd be able to restore back to the pre-14.04 install and use that to get all your files/data off before migrating to a normal install (without wubi) and running the current LTS 14.04 release.

Hopefully someone with any wubi experience will see this and help. I've never run wubi.

---

