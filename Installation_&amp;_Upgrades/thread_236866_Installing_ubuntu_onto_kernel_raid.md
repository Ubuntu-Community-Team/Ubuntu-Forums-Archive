---
title: "Installing ubuntu onto kernel raid?"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by wr0x2 on 2006-08-15
How would I go about installing dapper onto a kernel raid? I have two disks in my system that I want to have in an array, but I don't want to use dmraid to manage them in fake biosraid. I know that doing a kernel raid is possible with gentoo, and I'm sure it is with ubuntu as well, but I have only seen one or two posts on the entire forum that even mention it.

This would be my setup:

/dev/md1: /boot, 100mb, raid1 (/dev/sda1, /dev/sdb1)
/dev/md2 swap, 2G, raid0 ("2,"2)
/dev/md3 /, ~600GB, raid0("3,"3)

I already have the necessary partitions in place.

---

### Post by wr0x2 on 2006-08-15
Come on guys, someone has to know the answer to this...

---

### Post by wr0x2 on 2006-08-16
OK, here's what happens when I try to use mdadm to create an array:

```

root@ubuntu:/home/ubuntu# mdadm --create --verbose /dev/md1 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1
mdadm: Cannot open /dev/sda1: Device or resource busy
mdadm: Cannot open /dev/sdb1: Device or resource busy
mdadm: create aborted

```

This is on the 6.06 installer cd. /dev/md1 is my boot partition and it is in raid1.

---

### Post by wr0x2 on 2006-08-17
*bump* I don't understand why no one can help with this. The necessary tools are included, and installing onto kernel raid is fairly common.

---

### Post by benshort on 2006-08-21
[http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

---

### Post by xaminmo on 2007-01-26
I ran into the same issue and it ended up being that multipathd decided that my two disks were actually different paths to the same disk.

If I killed multipathd, I would get stack dumps to stdout.

I had to uninstall multipath-tools then reboot.  Everything worked after that.

---

