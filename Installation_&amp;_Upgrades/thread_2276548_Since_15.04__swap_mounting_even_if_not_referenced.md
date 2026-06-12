---
title: "Since 15.04 : swap mounting even if not referenced"
date: 2015-05-03
forum: Installation &amp; Upgrades
---

### Post by simon98 on 2015-05-03
Hello,
Since I've installed 15.04, my swap partition on /dev/sda10 is always mounted, even if I don't ask it to.
It should have been an encrypted swap, but I'm not sure it was really encrypted.
Anyway, now, I can't help at disabling it !

I thought I commented out anything related to this partition. Any idea on how could I prevent Ubuntu to mount it again ?

[B]swapon -s :
[/B]
[FONT=Courier New]simon@vivid:~$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda10                                 partition    5970940    0    -1[/FONT]

[B]/etc/fstab :
[/B]
[FONT=Courier New]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=8715bc8a-bd43-4932-981c-703c8a26d802 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=8019-D87D  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda7 during installation
UUID=416d76fd-2d1c-4bc5-95f1-2aa94c6aa0ea /home           ext4    defaults        0       2
# swap was on /dev/sda10 during installation
#UUID=87190a20-dbbc-4c51-8275-3dcb5ac22f99 none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0[/FONT]

**/etc/crypttab :**
[FONT=Courier New]
#cryptswap1 UUID=eaae202c-8f99-43fd-b6e4-9bfd785bbcc7 /dev/urandom swap,offset=1024,cipher=aes-xts-plain64
#cryptswap1 /dev/sda10 /dev/urandom swap,offset=1024,cipher=aes-xts-plain64
#cryptswap1 /dev/disk/by-id/wwn-0x14765524367225933825x-part10 /dev/urandom swap,offset=1024,cipher=aes-xts-plain64[/FONT]

---

### Post by dino99 on 2015-05-03
this is actually an issue for many users  [https://www.google.co.in/search?q=ubuntu+getdeb+archive&oq=ubuntu+getdeb+archive&aqs=chrome..69i57j69i64.9545j0j8&client=ubuntu&sourceid=chrome&es_sm=93&ie=UTF-8#q=ubuntu+cryptswap&tbs=qdr:m](https://www.google.co.in/search?q=ubuntu+getdeb+archive&oq=ubuntu+getdeb+archive&aqs=chrome..69i57j69i64.9545j0j8&client=ubuntu&sourceid=chrome&es_sm=93&ie=UTF-8#q=ubuntu+cryptswap&tbs=qdr:m)

---

### Post by simon98 on 2015-05-03
I think you didn't understand me.
I've already Googled before posting, but **my problem is not to mount my **(crypt)**swap **anymore**... It's to "not mount" it** !

And by the way, your link wasn't leading to any answer. Maybe you should have posted a link this page instead : [http://askubuntu.com/questions/616663/after-new-ubuntu-15-04-installation-startup-asks-for-password-even-though-no-di](http://askubuntu.com/questions/616663/after-new-ubuntu-15-04-installation-startup-asks-for-password-even-though-no-di)

---

### Post by simon98 on 2015-05-19
Solved with a recent update (a few days ago max)...

---

