---
title: "Ubuntu filesystem Error"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by georgeep on 2008-09-05
mount: Mounting /dev/sda1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/ .static/dev failed: No such file or
directory
mount: Mounting /dev on /root/dev failed:No such file or directory
Target filesystem doesn't have /sbin/init

This is the problem my server is giving and i can get pass the last line

Please i need this help argently to save all my web content:
Now i have done this with a live CD but still nothing

sudo mount -t ext3 -o rw /dev/hda1 /mnt
sudo chroot /mnt
sudo apt-get update; apt-get upgrade; apt-get install udev

I can't get the system to upgrade

---

### Post by overdrank on 2008-09-06
See duplicate thread here
[http://ubuntuforums.org/showthread.php?t=911023](http://ubuntuforums.org/showthread.php?t=911023)
Thread closed :)

---

