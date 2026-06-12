---
title: "Installing on external hard drive - partition issues"
date: 2016-06-10
forum: Installation &amp; Upgrades
---

### Post by candydoudou on 2016-06-10
Hello,
I wish to install Ubuntu on a new external hard drive, which I formatted like this with OS X El Capitan disk utility (disk3s2 and disk3s3 are in exFAT) :

```
/dev/disk3 (external, physical):    #:        TYPE                                NAME                              SIZE          IDENTIFIER
                                    0:      GUID_partition_scheme                                                   *1.0 TB       disk3
                                    1:      EFI                                   EFI                               209.7 MB      disk3s1
                                    2:      Microsoft Basic Data                  Ubuntu                            499.9 GB      disk3s2
                                    3:      Microsoft Basic Data                  Windows                           250.0 GB      disk3s3
                                    4:      Apple_HFS                             OS X                              249.7 GB      disk3s4
```

I created the following partitions :

[[IMG]http://img15.hostingpics.net/thumbs/mini_951001DSC0210.jpg[/IMG]]("http://www.hostingpics.net/viewer.php?id=951001DSC0210.jpg")

And after I clicked "install now", I got this message :

[[IMG]http://img15.hostingpics.net/thumbs/mini_977838DSC0212.jpg[/IMG]]("http://www.hostingpics.net/viewer.php?id=977838DSC0212.jpg")

After following the instructions, I still got the same message. I re-formatted the partition in FAT32 with OS X disk utility, but I still get the same message. 
How can I solve this problem ? Thank you in advance.

---

### Post by oldfred on 2016-06-10
Do not know Mac.

But not sure why error? I looks like it is divisible by 8 (check my math), which is what is important.
       Partition does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

Note that full install to any drive other than sda in UEFI mode has some issues. Grub only installs to the ESP - efi system partition on sda. And you then have to copy files to your install.

And Ubuntu's UEFI  grub only installs to the ESP on sda, or not the  external drive and not  to /EFI/Boot/bootx64.efi. For my PC UEFI full  install to a flash drive I  manually copied /EFI/ubuntu on sda's ESP to  flash drive's ESP. Then  copied it again to /EFI/Boot and renamed  shimx64.efi to bootx64.efi. I  then updated fstab to have correct UUID  for ESP on external drive.

The version of grub in a full install is hard coded to find the rest of   grub in /EFI/ubuntu so both copies are required. There are ways to  directly  install grub as bootx64.efi, but then you have to manually  maintain  grub.cfg.

---

### Post by candydoudou on 2016-06-10
Thank you for your answer. 
I initially wanted to directly make a triple boot on my computer, rather than try making a bootable hard drive first... In order to make things easier, I'll just directly make my triple boot then, and try installing on an external hard drive later then.

---

