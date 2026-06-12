---
title: "Need help clean-installing ubuntu 13.04 alongside windows 7"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by isaac12345 on 2013-05-01
Hi all,

A few days ago, I had ubuntu 12.04 installed alongside windows 7 on a dual boot partition across 2 different hard disks. I needed to re-size '/' as it was running out of space. Finding that it would be quite risky to do that as it would have involved moving many partitions around, I decided I would simply wipe everything off that hard disk and simply install Ubuntu on it from scratch. Therefore, I did that with Gparted. Then I ran an Ubuntu 13.04 liveUSB and first selected the "Do something else" option. I couldn't quite figure out what to do there so I went back and selected the "Install alongside Windows 7".
After installation, I re-booted, selected ubuntu from the OS-choice menu and got the GRUB console! Figuring that it was a problem with the first boot menu not directing the "Ubuntu" choice to the right partition, I used EasyBCD in Windows 7 to change it to various partitions but in vain. I am therefore now stuck with only Windows 7 and would appreciate your help in figuring out what exactly the problem is. Below are GParted screenshots of my hard disks after the Ubuntu 13.04 installation, for your consideration -

[ATTACH=CONFIG]242038[/ATTACH][ATTACH=CONFIG]242039[/ATTACH][ATTACH=CONFIG]242040[/ATTACH]

---

### Post by darkod on 2013-05-01
Boot into live mode, and install grub2 on the MBR of sdb. After that reboot and go into bios and set sdb as first boot option.

To install grub2 to sdb in live mode, open terminal and do:
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

See if that helps. The grub2 boot menu should give you option for your win7. Selecting that might give you another menu depending what changes you made with EasyBCD. You will have to undo them to make this second menu go away since it exists into the win7 boot files.
Grub2 is enough to dual boot, forget about easybcd.

---

### Post by isaac12345 on 2013-05-06
It worked!! What an elegant and simple solutions! Thanks! :) How do I mark the thread as solved?

---

### Post by darkod on 2013-05-06
The Solved option should be in Thread Tools above the first post but I think it's broken/missing right now.

---

