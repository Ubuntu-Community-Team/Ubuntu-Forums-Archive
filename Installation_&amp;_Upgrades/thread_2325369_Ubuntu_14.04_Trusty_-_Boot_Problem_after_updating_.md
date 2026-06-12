---
title: "Ubuntu 14.04 Trusty - Boot Problem after updating Kernel"
date: 2016-05-21
forum: Installation &amp; Upgrades
---

### Post by dustin18 on 2016-05-21
Bare with me I'm still not very proficient in Linux.  
Ubuntu 14.04 Trusty

I recently updated in the terminal as I always do: 

```

sudo apt-get update
sudo apt-get upgrade
```

It updated linux headers. I was using 3.13.0-85-generic. The update included 3.13.0-86-generic. Then I believe grub updated. I used to dual boot with windows on a separate hard drive but that Windows drive had a fatal error months ago. It's still in the computer though. 

After restarting after this update I get a black screen that says "Command not found" with a bunch of other stuff that goes far too quickly to read. It then arrives at the black GNU Grub version 2.02 screen. I can boot into the system after entering this at the GNU Grub screen: 

```

grub> set pager=1

grub> set root=(hd0,1)
grub> linux /boot/vmlinuz-3.13.0-85-generic root=/dev/sdb1
grub> initrd /boot/initrd.img-3.13.0-85-generic
grub> boot
```

(If I try booting to 3.13.0-86-generic, it says "invalid magic number") I got these instructions from this link: [https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux](https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux)

I've also applied the "Making permanent repairs" code once I've booted into the system. I mean I've udpated grub and installed it by doing the following: 

```

update-grub
# grub-install /dev/sdb
Installing for i386-pc platform.
Installation finished. No error reported.
```

None of this seems to work. Every time I restart I have to boot through the GNU Grub screen again
using the same code I first posted. 

Any advice? I can't seem to boot to the 3.13.0-86-generic nor can I boot as I normally did even using the 3.13.0-85-generic. 

Thanks in advance. Let me know if I can clarify anything.

---

### Post by grahammechanical on 2016-05-21
There is one thing that I have noticed. To load Ubuntu you set root=(hdo,1). But to re-install Grub you grub-install /dev/sdb

hdo,1 = first hard disk, first partition. What Linux calls sda, Grub calls hdo. sdb = second hard disk. You can either re-install grub to /dev/sda or set the BIOS utility to boot off of the second hard disk. 

Regards.

---

