---
title: "Alternate CD install with LVM, cannot install GRUB"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by b0wter on 2011-10-14
I am using the alternate CD (running from a bootable USB stick created by unetbootin) to install Ubuntu because I want to use the full disk encryption. (I am using this guide: [http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/](http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/) )

Problem is that I cannot install GRUB2 and I think I do know why, but I don't know how to solve it.
When the setup wants to know if it should install GRUB I say ok but then the screen goes red and I get an error message. I've looked at the system log and it tries to call the grub install with the option "-force /dev/sda" which does not seem to be correct because thats the USB stick I am installing from, the HDD is /dev/sdb.

Can someone tell me how to install GRUB in a correct way?
I tried with "-force /dev/sdb" but it gives some errors:

```

mount: mounting non on /proc failed: Device or resource busy
mount: can't find sysfs in /etc/fstab
chroot: cant change root directory to --no-floppy: No such file or directory

```

---

