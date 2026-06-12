---
title: "Reinstalling, what happens to LVM?"
date: 2013-03-18
forum: Installation &amp; Upgrades
---

### Post by yay101 on 2013-03-18
Hey all as the title suggests I am going to reinstall ubuntu very soon and would like to know what is going to happen to my lvm? Will my re-installation see it and allow me to reactivate it? Or will i have to do some witchcraft and wizardry to get it back up without losing data. PS Its a 10tb lvm which is almost full so i would really like this to work.

Thanks!

---

### Post by darkod on 2013-03-18
You didn't specify which OS exactly, desktop or server. The destop live cd doesn't include the lvm2 package so by default it will not see the LVM. But if you boot into live mode first, install the lvm2 package and activate the LVM, then start the installer with the icon on the desktop (without rebooting the live mode), it should find it just fine and allow you to use it as you wish.
```
sudo apt-get install lvm2
sudo vgchange -ay
```

But don't forget that ubuntu doesn't assume what you want to do with partitions (including LVM logical volumes). You need to select each and specify the filesystem and mount point you want to use on it, using the manual install mode. Since you want to keep the data make sure you DO NOT select the format box.

That should be it.

If the OS is not running on the LVM another option is installing the OS first, and after that installing the lvm2 package, activating the LVM and making the correct entries in /etc/fstab.

The server installer should see the existing LVM without any problems since it includes the package.

---

