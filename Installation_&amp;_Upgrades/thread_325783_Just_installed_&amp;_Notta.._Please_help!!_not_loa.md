---
title: "Just installed &amp; Notta.. Please help!! not loading dual boot menu"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by digix on 2006-12-26
Hello all and thanks in advance for helping me out here. I have a Dell 8200 2.4/512/200GB running XP Pro as with many other folks i am attempting to wean from Microsoft.. I decided to install factory CD Ubuntu ver 6.06 LTS and allowed ubuntu to create partition all looked well so i installed and on reboot this is the message received..

GRUB Loading Stage1.5.
GRUB Loading, please wait.....
Error 2


After research I believe this to be the Dual Boot program but cannot seem to get this resolved. Any Advise is much appreciated..

---

### Post by bulldog on 2006-12-26
2 : Bad file or directory type
    This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO. 

Boot into the live cd and type in a terminal [ALT+F2 -->type gnome-terminal]
```
sudo fdisk -l (l as in like)
```
And copy the output on this forum please.

---

### Post by digix on 2006-12-26
fdisk: invalid option   --  I

then gives usage of commands for fdisk: -b ssz, -u , -v etc.

please advise

---

### Post by bulldog on 2006-12-26
Just copy and paste the command sudo fdisk -l

---

