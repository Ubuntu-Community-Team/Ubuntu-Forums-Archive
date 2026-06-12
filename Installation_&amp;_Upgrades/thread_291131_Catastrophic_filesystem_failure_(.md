---
title: "Catastrophic filesystem failure :("
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by rc55 on 2006-11-02
Hi,

I'm having major troubles with my Ubuntu Dapper install in as far as, the system ran a fsck on startup, found a ton of errors which required manual repairing - so I ran fsck manually and answered yes to all the questions and the system no longer boots (Grub Error 15).

In addition, I tried to mount the drive from a liveCD and the only folder that exists is lost+found which is inaccessible.

The mount command I used was:
mkdir /home/ubuntu/Desktop/mnt
mount /dev/sda1 /home/ubuntu/Desktop/mnt

Have I lost all my data? :(

Any help greatly appreciated.

Ruairi

---

### Post by rc55 on 2006-11-02
For anyone searching I managed to solve it.

The manual repair relocated pretty much the entire filesystem inside lost+found, and all the folders were named with a #3197635 style reference.

I had to 

```
sudo chmod 777 /home/ubuntu/Desktop/mnt/lost+found
```

so Nautilus could browse it.

Now I face the arduous task of moving all the files from this huge hard drive onto another one and try a re-install!

Not a complete loss though! :D

Ruairi

---

### Post by galileon on 2006-11-02
indeed, error 15 is when it cant find the kernel files to load

[http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable](http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable)

---

