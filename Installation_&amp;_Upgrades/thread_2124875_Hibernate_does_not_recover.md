---
title: "Hibernate: does not recover"
date: 2013-03-12
forum: Installation &amp; Upgrades
---

### Post by alfirdaous on 2013-03-12
Hello everybody,

After upgrading from Ubutnu 12.10 to 13.04, when I suspend my computer (put in hibernate) the screen goes black, when I would like to recover (open the screen), the screen stays black.

How can  solve this problem out.

Thx for your help

---

### Post by dino99 on 2013-03-12
how large is your swap partition ?
it needs to be twice the installed ram and at least 4 Gb.

---

### Post by carl4926 on 2013-03-12
And what graphics device?

---

### Post by alfirdaous on 2013-03-12
It does work before, until I upgraded to 13.04

RAM is 3GB
Nvidia

```

~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       29G   14G   16G  47% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           602M  864K  602M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G  224K  1.5G   1% /run/shm
none            100M   16K  100M   1% /run/user
/dev/sda2        32G   17G   15G  55% /host

```

```

~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu Raring Ringtail (development branch)"
NAME="Ubuntu"
VERSION="13.04, Raring Ringtail"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu Raring Ringtail (development branch)"
VERSION_ID="13.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

```

```

~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Raring Ringtail (development branch)
Release:    13.04
Codename:    raring

```

---

### Post by alfirdaous on 2013-03-12
do you have any idea about the problem listed above?

Thx

---

### Post by carl4926 on 2013-03-13
This thread really ought to be moved to +1

---

### Post by alfirdaous on 2013-03-13
Thx carl4926, BUT this won't help me

---

### Post by ceholmes2@gmail.com on 2013-03-22
[QUOTE=alfirdaous;12553950]It does work before, until I upgraded to 13.04

^^^^same issue here.  I just tried remove/reinstall xscreensaver and the laptop hasn't gone into sleep mode again yet.  All worked fine before the 13.04 rolling upgrade install.  Also, cinnamon has crashed and won't run.  It did for a couple of weeks, and Cairo always runs w/ Unity, even in its separate DE login selection.  Not a production machine here....but none the less, I'm seeing similar issues.

---

