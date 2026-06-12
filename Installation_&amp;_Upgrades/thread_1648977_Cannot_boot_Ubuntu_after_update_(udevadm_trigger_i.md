---
title: "Cannot boot Ubuntu after update (udevadm trigger is not permitted while udev is uncon"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by yoramdavid on 2010-12-19
Hello,

I upgraded to the last ubuntu last week and since I get the error: "udevadm trigger is not permitted while udev is unconfigured."
I followed different posts on the forums but none helped: 
[http://www.art.ubuntuforums.org/showthread.php?t=1567147](http://www.art.ubuntuforums.org/showthread.php?t=1567147)
[http://ubuntuforums.org/showthread.php?p=10248820&posted=1](http://ubuntuforums.org/showthread.php?p=10248820&posted=1)
[http://answerpot.com/showthread.php?1057567-Re%3A+udevadm+trigger+is+not+permitted+while+udev+is+unconfigured](http://answerpot.com/showthread.php?1057567-Re%3A+udevadm+trigger+is+not+permitted+while+udev+is+unconfigured)

I did the sequence:
"1. Boot liveCD
2. "sudo fdisk -l" to find your boot disk, in my case it is /dev/sda5.
3. "sudo mkdir /media/newroot"
4. "sudo mount /dev/sda5 /media/newroot", change sda1 to whatever your boot disk is.
5. "sudo chroot /media/newroot"
6. apt-get update
7. apt-get dist-upgrade

It seems to work, but I then at about half way through installing, after downloading all the files needed, it tells me not enough space. But there is space, I have 128Mb free on the /boot partition and 1.5 Gb on the /Ubuntu partition. 1.23Gb of Swap.

The command: ""sudo update-initramfs -u -k 2.6.32-24-generic" 
does not do anything.

With the chroot /media/newroot I get the error "cannot run command '/bind/bash': no such file or directory"

I tried from both a USB drive and from a CD.

I realized a "File System" drive (folder (inode/directory) was created during this process which gets out of space.
Location: computer:///, Volume: unknown.
Is there something I am doing wrong?


Any help is welcome, thank you.

---

### Post by cleverbubbles123 on 2010-12-20
EXACTLY the same problem for me, happened after updating to kernel 2.6.35.26-generic yesterday (I think).

---

