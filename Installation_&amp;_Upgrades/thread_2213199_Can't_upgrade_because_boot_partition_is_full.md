---
title: "Can't upgrade because /boot partition is full"
date: 2014-03-25
forum: Installation &amp; Upgrades
---

### Post by moondoggy2 on 2014-03-25
I've been trying for the last few days, to update my copy of Trusty.  It won't work, because I'm told my /Boot partition is full.  
I am unable to manually delete the old images.  I can't move them to a different location.  [ATTACH=CONFIG]251454[/ATTACH]
I've cruised the net looking for solution after solution, and nothing has worked.  I've tried purging them, to no avail.  I've tried 'sudo apt-get autoremove' and nothing worked.  I tried 'sudo apt-get --purge autoremove' and nothing worked.  
Any help would be greatly appreciated, fellas.

---

### Post by oldfred on 2014-03-25
I generally do not suggest separate /boot partitions just for the issues you are having. 

If you can boot or chroot into your system. I ran these commands from my working system, if you only have command line then you cannot use nautilus to delete kernels. Obviously change fred to your username.

 ```
1253  dpkg -S /usr/src/*
 1254  uname --kernel-release
 1255  sudo apt-get update
 1256  sudo apt-get upgrade
 1257  sudo apt-get -s autoclean
 1258  sudo apt-get autoclean
 1259  sudo apt-get -s autoremove
 1260  sudo apt-get  autoremove
 1261  df -h
 1263  gksudo nautilus
 1268  sudo chown -R fred /root/.local/share/Trash/
 1274  sudo rm -rf /root/.local/share/Trash/
 1275  df -h
 1276  history
```

I gernally prefer to use synaptic. But if you upgraded, you may have old kernels from previous installs that are now not in dpkg to remove and have to manually remove them.
 Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.5.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.5.0-{17,18,19,21,22,23,24}-generic

If the only way you can get into system is with chroot from a live installer, these are examples of chroot to do other tasks as well. You do not need sudo once chrooted.
 drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Also
 [http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this](http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this)
dpkg -S /usr/src/*
uname --kernel-release

---

### Post by fantab on 2014-03-25
If you can still boot your system then you can also remove the old kernels with this:
```
sudo dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
sudo apt-get update && sudo apt-get dist-upgrade
```

Tell us if it helps... if it doesn' t then you will have to follow oldfred's advice.

---

