---
title: "Kernel install error"
date: 2005-04-26
forum: Installation &amp; Upgrades
---

### Post by Tiscan on 2005-04-26
Humm, I just installed a new Ubuntu box and this is what happens when I try to do an apt-get install linux-686 (notet that I am using software raids but not LVM), any ideas?

- Tiscan


Setting up linux-image-2.6.10-5-686 (2.6.10-34) ...
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
File descriptor 7 left open
    Finding all volume groups
  No volume groups found
/usr/sbin/mkinitrd: /dev/evms/.nodes/hdb2: Cannot find LVM device
Failed to create initrd image.
dpkg: error processing linux-image-2.6.10-5-686 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-686:
 linux-image-686 depends on linux-image-2.6.10-5-686; however:
  Package linux-image-2.6.10-5-686 is not configured yet.
dpkg: error processing linux-image-686 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.10-5-686:
 linux-restricted-modules-2.6.10-5-686 depends on linux-image-2.6.10-5-686; however:
  Package linux-image-2.6.10-5-686 is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.10-5-686 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-686:
 linux-restricted-modules-686 depends on linux-restricted-modules-2.6.10-5-686; however:
  Package linux-restricted-modules-2.6.10-5-686 is not configured yet.
dpkg: error processing linux-restricted-modules-686 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.10-5-686
 linux-image-686
 linux-restricted-modules-2.6.10-5-686
 linux-restricted-modules-686
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Tiscan on 2005-04-27
I seem to have everyone stumped? :(

---

### Post by az on 2005-04-27
Did your install go without a hitch?

sudo apt-get -f install

---

### Post by Tiscan on 2005-04-29
Yea the install went fine, didn't notice anything out of the ordinary,

---

### Post by nad on 2005-04-29
See if any of your particulars are here:

[https://bugzilla.ubuntu.com/buglist.cgi?query_format=specific&order=bugs.resolution%2C+relevance+desc&bug_status=__all__&product=&content=linux-image-686](https://bugzilla.ubuntu.com/buglist.cgi?query_format=specific&order=bugs.resolution%2C+relevance+desc&bug_status=__all__&product=&content=linux-image-686)

Edit: Is grub installed to /dev/hdb2? There are raid issues with the installer for this package.

---

### Post by Tiscan on 2005-04-29
Strange, here is my Grub conf entry:

title           Ubuntu, kernel 2.6.10-5-386
root            (hd2,0)
kernel          /vmlinuz-2.6.10-5-386 root=/dev/md2 ro quiet splash
initrd          /initrd.img-2.6.10-5-386
savedefault
boot

The disk layout is pretty simple.  One RAID1 (2 disks, 2 spares) for /boot, RAID5 (4 disks) for swap and RAID5 (4 disks) for /

Why would it be looking on hd2,0 ?

---

### Post by Tiscan on 2005-04-30
More fun:

root@trinity:/etc/mdadm # mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.01
  Creation Time : Sat Apr 23 15:56:09 2005
     Raid Level : raid1
     Array Size : 96256 (94.00 MiB 98.57 MB)
    Device Size : 96256 (94.00 MiB 98.57 MB)
   Raid Devices : 2
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Apr 29 23:57:56 2005
          State : clean
 Active Devices : 2
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 2

           UUID : e0420d85:6b7afb2c:ad5e366c:734ed431
         Events : 0.462

    Number   Major   Minor   RaidDevice State
       0     253        0        0      active sync   /dev/evms/.nodes/hdc1
       1     253        1        1      active sync   /dev/evms/.nodes/hda1

       2     253        3        -      spare   /dev/evms/.nodes/hdb1
       3     253        2        -      spare   /dev/evms/.nodes/hdd1

Looks like hda isn't considered the first drive... could this be my issue?

---

### Post by nad on 2005-04-30
Where are your stage1 and stage2 grub files? Is grub installed to /boot in your / partition, md2? This is where ubuntu would have put them by default, and to tell you the truth, I had a similar issue with installing hoary where I swear I requested grub to install to my /boot partition and only after a second os install did I find out that this was not the case.

Either way, the package installer is definitely looking in the wrong place to install it's new images. Unpackage and hand install or modify the script.

---

