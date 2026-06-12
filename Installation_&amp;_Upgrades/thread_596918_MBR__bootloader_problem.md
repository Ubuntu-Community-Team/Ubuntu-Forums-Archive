---
title: "MBR / bootloader problem"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by terjeloe on 2007-10-30
I've tried for two days now to re-install ubuntu and tried to get help from some helpfull people at the irc channel,but since it takes a while to reinstall I talk to different people all the time. So I'm starting this thread here.. heres my issue:

First I installed ubuntu on one partition and still had windows on another one. I desided to get rid of the windows partition and deleted all of the partition and made new once:

```
/dev/sda1 /boot    256mb primary ext3
/dev/sda2 /          12gb    primary ext3
/dev/sda5            1.5gb   logical   swap
/dev/sda6 /home  66gb    logical   ext3
```

Under the installation at 95% when it says installing bootloader the install windows just quits.. I try to boot and grub does not show up at all.. when I start with the live cd again and mount the boot folder there is no grub folder in it.. I've also tried to install grub manualy by first mounting /dev/sda2> doing chroot to the mounted folder> grub-install hd0 and grub-intall /dev/sda but I get a error msg"

```
root@ubuntu:/# grub-install /dev/sda
/dev/sda: Not found or not a block device.
root@ubuntu:/# grub-install hd0
Could not find device for /boot: Not found or not a block device.
root@ubuntu:/# grub-install /dev/hd0
Could not find device for /boot: Not found or not a block device.
```

When I do find find/grub/stage1 I in grub I get "error 15 - file not found"


I've tried for two days now.. help! :D

---

### Post by terjeloe on 2007-10-30
bump

Ive also tried sda sda1 sda2 sda0 hd0 in all of the cases..

---

### Post by terjeloe on 2007-10-30
and.. it does not even make a grub directory in the /boot folder..

---

### Post by w116tjb on 2007-10-30
Try this, it worked for me:

[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+repair]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+repair")

---

