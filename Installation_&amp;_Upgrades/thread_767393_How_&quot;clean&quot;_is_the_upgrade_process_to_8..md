---
title: "How &quot;clean&quot; is the upgrade process to 8.04?"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by RedPeasant on 2008-04-25
Short story:
I have a 6.10 installation that is brand new (if you want the reason, see below). I want to upgrade it to 8.04. Is there going to be a lot of extra junk from 6.10 that isn't used any more but is left on the system for compatibility, or does the process of doing a new install of 6.10 then an upgrade to 8.04  have the same net result as a straight 8.04 install? Would I be better served by using the wubi installer to overwrite this old install with 8.04/would that even work. (I only marginally have a CD drive, see below for details)

Long Story:
I had an XP/7.10 dual boot and wanted to do a fresh install of 8.04 over the older version because I'd managed to get a couple minor things messed up in the old install that I couldn't fix. I torrented the CD and booted it. I got as far as formatting over my old partition and started the install, when the CD drive started giving read errors and the installation failed. Note that this was after the format, so I lost GRUB. I tried everything on both Linux and Windows recovery disks to get something working, but couldn't even get Windows to find itself to boot. I eventually tried the 6.10 disk I had sitting around because it has installed correctly before. It installed just fine.

I'm just wondering which way will work better to get 8.04: Booting into my windows partition and using wubi, or just using the update manager. Or, is there another way of doing it that will just overwrite the current partition with 8.04 that doesn't involve a CD or booting from a USB key (I can't do that on my laptop). Sorry if it's kind of a weird question, but I'm not sure what I should do.

---

### Post by Saint Angeles on 2008-04-25
when you do an upgrade, it should autoremove old packages for ya...


afterwards... you could always run ```
sudo apt-get autoremove
``` and ```
sudo apt-get autoclean
```

---

### Post by RedPeasant on 2008-04-25
Ok, thanks. I just didn't want to get stuck with a bunch of useless packages. I don't have a whole lot of space partitioned for Ubuntu.

---

