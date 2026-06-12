---
title: "grub error 17"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by moustacheky on 2006-06-16
hi, i just installed ubuntu on a new partition on my hard disc.
i also have winxp installed.

getting the live cd to install was quite a pain, but eventually i managed to get it to work. i was all exited about booting my own ubuntu for the first time when i got a
grub error 17 message, and  couldn't do anything but reboot with the live cd... 

now what?

these are my partitions

/dev/hda1   *          63    41945714    20972826    7  HPFS/NTFS
/dev/hda2        41945715   331999289   145026787+   7  HPFS/NTFS
/dev/hda3       331999290   396419939    32210325   83  Linux
/dev/hda4       396419940   398283479      931770   82  Linux swap / Solaris

---

### Post by moustacheky on 2006-06-16
these are my partitions

/dev/hda1   *          63    41945714    20972826    7  HPFS/NTFS
/dev/hda2        41945715   331999289   145026787+   7  HPFS/NTFS
/dev/hda3       331999290   396419939    32210325   83  Linux
/dev/hda4       396419940   398283479      931770   82  Linux swap / Solaris

---

### Post by confused57 on 2006-06-16
When your computer boots up and the grub screen is displayed, make sure the Ubuntu kernel is highlighted...press "e", looks like the root should be (hd0,2), change if it isn't and try booting(I think you press "b".  If this boots you make the change permanent in your menu.lst.

If this doesn't work, boot up with the live cd, open up a terminal, enter:

```
fdisk -l
```
The -l is a lowercase "L"
This should list your partitions.

---

### Post by moustacheky on 2006-06-16
wtf..

ALL MY PARTITIONS ARE GONE????

i have no idea how this happened.. i thought i would try reinstalling windows, but when the installer asked on what partition i wanted to do this, i could only chose 1 partition: my entire disc...

after rebooting the live cd, gparted confirms that i ve got no partitions and only one big unallocated disc...

how did this happen... and more important; is there ANY way to fix this? this really really REALLY blows.........:-(

---

