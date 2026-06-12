---
title: "Disk space issue"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by spacerocket on 2014-04-22
Hello!

My system is running out of disk space and I did

> user@user-MS-7817:~$ du .

Then I noticed  [COLOR=#0000ff]59666340	./.cache/upstart[/COLOR]   ....              and this one looks terribly big.

Is there any way I could resize that? If so how?

Thanks

---

### Post by wieman01 on 2014-04-22
You could resize your harddisk using the Ubuntu installation image. Boot from USB or CD and fire up Partition Editor to tinker with the various partitions. I am not sure what this cache partition of yours is though.

---

### Post by Elfy on 2014-04-22
> **spacerocket said:**
> Hello!

My system is running out of disk space and I did



Then I noticed  [COLOR=#0000ff]59666340	./.cache/upstart[/COLOR]   ....              and this one looks terribly big.

Is there any way I could resize that? If so how?

Thanks

I'd check what you have in there that's causing the size - but I've deleted one and it gets rebuilt on reboot.

> **wieman01 said:**
> ... I am not sure what this cache partition of yours is though.
Mine is holding a set of logs and crash log backups.

---

### Post by wieman01 on 2014-04-22
> **Elfy said:**
> Mine is holding a set of logs and crash log backups.
Yes, so is mine. But who knows...

---

### Post by Elfy on 2014-04-22
> **wieman01 said:**
> Yes, so is mine. But who knows...

I don't - hence the > I'd check what you have in there that's causing the size :)

---

### Post by wieman01 on 2014-04-22
> **Elfy said:**
> I don't - hence the  :)
I got it, Mr Elfy. :-)

---

### Post by spacerocket on 2014-04-23
[COLOR=#0000cd]"You could resize your harddisk using the Ubuntu installation image. Boot  from USB or CD and fire up Partition Editor to tinker with the various  partitions."[/COLOR]

Ok so I boot from original Ubuntu CD and find Partition Editor. That is some program? I thought it was gparted.

[COLOR=#0000cd]"I'd check what you have in there that's causing the size"[/COLOR]

How can I check it?

Thanks

---

### Post by Elfy on 2014-04-23
> **spacerocket said:**
> [COLOR=#0000cd]"You could resize your harddisk using the Ubuntu installation image. Boot  from USB or CD and fire up Partition Editor to tinker with the various  partitions."[/COLOR]

Ok so I boot from original Ubuntu CD and find Partition Editor. That is some program? I thought it was gparted.

[COLOR=#0000cd]"I'd check what you have in there that's causing the size"[/COLOR]

How can I check it?

Thanks

It is gparted.

```
du ~/.cache/upstart/ -a -BK
```will tell you what files you have in there and their apparent sizes in Kb

I'd be looking for one's that are bigger than a few kilobytes.

Alternatively - just open it in nautilus.

---

### Post by spacerocket on 2014-04-23
user@user-MS-7817:~$ du ~/.cache/upstart/ -a -BK```

0K    /home/user/.cache/upstart/hud.log.3.gz
4K    /home/user/.cache/upstart/im-config.log.6.gz
4K    /home/user/.cache/upstart/im-config.log.1.gz
4K    /home/user/.cache/upstart/window-stack-bridge.log.7.gz
4K    /home/user/.cache/upstart/hud.log
4K    /home/user/.cache/upstart/unity7.log.1.gz
4K    /home/user/.cache/upstart/unity7.log
0K    /home/user/.cache/upstart/window-stack-bridge.log.3.gz
4K    /home/user/.cache/upstart/at-spi2-registryd.log.4.gz
4K    /home/user/.cache/upstart/upstart-file-bridge.log.4.gz
4K    /home/user/.cache/upstart/gnome-session.log.5.gz
4K    /home/user/.cache/upstart/gnome-settings-daemon.log.6.gz
4K    /home/user/.cache/upstart/im-config.log.2.gz
24K    /home/user/.cache/upstart/dbus.log
4K    /home/user/.cache/upstart/gnome-session.log.2.gz
0K    /home/user/.cache/upstart/im-config.log.3.gz
4K    /home/user/.cache/upstart/upstart-file-bridge.log.6.gz
4K    /home/user/.cache/upstart/hud.log.1.gz
4K    /home/user/.cache/upstart/at-spi2-registryd.log.2.gz
4K    /home/user/.cache/upstart/hud.log.5.gz
8K    /home/user/.cache/upstart/dbus.log.3.gz
0K    /home/user/.cache/upstart/update-notifier-release.log.3.gz
4K    /home/user/.cache/upstart/update-notifier-release.log
8K    /home/user/.cache/upstart/gnome-session.log.4.gz
4K    /home/user/.cache/upstart/window-stack-bridge.log.5.gz
4K    /home/user/.cache/upstart/at-spi2-registryd.log.7.gz
4K    /home/user/.cache/upstart/unity7.log.7.gz
4K    /home/user/.cache/upstart/im-config.log.5.gz
8K    /home/user/.cache/upstart/unity-panel-service.log
4K    /home/user/.cache/upstart/gnome-session.log.1.gz
4K    /home/user/.cache/upstart/unity7.log.6.gz
0K    /home/user/.cache/upstart/gnome-settings-daemon.log.3.gz
4K    /home/user/.cache/upstart/unity-panel-service.log.5.gz
4K    /home/user/.cache/upstart/unity-panel-service.log.2.gz
4K    /home/user/.cache/upstart/hud.log.2.gz
4K    /home/user/.cache/upstart/dbus.log.1.gz
0K    /home/user/.cache/upstart/unity7.log.3.gz
4K    /home/user/.cache/upstart/window-stack-bridge.log.1.gz
8K    /home/user/.cache/upstart/unity-panel-service.log.4.gz
4K    /home/user/.cache/upstart/upstart-file-bridge.log.7.gz
4K    /home/user/.cache/upstart/im-config.log.7.gz
4K    /home/user/.cache/upstart/unity-panel-service.log.1.gz
4K    /home/user/.cache/upstart/gnome-settings-daemon.log.1.gz
4K    /home/user/.cache/upstart/dbus.log.5.gz
4K    /home/user/.cache/upstart/update-notifier-release.log.7.gz
4K    /home/user/.cache/upstart/hud.log.4.gz
4K    /home/user/.cache/upstart/update-notifier-release.log.4.gz
4K    /home/user/.cache/upstart/gnome-settings-daemon.log.4.gz
4K    /home/user/.cache/upstart/at-spi2-registryd.log.5.gz
4K    /home/user/.cache/upstart/upstart-file-bridge.log
4K    /home/user/.cache/upstart/update-notifier-release.log.1.gz
8K    /home/user/.cache/upstart/dbus.log.4.gz
4K    /home/user/.cache/upstart/at-spi2-registryd.log
8K    /home/user/.cache/upstart/gnome-session.log.6.gz
4K    /home/user/.cache/upstart/window-stack-bridge.log
4K    /home/user/.cache/upstart/unity-panel-service.log.7.gz
0K    /home/user/.cache/upstart/logrotate.log
4K    /home/user/.cache/upstart/unity-panel-service.log.6.gz
4K    /home/user/.cache/upstart/dbus-session
4K    /home/user/.cache/upstart/im-config.log.4.gz
0K    /home/user/.cache/upstart/upstart-file-bridge.log.3.gz
4K    /home/user/.cache/upstart/im-config.log
4K    /home/user/.cache/upstart/window-stack-bridge.log.6.gz
4K    /home/user/.cache/upstart/update-notifier-release.log.5.gz
4K    /home/user/.cache/upstart/upstart-file-bridge.log.2.gz
8K    /home/user/.cache/upstart/dbus.log.7.gz
4K    /home/user/.cache/upstart/hud.log.6.gz
8K    /home/user/.cache/upstart/gnome-session.log
720K    /home/user/.cache/upstart/gnome-session.log.3.gz
4K    /home/user/.cache/upstart/upstart-file-bridge.log.1.gz
4K    /home/user/.cache/upstart/dbus.log.6.gz
4K    /home/user/.cache/upstart/gnome-settings-daemon.log.2.gz
4K    /home/user/.cache/upstart/gnome-settings-daemon.log
4K    /home/user/.cache/upstart/hud.log.7.gz
4K    /home/user/.cache/upstart/gnome-settings-daemon.log.5.gz
4K    /home/user/.cache/upstart/at-spi2-registryd.log.3.gz
4K    /home/user/.cache/upstart/at-spi2-registryd.log.1.gz
4K    /home/user/.cache/upstart/unity7.log.5.gz
4K    /home/user/.cache/upstart/gnome-settings-daemon.log.7.gz
4K    /home/user/.cache/upstart/at-spi2-registryd.log.6.gz
4K    /home/user/.cache/upstart/window-stack-bridge.log.2.gz
4K    /home/user/.cache/upstart/update-notifier-release.log.2.gz
4K    /home/user/.cache/upstart/unity7.log.2.gz
0K    /home/user/.cache/upstart/unity-panel-service.log.3.gz
4K    /home/user/.cache/upstart/update-notifier-release.log.6.gz
4K    /home/user/.cache/upstart/dbus.log.2.gz
4K    /home/user/.cache/upstart/upstart-file-bridge.log.5.gz
8K    /home/user/.cache/upstart/gnome-session.log.7.gz
4K    /home/user/.cache/upstart/unity7.log.4.gz
4K    /home/user/.cache/upstart/window-stack-bridge.log.4.gz
1100K    /home/user/.cache/upstart/
```

---

### Post by Elfy on 2014-04-23
Doesn't look like it's very big to me.

What do you get from 
```

df -h
```

and 
```
sudo du -h --max-depth=1 /
```

---

### Post by spacerocket on 2014-04-23
df -h
```
user@user-MS-7817:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda4        65G  4,7G   57G   8% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            3,9G  4,0K  3,9G   1% /dev
tmpfs           785M  1,1M  784M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            3,9G   80K  3,9G   1% /run/shm
none            100M   24K  100M   1% /run/user
/dev/sda1        96M   22M   75M  22% /boot/efi
```

```
user@user-MS-7817:~$ sudo du -h --max-depth=1 /
[sudo] password for user: 
8,0K    /media
4,0K    /lib64
2,9G    /usr
4,0K    /mnt
609M    /lib
0    /sys
4,0K    /cdrom
4,0K    /opt
24K    /root
127M    /boot
du: cannot access &#8216;/proc/2165/task/2165/fd/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/2165/task/2165/fdinfo/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/2165/fd/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/2165/fdinfo/4&#8217;: No such file or directory
0    /proc
du: cannot access &#8216;/run/user/1000/gvfs&#8217;: Permission denied
1,2M    /run
13M    /etc
4,0K    /srv
9,7M    /bin
934M    /var
95M    /home
4,0K    /dev
16K    /lost+found
11M    /sbin
24K    /tmp
4,6G    /
```

---

### Post by Elfy on 2014-04-23
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Hi - so from the frist block you can see the results for the df -h command, they are telling me that you have no problem with disk space at all.

What makes you think that you're running out? 

>  My system is running out of disk space and I did

---

