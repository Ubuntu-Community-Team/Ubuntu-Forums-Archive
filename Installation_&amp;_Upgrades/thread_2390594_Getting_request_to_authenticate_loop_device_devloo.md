---
title: "Getting request to authenticate loop device /dev/loop`12"
date: 2018-04-30
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2018-04-30
One of my PC's that is just upgraded to 18.04 LTS is now asking to authenticate loop device /dev/loop 12 when I open a file I have downloaded.

Everything works once I authenticate, but what is going on.

Thank you,

John

---

### Post by Claus7 on 2018-04-30
Hello,

what is the output of the command:
```
df -kh
``` ?

I suppose that you have snap packages installed in your system.

In any case I would try to change the permissions of the /dev/loop* and see what I will get.

Regards!

---

### Post by cigtoxdoc on 2018-05-02
john@john-MS-7846:~$ df -kh
Filesystem      Size  Used Avail Use% Mounted on
udev            3.8G     0  3.8G   0% /dev
tmpfs           784M  1.7M  783M   1% /run
/dev/sda5        72G   67G  1.9G  98% /
tmpfs           3.9G   30M  3.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0       87M   87M     0 100% /snap/core/4486
/dev/loop4       13M   13M     0 100% /snap/gnome-characters/69
/dev/loop1      1.7M  1.7M     0 100% /snap/gnome-calculator/154
/dev/loop2       87M   87M     0 100% /snap/core/4407
/dev/loop3       21M   21M     0 100% /snap/gnome-logs/25
/dev/loop6       22M   22M     0 100% /snap/gnome-logs/31
/dev/loop8      141M  141M     0 100% /snap/gnome-3-26-1604/59
/dev/loop7      3.8M  3.8M     0 100% /snap/gnome-system-monitor/39
/dev/loop5       13M   13M     0 100% /snap/gnome-characters/86
/dev/loop9      2.4M  2.4M     0 100% /snap/gnome-calculator/167
/dev/loop10      83M   83M     0 100% /snap/core/4327
/dev/loop11     3.4M  3.4M     0 100% /snap/gnome-system-monitor/36
/dev/sda6        93G   11G   78G  13% /media/MyDocuments
/dev/sda7        53G   69M   50G   1% /media/MyChemistry
/dev/sda1       215G  100G  115G  47% /media/OS
tmpfs           784M  120K  784M   1% /run/user/1000

So, is there really a loop 12?

John

---

### Post by Claus7 on 2018-05-03
Hello,

all these /dev/loops are corresponding to snap packages that you have installed. The fact that they are 100% full is pretty normal. From the output of the command I cannot see any /dev/loop/12, yet I can see duplicate packages including 2 versions of gnome-system-monitor. Similar case can be found here:
[https://ubuntuforums.org/showthread.php?t=2390242](https://ubuntuforums.org/showthread.php?t=2390242)

I do not know if this would help you, but you could try to remove this package, since its harmless using:
sudo snap remove gnome-system-monitor

and see if you get the same error. If this does not work you could update your snap packages using:
snap refresh

and see what you will get.

Regards!

---

