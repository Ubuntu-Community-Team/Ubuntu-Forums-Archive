---
title: "RAID broke after update to karmic - can't boot/mount/do anything!"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by athrpf on 2009-12-11
Hello everyone,

last night I tried to upgrade my 9.04 tp 9.10 . 

My system has two hard drives which used to run in RAID-1 mode using dmraid. I had set up a set of partitions /dev/md0 /dev/md1 /dev/md2 as raid arrays into which I hung my partitions sda0-2, sdb0-2. 

After upgrading to 9.10 and restarting the computer, grub couldn't find /dev/md0 anymore. When I rebooted the computer with 9.04 live cd and tried to mount /dev/sdax, mount told me it couldn't do it since sdax was a linux_raid_partition. 

I am at a point where I'm thinking that I would like to re-install Ubuntu with Grub2 using the native RAID support I heard of. 

My questions are now: 

1. How can I mount the old partitions in order to get my data back?

2. Is Grub2 really that great in supporting RAID 1 that it is worth doing a whole re-install?

Thanks for the help!

---

### Post by phillw on 2009-12-11
Ahhh.... Grub2 and RAID -- Seems to be a sore point with 9.10.

A couple of discussions on the matter ...

[http://ubuntuforums.org/showthread.php?t=1347488&highlight=raid+grub2](http://ubuntuforums.org/showthread.php?t=1347488&highlight=raid+grub2)

[http://ubuntuforums.org/showthread.php?t=1321231&highlight=raid+grub2](http://ubuntuforums.org/showthread.php?t=1321231&highlight=raid+grub2)

[http://ubuntuforums.org/showthread.php?t=1305811&highlight=raid+grub2](http://ubuntuforums.org/showthread.php?t=1305811&highlight=raid+grub2)

and

[http://ubuntuforums.org/showthread.php?t=1323496&highlight=raid+grub2](http://ubuntuforums.org/showthread.php?t=1323496&highlight=raid+grub2)

Should give you some reading material, 'work-arounds' and installation instructions

Regards,

Phill.

---

### Post by athrpf on 2009-12-12
thanks for the response

these threads are mainly about installing grub2. my first problem though is that I would like to save my data before a new install.

I downloaded the ubuntu 9.10 alternate installer CD, burned it and booted from it. Using the recovery mode I was able to mount /dev/md0 again! So now I have access to my files from the shell. 

I am not familiar though with the way the startup of the system works, so I have no clue where I have to change something to make grub able to see the partition /dev/md0 (which is my / ) as well. Does anyone have any suggestions? 

Neither my fstab nor my menu.lst where change in the upgrade process.

any help is greatly appreciated!

---

### Post by athrpf on 2009-12-12
I got it to work - the problem was that my /boot/grub/menu.lst looked like this:
```

title		Ubuntu 9.10, kernel 2.6.31-16-generic
root		/dev/md0
kernel		/boot/vmlinuz-2.6.31-16-generic root=/dev/md0 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic

```

whereas it should've looked like this:

```

title		Ubuntu 9.10, kernel 2.6.31-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-16-generic root=/dev/md0 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic

```

---

