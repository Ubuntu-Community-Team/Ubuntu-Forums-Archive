---
title: "SE Linux: Disabled at boot"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by jenaniston on 2010-02-05
In trying to troubleshoot . . . 
and with only about 10 more mounts left before the automatic filesystem check crashes this "jerry-rig" USB OS on my laptop
(unless the double fstab modifications work this time) . . .

I ran the command
```
#  dmesg | less
```to find the line
```
  . . . 

[    0.0042041] SELinux:  Disabled at boot

  . . .
```and then,
 with the same Live USB Ubuntu 9.04 that installed the above U9.04 OS USB, being booted on a campus computer,
that **SELinux** is ***also disabled*** at the 4 millisecond mark as well . . .

```
ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# dmesq | less
. . .

[    0.004000] SELinux:  Disabled at boot.
. . .
```On a Live USB Fedora 12 KDE (and I will also check a Fedora 11 Live CD in gnome as well)
that same dmesg command reveals boot conditions that show the **starting of SE Linux**
```
. . .
SELinux:  Initializing.
SELinux:  Starting in permissive mode.
. . .

```Any of the wise experts understand why this difference,
and if it ***may or may not*** be helpful to follow some ideas from this archive thread in the forums

[http://ubuntuforums.org/showthread.php?t=533235](http://ubuntuforums.org/showthread.php?t=533235)

and to try to go ahead and enable/install SELinux for my Ubuntu9.04 running a sick laptop.

Thank you in advance . . . while I try to do more research of my own as well.

---

