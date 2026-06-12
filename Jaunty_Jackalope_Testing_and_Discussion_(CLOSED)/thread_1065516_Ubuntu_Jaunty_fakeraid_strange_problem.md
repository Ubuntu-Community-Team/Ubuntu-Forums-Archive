---
title: "Ubuntu Jaunty fakeraid strange problem"
date: 2009-02-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by psychok9 on 2009-02-10
I've Intel ICH10 (fake)raid 0 (stripe) array.
With Ubuntu 8.10 i've used alternate cd, but with Jaunty Alpha 4 I can't use Alternate CD because the dmraid packaged is break (don't found raid array).
With Ubuntu Jaunty Live CD, and previous dmraid... I've installed Jaunty and with the help of [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) the Grub /boot.
I've this situation:
[[IMG]http://img27.imageshack.us/img27/5214/bootwq2.th.jpg[/IMG]](http://img27.imageshack.us/my.php?image=bootwq2.jpg)

The problem is that during the boot process, i got this message:
[[IMG]http://img27.imageshack.us/img27/1586/1002090528ht4.th.jpg[/IMG]](http://img27.imageshack.us/my.php?image=1002090528ht4.jpg)
/dev/sdb1 is one of the two raid array hdd... why it want check? :confused:

```
$ sudo dmraid -r
ERROR: sil: only 1/4 metadata areas found on /dev/sdc, picking...
/dev/sdc: "sil" and "isw" formats discovered (using isw)!
ERROR: sil: only 1/4 metadata areas found on /dev/sdb, picking...
/dev/sdb: "sil" and "isw" formats discovered (using isw)!
/dev/sdc: isw, "isw_dheijhcahi", GROUP, ok, 312581806 sectors, data@ 0
/dev/sdb: isw, "isw_dheijhcahi", GROUP, ok, 312581806 sectors, data@ 0
```

Very strange for me...

---

### Post by psychok9 on 2009-02-10
Solved without know HOW.
I've tried a lot of re-install, and I get a lot of busybox/grub error...
Last time with Ubiquity + a try of grub install - reboot - 2nd try to install grub and dmraid rc14 have solved the problem (thanks to fakeraidhowto and mount --bind /dev/, chroot /target etc.etc.).

---

