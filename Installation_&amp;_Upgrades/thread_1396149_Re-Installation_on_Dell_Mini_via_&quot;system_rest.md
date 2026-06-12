---
title: "Re-Installation on Dell Mini via &quot;system restore&quot;: BOOT ERROR"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by LeFou on 2010-02-01
My Mini13 came with hardy preloaded, and it's got pretty messed up since, so I'd like to restore factory OS via a grub entry that looks like this:

title System Restore
root (hd0,2)
chainloader +1
boot

This points to a partition which, when mounted, has this stuff in it:

bootfs.img  initrd0.img  install.sh   logo.png    syslinux.cfg  vmlinuz
boot.msg    install.cfg  ldlinux.sys  rootfs.img  vesamenu.c32

I'm not a computer, but that looks pretty good to me... but when I select this grub option it just says

BOOT ERROR

is there a log or something that might give me more info about the error?

---

### Post by Leppie on 2010-02-01
i'm not sure, but you could try and have a look at the install.sh script.
maybe it shows what it does.

---

### Post by LeFou on 2010-02-02
that script says 

> # This is the script that will be placed onto the USB flash drive, that will
# run on bootup to install the software onto the device.

This is not what I'm doing. I think I just want the equivalent of 

(grub prompt) 
> kernel (hd0,2)/vmlinuz
should I add root=/dev/sda3 here?

> initrd (hd0,2)/initrd0.img
> boot

At issue (maybe) is that there isn't a boot partition? here's df -h

> /dev/sda2              35G   12G   22G  36% /
varrun                501M  100K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   52K  501M   1% /dev
devshm                501M     0  501M   0% /dev/shm
lrm                   501M  1.9M  499M   1% /lib/modules/2.6.24-24-lpia/volatile
/dev/sda3             1.4G  1.2G  205M  86% /mnt

---

### Post by Leppie on 2010-02-02
> **LeFou said:**
> that script says 
> # This is the script that will be placed onto the USB flash drive, that  will
# run on bootup to install the software onto the devic
then that's not what you're looking for...

> **LeFou said:**
> This is not what I'm doing. I think I just want the equivalent of 

(grub prompt) 
> kernel (hd0,2)/vmlinuz
should I add root=/dev/sda3 here?
(hd0,2) is the same as /dev/sda3

> **LeFou said:**
> At issue (maybe) is that there isn't a boot partition? here's df -h
you do not necessarily have to have a boot partition.

it looks like sda3 contains a bit more than the files you listed (1.2gb used)...

---

### Post by darkod on 2010-02-02
Since you are not dual booting at all, any reason why not to try simply installing any version of ubuntu? A system restore to factory state will not bring back your data and any settings anyway. Why not a clean install of Karmic, or Jaunty or what ever?

---

### Post by Leppie on 2010-02-02
> **darkod said:**
> Since you are not dual booting at all, any reason why not to try simply installing any version of ubuntu? A system restore to factory state will not bring back your data and any settings anyway. Why not a clean install of Karmic, or Jaunty or what ever?
good point :)

---

