---
title: "Grub rescue - not booting after a partition deletion"
date: 2012-11-24
forum: Installation &amp; Upgrades
---

### Post by SuperFabius on 2012-11-24
Hi all,
this is a problem that happened to me after deleting a partition. Hoping to help someone with the same issue.

* * * Scenario (various linux logical partitons):

Ubuntu 12.04 on /dev/sda12.
Fedora on /dev/sda10.
kubuntu 12.04 on /dev/sda9.
Swap on /dev/sda5
Others on /dev/sda6..7.
Extetended partion on /dev/sda4, wich "owns" /dev/sda5..12.
Primry partitions on /dev/sda1..3

All linux partitions have grub on partition boot sector (*NOT* in the MBR).

In the MBR there is a multi-boot manager program to boot from the various installations.


* * * Problem occurred:

Deleted partition sda11 (Fedora). After sda11 deletion, old sda12 (Uduntu) becames sda11.
When grub2 boots Ubuntu shows this error: 

no such partion
grub rescue>


* * * Solution:

Fom Grub rescue prompt:

```

set                                    # to see "old" stored config
set prefix=(hd0,msdos11)/boot/grub     # to correct partition to load (msdos11 -> sda11)
set root=hd0,msdos11                   # to correct partition to load
insmode normal                         # load "normal"
normal                                 # start with usual boot screen
```

From Ubuntu terminal (after booted normally):

```

sudo grub-install --force --recheck /dev/sda11          # to reinstall grub on /dev/sda11 boot sector with correct parameters
sudo update-grub                                        # to update /boot/grub/grub.cfg

```


* * * References:

1. [http://www.terabyteunlimited.com/kb/article.php?id=408](http://www.terabyteunlimited.com/kb/article.php?id=408)
2. [http://superuser.com/questions/419876/grub-reinstall-after-partition-name-change](http://superuser.com/questions/419876/grub-reinstall-after-partition-name-change)
3. [http://ward.vandewege.net/blog/2011/08/grub-rescue-commands/](http://ward.vandewege.net/blog/2011/08/grub-rescue-commands/)



Cheers.

---

