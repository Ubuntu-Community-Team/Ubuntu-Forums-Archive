---
title: "No Space Left Persistent Mode USB Boot"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by Brianivander on 2013-02-24
I am trying to boot to xubuntu persistent mode. I had tried with ubuntu 12.10 but it resulted the same. 

I was going to install boot-repair to fix my windows 7. Now everytime i try to install, it always said that I don't have space left.

I've been using linux (ubuntu) for a couple of months, but I never understand about commands from terminal so please give me directions step by step.

I am tired of googling but have no result on fixing my problem. I find out that some solutions is to command df -l
so, this is my usb

```
 xubuntu@xubuntu:~$ df -l
Filesystem     1K-blocks   Used Available Use% Mounted on
/cow              150752 150736         0 100% /
udev              953776      4    953772   1% /dev
tmpfs             385076    888    384188   1% /run
/dev/sdb1         992344 886772    105572  90% /cdrom
/dev/loop0        680704 680704         0 100% /rofs
tmpfs             962688     44    962644   1% /tmp
none                5120      0      5120   0% /run/lock
none              962688     88    962600   1% /run/shm
none              102400     16    102384   1% /run/user

```I could see that actually I still have lot of space in 
/dev
/run
/tmp/run/shm

I wish that the / can have more space by moving some files to the free directories there.

I have tried usin Linux Live usb creator. Unetbootin. But it result the same. NO SPACE LEFT ON DEVICE.

I need your help so I can install boot-repair. Thank you so much.

---

