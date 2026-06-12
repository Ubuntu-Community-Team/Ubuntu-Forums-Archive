---
title: "BIG Grub problem after WIndows install! cannot reinstall!"
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by amonsul on 2006-07-28
Hi!

After Windows installation i have to reinstall Grub...i know but it dont works!

Look here, i post you the code... (from the Live-CD)

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 7475 60042906 7 HPFS/NTFS

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdc1 * 1 23943 192322116 83 Linux
/dev/hdc2 23944 24321 3036285 5 Extended
/dev/hdc5 23944 24321 3036253+ 82 Linux swap / Solaris
ubuntu@ubuntu:~$


and then the problem...
> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hdc1 /mnt/ubuntu
ubuntu@ubuntu:~$ chroot /mnt/ubuntu
chroot: cannot change root directory to /mnt/ubuntu: Operation not permitted
ubuntu@ubuntu:~$ sudo chroot /mnt/ubuntu
root@ubuntu:/# grub-install /dev/hdc
/dev/hdc: Not found or not a block device.
root@ubuntu:/# sudo grub-install /dev/hdc
/dev/hdc: Not found or not a block device.
root@ubuntu:/# sudo grub-install /dev/hda
/dev/hda: Not found or not a block device.
root@ubuntu:/# fdisk -l
cannot open /proc/partitions
root@ubuntu:/# sudo grub-install /dev/hdc1
/dev/hdc1: Not found or not a block device.
root@ubuntu:/# grub-install /dev/hda1
/dev/hda1: Not found or not a block device.
root@ubuntu:/# grub-install /dev/hdc5
/dev/hdc5: Not found or not a block device.
root@ubuntu:/#


What should i do?

---

### Post by Herman on 2006-07-28
Try this method,
1) Boot a Live CD (Ubuntu, Kubuntu or Knoppix or something like that).
2) Open a terminal
3) Get a GRUB Shell
```
sudo grub
``` 4) Find out exactly which partition is your Linux (Ubuntu) partition,
```
find /boot/grub/stage1
``` 5) root GRUB to that partition, 
```
root (hd0,1)
``` (Where (hd0,1) is the Ubuntu partition). (For you it might be (hd2,0) instead - use whatever the 'find' command above told you).

6) Install GRUB with its first stage to MBR,
```
setup (hd0)
``` 7) Exit the GRUB Shell
```
quit
``` 8) Exit the terminal, remove the Linux Live CD and reboot.

Regards, Herman :D

---

### Post by izle on 2006-07-28
Hi,

perhaps you just have to do a grub-install /dev/hd0 instead of grub-install /dev/hda

[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html)

---

### Post by amonsul on 2006-07-28
I think its a problem with the harddisk:

The story:

1) I´ve installed Ubuntu on primary master  (Disk 1  200GB)

2) yesterday i´ve installed Windows on DISK 2 (60GB). But i needer to disconnect the DISK1 with Ubuntu because Windows will install only on primary master.

So the problem is that now Windows is on the primary master and Ubuntu is setted as slave. But when i start grub (now it works) he cannot find Ubuntu /root  section (because he is searching /root on the primary master)

Here my grub menu.lst

How to change the parameter?

> title		Ubuntu, kernel 2.6.15-26-386 (200GB-Festplatte LOL!!!)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot


---

### Post by izle on 2006-07-28
to change the parameter you need to edit the menu.lst file, for example type 

sudo gedit /boot/grub/menu.lst

you then have to specify where to find the /, ie /dev/hdaX or /dev/hdbX or ... , but I don't know if you have to change "root (hd0,0)".

---

### Post by confused57 on 2006-07-28
I'm not sure if it will work, but you might want to consider this option:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

This assumes both drives(Windows & Ubuntu) will boot separately when connected as primary master drive.

---

