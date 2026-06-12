---
title: "Configuring grub2-pc after cloning a drive"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by secondsystem on 2011-01-17
Hi guys, I just used dd to duplicate a 160gb drive to a 2TB in Ubuntu 10.  I cloned all of the data over and then used gparted to resize leaving room for swap space.  The install that I cloned used grub-pc, and my ubuntu usb key install uses that as well. I'm having a hard time getting a clear answer on how to configure grub-pc while booted from the USB drive.  

I've tried running /usr/sbin/grub-mkconfig but i get error: cannot find device for / (is /dev mounted?).  I tried mounting both sda and sda1 IE:  mount /dev/sda /mnt -t ext4.  What am I doing wrong?

---

### Post by secondsystem on 2011-01-17
Ok, so far as i can tell the procedure for doing this should be something like the following:

mount -odev /dev/sda1 ~/mountpoint
sudo chroot ~/mountpoint
grub-install /dev/sda1

I keep getting

```
/usr/sbin/grub-probe: error: cannot find a device for ~/mountpoint//boot/grub (is /dev mounted?).

```

---

### Post by secondsystem on 2011-01-18
doesn't anybody screen these calls?

---

### Post by pl@yer on 2011-01-18
what are the results of this command?

```

# ls -l /dev|grep sd

```

---

### Post by secondsystem on 2011-01-18
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bd59b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243112  1952796640+  83  Linux
/dev/sda2          243112      243202      717824    5  Extended

Disk /dev/sdb: 4025 MB, 4025810432 bytes
124 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000818f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1022     3928537    c  W95 FAT32 (LBA)

```

---

### Post by pl@yer on 2011-01-18
I will admit I am not familiar with the new grub but have done this several times with the old one.

I just read that you do not need to chroot anymore. You can just run.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

```

sudo grub-install --root-directory=~/mountpoint /dev/sda1

```

---

### Post by secondsystem on 2011-01-18
I noticed that I had not set the the boot flag, so now that is done.  I tried what you said:

```

ubuntu@ubuntu:~$ sudo mount -odev /dev/sda1 ~/mountpoint 
ubuntu@ubuntu:~$ sudo grub-install --root-directory=~/mountpoint /dev/sda1
/usr/sbin/grub-probe: error: cannot find a device for ~/mountpoint/boot/grub (is /dev mounted?).
ubuntu@ubuntu:~$ 

```

---

### Post by pl@yer on 2011-01-18
what kernel version do you have booted?
```

uname -a

```

---

### Post by oldfred on 2011-01-18
Do not install to the partition sda1 but to the drive sda.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda1 and want grub2 in drive sda's MBR:
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

---

### Post by secondsystem on 2011-01-18
```
root@ubuntu:/# uname -a
Linux ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux

```

---

### Post by secondsystem on 2011-01-18
> **oldfred said:**
> Do not install to the partition sda1 but to the drive sda.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda1 and want grub2 in drive sda's MBR:
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

This is exactly the solution, thanks so much for the help.  So often the answer is something simple like this.

---

### Post by secondsystem on 2011-01-18
> **oldfred said:**
> Do not install to the partition sda1 but to the drive sda.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda1 and want grub2 in drive sda's MBR:
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

This is exactly the solution, thanks so much for the help.  So often the answer is something simple like this.

---

