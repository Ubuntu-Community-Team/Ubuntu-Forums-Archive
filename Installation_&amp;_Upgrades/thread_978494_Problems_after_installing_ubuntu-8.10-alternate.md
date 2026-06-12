---
title: "Problems after installing ubuntu-8.10-alternate"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by voppe on 2008-11-11
After installation of 8.10-alternate with ltsp-server-standalone on
a Supermicro P4DP8-G2 with 2 scsi disks I got these problems:

When booting, this message shows up:
Boot from (hd0,0) reiserfs 7e57....
Starting up ...
Loading, please wait
[ 20.340879] scsi target0:0:5 Domain Validation
Disabling Information Units
Gave up waiting for root device. Common problems:
...
ALERT! /dev/disk/by-uid/7e5f... does not exist. Dropping to a shell!
...
(initramfs)

If I press Ctrl-D at this stage the boot continues with no more problems.
I tried to change disks/partitions/fs-types and tryied different configs
(even rootdelay=30) in grub/menu.lst without succes.
NB Before this installation I used both Suse and Gentoo on the same hardware without such problem.

When the system went up first time, both NICs were assigned the same IP:
192.168.0.254 ! The graphical nm-connection-editor doesn't work, it says
'ifupdown-connection.c.82 - connection update not supported (read only)'.
So I edited /etc/network/interfaces and have now these static interfaces:
192.168.1.101 on eth0 (to firewall) and 192.168.0.254 on eth1 (to thin clients). I have still problems with the default route 192.168.1.1, must
be added each time I reboot.

The first connected ltsp-client went up without problems, everything
seems to work OK except I can't log on the shell screen tty1.
Yes, I added a user to the ltsp-tree with sudo chroot /opt/ltsp/i386,
useradd + passwd.

The last problem is that the users-admin widget doesn't work, even if
invoked from xterm with 'sudo users-admin'. A workaround is to assign
a passwd to root and the ssh root@192.168.0.101 :( I was surprised that
i could log in as root with ssh - it should not be possible by default!)

I hope you gurus have hints how fix these problems (bugs??)
Cheers
peter

---

### Post by voppe on 2008-11-11
Booting problem solved now!
Increased the rootdelay option in /boot/grub/menu.lst to rootdelay=140


Automatic default gw solved!
Added following to /etc/network/interfaces in section iface eth0 inet static
  up route add default gw 192.168.1.1
  down route del default gw 192.168.1.1

I should RTFM first!

peter

---

