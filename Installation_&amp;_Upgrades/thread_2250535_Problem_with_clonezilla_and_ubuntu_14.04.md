---
title: "Problem with clonezilla and ubuntu 14.04"
date: 2014-10-29
forum: Installation &amp; Upgrades
---

### Post by javier29 on 2014-10-29
Hello!!! I installed ubuntu 14.04 lts with encryption mode and i made a clonezilla image.
The problem starts when i burn the image in a new computer (same  model,hardware, etc...) and does'nt work, when i turn on the computer  only appears a black screen and "grub>".
I tried to update grub with a live cd (  [http://ubuntuforums.org/showthread.php?t=1807307](http://ubuntuforums.org/showthread.php?t=1807307) ), but i can't because  the HDD is encrypted and give me error.

(I tried with others computers too, and doesn't works...)

Any ideas??



Regards.

---

### Post by sudodus on 2014-10-29
I use Clonezilla, but not with encrypted disks. I don't know if it works with encrypted disks. Probably it works with encrypted home.

What should be possible is to clone the drive to another drive of at least the same size using ***dd***, nicknamed 'disk destroyer' because there are no security checks. A minor mistake, for example a typing error may cause massive loss of data. But if you know what you are doing, check and double-check, it is a reliable method.

Assuming x is the source drive letter and y the target drive letter:

```
sudo dd if=/dev/sdx of=/dev/sdy bs=4096
```

or making an image file

```
sudo -s
dd if=/dev/sdx bs=4096 | gzip > target.img.gz
sync
exit    # shut off superuser privileges

```
The image would be smaller if you zeroise the free space before cloning, but I that must be done, when running the system (and the file system is decrypted).


If there are bad sectors (hardware defects) on any of the drives, you should use ***ddrescue*** instead.

-o-

I hope someone else can give better advice (how to use a safer method).

---

