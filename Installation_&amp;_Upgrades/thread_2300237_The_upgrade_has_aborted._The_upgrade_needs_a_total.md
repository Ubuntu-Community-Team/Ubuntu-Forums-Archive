---
title: "The upgrade has aborted. The upgrade needs a total of 69.3 M free space on disk '/boo"
date: 2015-10-24
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2015-10-24
I am trying to upgrade from 15.04 to 15.10
I have sudo apt-get clean. didn't help.

The upgrade has aborted. The upgrade needs a total of 69.3 M free space on disk '/boot'. Please free at least an additional 7,801 k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

---

### Post by deadflowr on 2015-10-24
Is /boot a separate partition?
If so, you need to try to clear out some old kernels.
Here's a quick one-liner, with a nice explanation about it
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)
Note: use the --dry-run option first, to see how it will go before trying it for real.

The apt-get clean command won't have any size affect on any partition except for whatever partition the /var directory is on.
So if boot is separate, then running that command won't do anything to clear space on /boot.
If that makes sense.

---

### Post by hoboy on 2015-10-25
I have followed this link:[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)
But I am still getting the same errors.
ls -as /boot
total 159565
    4 .                                       7883 initrd.img-3.19.0-25-generic.old-dkms
    4 ..                                      7884 initrd.img-3.19.0-26-generic.old-dkms
 1248 abi-3.19.0-32-generic                   7886 initrd.img-3.19.0-27-generic.old-dkms
  175 config-3.19.0-32-generic                7887 initrd.img-3.19.0-28-generic.old-dkms
    1 grub                                    7887 initrd.img-3.19.0-29-generic.old-dkms
 7860 initrd.img-3.19.0-15-generic.old-dkms   7887 initrd.img-3.19.0-30-generic.old-dkms
 7860 initrd.img-3.19.0-16-generic.old-dkms   7887 initrd.img-3.19.0-31-generic.old-dkms
 7880 initrd.img-3.19.0-17-generic.old-dkms  21494 initrd.img-3.19.0-32-generic
 7880 initrd.img-3.19.0-18-generic.old-dkms     12 lost+found
 7880 initrd.img-3.19.0-20-generic.old-dkms    162 memtest86+.bin
 7880 initrd.img-3.19.0-21-generic.old-dkms    164 memtest86+.elf
 7881 initrd.img-3.19.0-22-generic.old-dkms    164 memtest86+_multiboot.bin
 7883 initrd.img-3.19.0-23-generic.old-dkms   3553 System.map-3.19.0-32-generic
 7883 initrd.img-3.19.0-24-generic.old-dkms   6496 vmlinuz-3.19.0-32-generic
-----------------------------------------------------------------------------------------------
df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         7.3G     0  7.3G   0% /dev
tmpfs                        1.5G  9.3M  1.5G   1% /run
/dev/mapper/ubuntu--vg-root  910G  152G  712G  18% /
tmpfs                        7.3G   22M  7.3G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        7.3G     0  7.3G   0% /sys/fs/cgroup
/dev/sda1                    236M  165M   59M  74% /boot
cgmfs                        100K     0  100K   0% /run/cgmanager/fs
tmpfs                        1.5G   60K  1.5G   1% /run/user/1000
------------------------------------------------
How can I increase the size of /dev/sda1                    236M  165M   59M  74% /boot

---

