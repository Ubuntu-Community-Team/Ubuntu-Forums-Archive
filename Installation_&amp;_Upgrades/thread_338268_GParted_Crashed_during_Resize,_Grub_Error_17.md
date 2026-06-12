---
title: "GParted Crashed during Resize, Grub Error 17"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by poebae on 2007-01-14
Okay, here's the situation:

I'd successfully been dual booting Windows XP and Ubuntu, but I decided to do some reshuffling of my hard disk space.

I fired up the GParted Live CD, and started my operations. (see screenshot) I reduced the size of hda5 from 15GB to 500MB, because it wasn't in use. Then I used the freed up space to increase my NTFS partition to 10GB. All was going well until I decided to merge the remaining free space with hda6 (see screenshot). While that was happening, my laptop switched off for no reason at all. 

When I turned it on again, Grub gave me an error 17 report. :rolleyes: 

I booted the Gparted LiveCD and tried again, but every time I tried to do anything with that partition, GParted would just close by itself. This happened when I tried it with the GParted LiveCD, the system rescue disk, and the Ubuntu Live CD.


```

sudo grub

grub> root (hd0,5)
grub> setup (hd0)

   Checking if "/boot/grub/stage1" exists... no
   Checking if "/grub/stage1" exists... no

Error 2: Bad file or directory type
```

I tried all the other possible (hd0,*) entries, but that just tells me "cannot mount selected partition"

The contents of my /etc/fstab are as follows:

```

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

```

I've tried the advice in about 50 threads, with no luck. Most of the threads concerning this problem say that one should edit this and that inside their /boot/grub directory, but there is no directory in my /boot named "grub"

---

