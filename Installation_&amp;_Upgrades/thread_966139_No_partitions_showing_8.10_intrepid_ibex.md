---
title: "No partitions showing? 8.10 intrepid ibex"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by gibberz on 2008-11-01
Hi there ! is anyone else having the problem that when trying to install, their is none of your existing partitions  showing in either Manual or Guided options? I`ve got like four partitions and none show up?
I also checked the release notes and i have not mounted or searched the drives in the live cd. I have now tried the desktop 8.10 install cd  and the alternate install cd with no luck. If anyone has had this problem and has found a fix , let me know thanks

---

### Post by gulch on 2008-11-01
well, this is a real problem, 
I. you can install it on usb device;
II. 
a) get vmlinuz&#12289;initrd.gz from desktop;
b) edit menu.lst as the following&#65306;
title Install Ubuntu
root (hd0,0)
kernel (hd0,0)/vmlinuz boot=casper iso-scan/filename=/ubuntu-8.10-desktop-i386.iso ro quiet splash locale=zh_CN.UTF-8
initrd (hd0,0)/initrd.gz;
and put the desktop on other usb divice,
it work

---

### Post by gulch on 2008-11-01
well, this is a real problem, 
I. you can install it on usb device;
II. 
a) get vmlinuz&#12289;initrd.gz from desktop;
b) edit menu.lst as the following&#65306;
title Install Ubuntu
root (hd0,0)
kernel (hd0,0)/vmlinuz boot=casper iso-scan/filename=/ubuntu-8.10-desktop-i386.iso ro quiet splash locale=zh_CN.UTF-8
initrd (hd0,0)/initrd.gz;
and put the desktop on other usb divice,
it work

---

### Post by gibberz on 2008-11-01
> **gulch said:**
> well, this is a real problem, 
I. you can install it on usb device;
II. 
a) get vmlinuz&#12289;initrd.gz from desktop;
b) edit menu.lst as the following&#65306;
title Install Ubuntu
root (hd0,0)
kernel (hd0,0)/vmlinuz boot=casper iso-scan/filename=/ubuntu-8.10-desktop-i386.iso ro quiet splash locale=zh_CN.UTF-8
initrd (hd0,0)/initrd.gz;
and put the desktop on other usb divice,
it work

Thanks for the replay gulch. I`ve found a bug thats been filed in launchpad so i added a comment to let them know that the problem is still their. It seems the bug was reported before the full  release. I`m going to give the usb thing ago . It`s a shame really , this is the first real problem i`ve had when installing Ubuntu over the last couple of years.No ubuntu intrepid for me unless i can find my usb stick :(

Oh here`s the bug report: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/288675](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/288675)

---

### Post by gibberz on 2008-11-01
Ok now i`m lost! I just tried to install hardy so i could upgrade to ibex.
The thing is that Hardy is doing the same thing , only showing one hard drive (sda) with no partitions shown? It must be my set up? Like i say i`m bit lost now i really don`t know how my partitions are not showing in the list especially since it`s in a live environment  . If anyone has any ideas on this please let me know, thanks !

---

### Post by plmday on 2008-11-01
> **gibberz said:**
> Hi there ! is anyone else having the problem that when trying to install, their is none of your existing partitions  showing in either Manual or Guided options? I`ve got like four partitions and none show up?
I also checked the release notes and i have not mounted or searched the drives in the live cd. I have now tried the desktop 8.10 install cd  and the alternate install cd with no luck. If anyone has had this problem and has found a fix , let me know thanks

Hmmm, gibberz, I met the same problem with Xubuntu.  No idea how to solve it.  It's also my first time failing to install *ubuntu.  It seems to me this release rushes out a little bit early ... :-(

---

### Post by gulch on 2008-11-01
> **gibberz said:**
> Ok now i`m lost! I just tried to install hardy so i could upgrade to ibex.
The thing is that Hardy is doing the same thing , only showing one hard drive (sda) with no partitions shown? It must be my set up? Like i say i`m bit lost now i really don`t know how my partitions are not showing in the list especially since it`s in a live environment  . If anyone has any ideas on this please let me know, thanks !

oh,my friend, I have fixed it.

[http://ubuntuforums.org/showthread.php?t=966609](http://ubuntuforums.org/showthread.php?t=966609)
Fix Ubuntu 8.10 Intrepid bug/288675 "no partitions listed in partition table"

That is an easy way to solve the problem:
1. plesae use the Alternative iso;

2. when partition, run shell, you can see /hd-media,
only need run as following:
[COLOR="Red"][SIZE="6"]# umount -l /hd-media
# exit[/SIZE][/COLOR]

3. now you can see partition tab, good luck!!!

---

