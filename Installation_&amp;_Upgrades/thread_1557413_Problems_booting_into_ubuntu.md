---
title: "Problems booting into ubuntu"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by clabdio on 2010-08-20
Hello,

Please I need some help because after two correct installations (I think so) whit a win7, on a toshiba nb200, and when I try to boot in ubuntu, after a few seconds of a black screen apears:

Gave up waiting for root device. common problems
boot args (cat /proc/cmdline)
check rootdelay = did .... ABOUT 15 SECONDS
check root = PERHAPS BUT I DIDN´T TOUCH ANYTHING
missing modules (cat/proc/modules: is /dev)
ALERT! /dev/disk/by-uuid/77466bcc-f76Z-4678-b818-
Dropping to a shell!
busybox v1.13.3 ubuntu 1;1.13.3-...
Enter help 

I've boot from the usb and works fine, reinstall grub 
and use
grub> root (hd0,5) [I]and ok, my fsdisk -l says /dev/sda6 ...
[/I]but when I type

grub> setuo (hd0) it says that cant mount the unit

so please If anybody can help me, 

Thanks a lot;)

---

### Post by oldfred on 2010-08-20
Try this at the Grub prompt if partition is sda6  change 6 if not correct:

set root (hd0,6)
kernel /vmlinuz root=/dev/sda6 ro
initrd /initrd.img
boot
This should boot you into Ubuntu.
Open a terminal in Ubuntu and run

sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by clabdio on 2010-08-21
Thanks a lot, but it doesn't work, this is the screen trying it, sorry I've not experience on Ubuntu

ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found
ubuntu@ubuntu:~$ sudo
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u
            username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo  -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ sudo grub-install --recheck /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ kernel
kernel: command not found
ubuntu@ubuntu:~$ sudo  update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ set root (hd0,5)
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ set root(hd5,0)
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ set root hd5,0
ubuntu@ubuntu:~$ cls
No command 'cls' found, but there are 19 similar ones
cls: command not found
ubuntu@ubuntu:~$ kernel
kernel: command not found
ubuntu@ubuntu:~$ kernel /vmlinuz root=/dev/sda5 ro
kernel: command not found
ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found
ubuntu@ubuntu:~$ sudo
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u
            username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt]  [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...
ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbc92c6ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *            1          52      409600   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2              52        8695    69431223+   7  HPFS/NTFS
/dev/sda3           15222       30402   121930752    7  HPFS/NTFS
/dev/sda4            8695       15222    52424705    5  Extended
/dev/sda5           10851       15037    33622016   83   Linux
/dev/sda6           15037       15222     1488896   82  Linux swap / Solaris
/dev/sda7            8695       10755    16541696   83  Linux
/dev/sda8           10755       10851      768000   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1031 MB, 1031798272 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91f72d24

   Device  Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         126     1007584    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 50)
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 

Thank again

---

### Post by oldfred on 2010-08-22
If you are at ubuntu@ubuntu that should be the terminal in the liveCD not the boot from your hard drive. Your install is either in sda5 or sda7, did you install twice?

To try manual boot you need to be at this prompt from booting your hard drive. Or possibly the rescue prompt:
sh:grub>

From the liveCD you can reinstall grub but need to know if your install is sda5 or sda7?

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
change sda5 to sda7, it that is your install:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by clabdio on 2010-08-23
Hello Oldfred, and thanks for your help. You`re right, I've install twice because the first one doesn't work, so can I unistall one of them? how?

And I will try your lines, I'll keep you updated, thanks again

---

### Post by oldfred on 2010-08-23
You can use gparted to delete partitions or reformat, but you have to know which one you are booting, sda5 or sda7. 

You could then expand partitions, if you reformat you can use for data or move /home into the other space. The system without all your data uses 3 to 6GB and I normally suggest 10-20GB for the root partition. But your data can of course be very large.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

