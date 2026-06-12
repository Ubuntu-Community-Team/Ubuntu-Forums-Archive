---
title: "[SOLVED] Dual boot confusion - win xp"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by SpikeMolotov on 2008-05-18
Hey all,

So I'm completely clueless about Linux and I have a machine with 2 physical drives. I use one of those for media and file storage, the other is my windows drive which is already partitioned into 2 logical drives.

What I'm trying to do is install Ubuntu onto the 2nd partition on my OS drive as a dual boot with WinXP, and that is fine, but I was hoping to try and make the media disk available to both OSes (if possible).

I know I have to set the  mount point of the windows partition as /windows, but I'm not sure what to do with the media drive. Do I leave it without a mount point?

Any info or advice would be awesome - cheers guys

---

### Post by Partyboi2 on 2008-05-18
Ubuntu can read/write to ntfs so you shouldn't have to do anything to your media hard drive. Ubuntu should auto mount it.
If you are choosing to manually do the partitions make sure you create a /(root), (mount point /) and a swap partition. If you want you can also create a /home partition so that if you need to reinstall for any reason in the future you can do so without loosing your personal data or settings. In other words what ever you put on the /home partition will not be touched if you have to reinstall.

To dual boot there are plenty of howto's around here is a few
[http://digitalgraphy.wordpress.com/2007/10/20/dual-booting-ubuntu-and-windows-ntxpvista/](http://digitalgraphy.wordpress.com/2007/10/20/dual-booting-ubuntu-and-windows-ntxpvista/)
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by SpikeMolotov on 2008-05-18
Thanks for ur help. I'll give it a shot :)

---

### Post by cdtech on 2008-05-18
I've set mine up in the "/etc/fstab" to auto mount at boot.

You need to create a directory to mount to, I made mine "/mnt/share".
```
/dev/hdb1 /mnt/share ntfs-3g defaults,locale=en_US.utf8 0 0
```

The hdb1 is my spare drive that I can share with both windows and ubuntu.

Hope this helps.

---

