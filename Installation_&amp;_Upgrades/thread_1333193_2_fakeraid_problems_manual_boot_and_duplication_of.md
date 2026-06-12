---
title: "2 fakeraid problems: manual boot and duplication of icons"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by sucotronic on 2009-11-21
After following the steps in the [fakeraid howto ubuntu guide]("https://help.ubuntu.com/community/FakeRaidHowto#Live%20CD%20Installation%20%28Ubiquity%20graphical%20installer%29"), I have two problems with my ubuntu installation:

**First problem**:
- At startup process I've to manually enter the command "dmraid -ay" and the "return" in the shell in order to boot the system. You can see the problem exactly in the following video:

>>  [fakeraid problem in Ubuntu Karmic 9.10 - dailymotion]("http://www.dailymotion.com/video/xb7zp0_fakeraid-problem-in-ubuntu-910-karm_tech")

¿Is there any way to automate this and avoid having to input manually every time the computer starts?

**Second problem**:
- Once the system is started and I login into my account, in the Places menu I can see several times my drives and partitions:

[[IMG]http://img509.imageshack.us/img509/4521/fakeraid.th.png[/IMG]](http://img509.imageshack.us/i/fakeraid.png/)

¿Can I hide the duplicates?

---

### Post by sucotronic on 2009-11-21
I've been able to solve the problem **2** (duplicate devices) thanks to an article in [www.geek-blog.de]("http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&u=http%3A%2F%2Fwww.geek-blog.de%2Fstorende-partitionen-in-gnomenautilus-ausblenden.html&sl=de&tl=en"):

Add as many lines as the following to avoid nautilus show them in the menu:
```
/dev/sdb1 /mnt/ignore auto defaults,noauto 0 0
/dev/sdb2 /mnt/ignore auto defaults,noauto 0 0
/dev/sdb3 /mnt/ignore auto defaults,noauto 0 0
/dev/sdb4 /mnt/ignore auto defaults,noauto 0 0
/dev/sdb5 /mnt/ignore auto defaults,noauto 0 0
/dev/sdb6 /mnt/ignore auto defaults,noauto 0 0
/dev/sda1 /mnt/ignore auto defaults,noauto 0 0
/dev/sda2 /mnt/ignore auto defaults,noauto 0 0
/dev/sda3 /mnt/ignore auto defaults,noauto 0 0
/dev/sda4 /mnt/ignore auto defaults,noauto 0 0
/dev/sda5 /mnt/ignore auto defaults,noauto 0 0
/dev/sda6 /mnt/ignore auto defaults,noauto 0 0
```

Now the menu is more clear:
[[IMG]http://img153.imageshack.us/img153/3510/screenshot001w.th.png[/IMG]](http://img153.imageshack.us/i/screenshot001w.png/)

For the problem **1**, I've found some info here:
[http://www.dalouche.com/wordpress/2006/01/15/running-ubuntu-gnulinux-on-a-fakeraid1-mirroring-array/](http://www.dalouche.com/wordpress/2006/01/15/running-ubuntu-gnulinux-on-a-fakeraid1-mirroring-array/)

The solution is:
```
sudo vi /etc/initramfs-tools/scripts/local-top/dmraid
```

There copy the following text:
```
#!/bin/sh
sleep 10
/sbin/dmraid -ay
```

Now exit vi and make the file executable:
```
sudo chmod a+x /etc/initramfs-tools/scripts/local-top/dmraid
```

Update initrd to include the changes done:
```
sudo update-initramfs -u
```

---

