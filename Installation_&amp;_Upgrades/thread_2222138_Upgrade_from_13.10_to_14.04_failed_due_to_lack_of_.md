---
title: "Upgrade from 13.10 to 14.04 failed due to lack of space on /boot"
date: 2014-05-05
forum: Installation &amp; Upgrades
---

### Post by mike40033 on 2014-05-05
So, I cleared some unwanted images. Now Ubuntu won't detect a new version, yet it still seems to be the old version.

sudo apt-get update && sudo apt-get dist-upgrade

doesn't update the distro.

lsb_release -a

says 

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy

What can I do?

---

### Post by plucky on 2014-05-05
What does ```
 ls /boot
``` show you?

---

### Post by mike40033 on 2014-05-05
hartleym@chocolate:~$ ls /boot
abi-3.11.0-15-generic         initrd.img-3.11.0-20-generic
abi-3.11.0-17-generic         lost+found
abi-3.11.0-19-generic         memtest86+.bin
abi-3.11.0-20-generic         memtest86+_multiboot.bin
config-3.11.0-15-generic      System.map-3.11.0-15-generic
config-3.11.0-17-generic      System.map-3.11.0-17-generic
config-3.11.0-19-generic      System.map-3.11.0-19-generic
config-3.11.0-20-generic      System.map-3.11.0-20-generic
grub                          vmlinuz-3.11.0-15-generic
grub.bak                      vmlinuz-3.11.0-17-generic
initrd.img-3.11.0-15-generic  vmlinuz-3.11.0-19-generic
initrd.img-3.11.0-17-generic  vmlinuz-3.11.0-20-generic
initrd.img-3.11.0-19-generic


hartleym@chocolate:~$ df -h /boot
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       236M  123M  101M  56% /boot

---

### Post by aysiu on 2014-05-05
Have you tried this? ```
sudo do-release-upgrade -d
```

---

### Post by grahammechanical on 2014-05-05
If the upgrade failed then Ubuntu has not been upgrade to the next release and dist-upgrade only upgrades the packages on the existing release. It does not upgrade to the next released version of Ubuntu. Please see Maintenance Commands 1, 2 and 3

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Regards.

---

### Post by mike40033 on 2014-05-05
That worked!

Alas, I have a worse problem now. 

My screen is showing

Boot from CD :
error: symbol 'grub_term_highlight_color' not found.
Entering rescue mode...
grub rescue>

and I'm totally lost.

---

### Post by aysiu on 2014-05-05
Seems to be a bug but with workarounds:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)

---

### Post by mike40033 on 2014-05-07
dpkg-reconfigure didn't work for me, but there's no clear instructions on how to run it in the bug report. Maybe I'm doing something wrong.

I feel like the guy who wrote [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977/comments/32](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977/comments/32) was talking about me. The only thing stopping me giving up on Ubuntu right now is I don't have 2k lying around for a Mac.

---

