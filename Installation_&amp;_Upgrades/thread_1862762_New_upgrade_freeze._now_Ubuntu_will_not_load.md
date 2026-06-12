---
title: "New upgrade freeze. now Ubuntu will not load"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by g_lev on 2011-10-17
Hi,

I've tried upgrading Ubuntu but the OS froze on the point where it asked me if I want to keep old file configuration (I think desktop). no button worked, nothing. so I had to reboot but once rebooted nothing loads. now I have no previous OS and no new one.
I have a lot of stuff in there but my main concern is a virtual box with Ubuntu server on it with tuns of projects.
my questions are:
1. can Ubuntu be saved? and if not;
2. can I rescue my virtual box images, back them up and then reinstall everything.

thank you for your help.

---

### Post by flangemonkey on 2011-10-17
lesson for the future... keep your important stuff on a new partition and ideally backed up (there's loads of guides out there for partitioning)

but, back to your current problem; on boot up grub will load and you might see a choice of kernels, or a line that says press Escape to see the boot menu, if the latter, press escape and you'll get a list of kernels.

Select the second line down (recovery mode) and at the prompt when all the text stops moving type these commands in order:
```

apt-get update
apt-get upgrade
do-release-upgrade
```
if this doesn't put you back to a working system, report the output of these commands here 

```

df -Th *(capital T)*
dmesg | tail
ifconfig | grep addr

```

good luck :)

---

### Post by g_lev on 2011-10-18
> **flangemonkey said:**
> lesson for the future... keep your important stuff on a new partition and ideally backed up (there's loads of guides out there for partitioning)

but, back to your current problem; on boot up grub will load and you might see a choice of kernels, or a line that says press Escape to see the boot menu, if the latter, press escape and you'll get a list of kernels.

Select the second line down (recovery mode) and at the prompt when all the text stops moving type these commands in order:
```

apt-get update
apt-get upgrade
do-release-upgrade
```if this doesn't put you back to a working system, report the output of these commands here 

```

df -Th *(capital T)*
dmesg | tail
ifconfig | grep addr

```good luck :)

WOW! worked like charm! I ran  
apt-get update
apt-get upgrade
then I got an error - 
```

E: dpkg was interrupted, 
you must manually run 'dpkg --configure -a' to correct the problem 

```so I ran dpkg --configure -a and it fixed itself :)

In the names of the gods of Linux I thank you flangemonkey [-o<

---

### Post by kyrol on 2012-04-29
While I upgraded Ubuntu 10.04 to 12.04 very same issue occured - something stuck with my installation. Here are commands results (chroot was used, I binded /dev /dev/pts /proc /sys using Ubuntu livecd 12.04):

```
root@ubuntu:/# df -Th
df: `/run/lock': No such file or directory
df: `/run/shm': No such file or directory
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sde2      ext4       65G   57G  4.9G  93% /
none           devtmpfs  747M   12K  747M   1% /dev
none           tmpfs      65G   57G  4.9G  93% /run
```

```
[ 1603.969852] EXT4-fs (sdb2): warning: maximal mount count reached, running e2fsck is recommended
[ 1604.004464] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[ 1604.139281] EXT4-fs (sdb3): warning: maximal mount count reached, running e2fsck is recommended
[ 1604.241308] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
[ 1604.357729] EXT4-fs (sdd1): warning: maximal mount count reached, running e2fsck is recommended
[ 1604.516416] EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: (null)
[ 2020.806803] whiptail[16180]: segfault at 1 ip b774c1a8 sp bf8798c0 error 4 in libnewt.so.0.52.11[b7747000+15000]
[ 5132.325634] whiptail[17100]: segfault at 1 ip b77971a8 sp bfebb110 error 4 in libnewt.so.0.52.11[b7792000+15000]
[ 5156.747973] EXT4-fs (sdb2): warning: maximal mount count reached, running e2fsck is recommended
[ 5156.759543] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)

```

```
root@ubuntu:/# ifconfig | grep addr
eth0      Link encap:Ethernet  HWaddr 00:15:f2:6b:96:dd  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          inet addr:188.33.208.164  P-t-P:10.64.64.64  Mask:255.255.255.255

```

Most ironic of all:

```
root@ubuntu:/# do-release-upgrade
Checking for a new Ubuntu release
No new release found

```

---

### Post by shubes on 2012-06-06
I experienced this as well. The system isn't frozen, it's just waiting for input from the terminal display. I inadvertently stumbled upon the <tab> key, which changes the focus to the terminal display inside of the Distribution Upgrade window. Once you press the <tab> key, you can do whatever's appropriate to continue on (<enter> or whatever).

This really should be documented somewhere that's easy to find. Drove me nuts.

---

