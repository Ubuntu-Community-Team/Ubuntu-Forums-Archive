---
title: "accidentally removed libs ,can't log onto Ubuntu 10.04"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by Gimmie5Bukks on 2010-05-09
Hi 
i was trying to remove the flash plugin 32bit wrapper (don't remember the exact name of the package),using the command apt-get -*y* remove --[I]purge and i saw somehow uninstalled a bunch of other programs like the gnome-network manager,emphaty...
Now i rebooted and can't log on anymore .

Is there a way to repair this,like running an upgrade from the livecd to restore the missing parts without wiping out my conf & other programs ? 

I've tried this that i found some other forum ,but i didn't work

[/I]```
sudo mkdir /mnt/repair

sudo mount /dev/sda3 /mnt/repair

sudo chroot /mnt/repair su

sudo apt-get update
sudo apt-get upgrade
sudo aptitude upgrade
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get upgrade
```

I'm running a dual-boot with windows 7

---

### Post by Gimmie5Bukks on 2010-05-10
well i've given up ,so i did a clean install of ubuntu

---

