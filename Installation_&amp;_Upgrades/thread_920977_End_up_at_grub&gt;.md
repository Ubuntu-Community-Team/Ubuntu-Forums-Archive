---
title: "End up at grub&gt; ?"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by MissingScrews on 2008-09-15
First, I install ubuntu on 160GB SATA and the install goes through, but when I restart I end up at grub> .

Other issues I'm having is my PATA drives are being viewed as sd:

EX:
160 SATA = sda
500 SATA = sdb
40 PATA = sdc
80 PATA = sdd

Tried the GUI install and the Live CD install and I continue to end up at grub>

Any ideas?

I'm using a Pentium 4 HT 3.0GHz.

---

### Post by caljohnsmith on 2008-09-15
I'm not sure of the technical details, but Hardy labels all HDDs as sdX instead of also using hdX, so don't let that worry you. When you start up and get the Grub prompt, try:
```
grub> find /boot/grub/stage1
grub> find /boot/grub/menu.lst

```
And post the output of both of those commands. Next boot your Live CD, open a terminal and do:
```
sudo fdisk -lu
```
Post the results of that, and also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
And post the results of that. That should give us a good place to start in troubleshooting your problem.

---

### Post by MissingScrews on 2008-09-15
grub> find /boot/grub/stage1           'Error 15: File not found'
grub> find /boot/grub/menu.lst       'Error 15: File not found'

sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb93a63f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    10008494     5004216   82  Linux swap / Solaris
/dev/sda2        10008495   312576704   151284105   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1c295693

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976768064   488384001   83  Linux

Disk /dev/sdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00b900b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    80292869    40146403+  83  Linux

Disk /dev/sdd: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders, total 156312576 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97e097e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   156312449    78156193+  83  Linux

sudo mount /dev/sda2 /mnt
cat /mnt/boot/grub/menu.lst           'No such file or directory'

So clearly stuff is missing?

---

### Post by caljohnsmith on 2008-09-15
Yes, it looks like you're missing some files. Do you know for sure which HDD you are booting from? Is it the 160 GB Ubuntu drive? 

While you have sda2 mounted on /mnt, please post:
```
ls -l /mnt
ls -lR /boot
```
Note that is a lower-case L, not a one.

---

### Post by MissingScrews on 2008-09-15
ls -l /mnt

total 88
drwxr-xr-x   2 root root    4096 2008-09-15 19:38 bin
drwxr-xr-x   2 root root    4096 2008-09-15 19:37 boot
lrwxrwxrwx   1 root ubuntu    11 2008-09-15 19:27 cdrom -> media/cdrom
drwxr-xr-x   4 root root    4096 2008-07-02 10:26 dev
drwxr-xr-x 120 root root    4096 2008-09-15 19:38 etc
drwxr-xr-x   2 root ubuntu  4096 2008-09-15 19:27 home
drwxr-xr-x   2 root root    4096 2008-07-02 10:16 initrd
lrwxrwxrwx   1 root ubuntu    33 2008-09-15 19:37 initrd.img -> boot/initrd.img-2.6.24-19-generic
drwxr-xr-x  16 root root    4096 2008-09-15 19:38 lib
drwx------   2 root root   16384 2008-09-15 19:26 lost+found
drwxr-xr-x   4 root root    4096 2008-07-02 10:16 media
drwxr-xr-x   2 root root    4096 2008-04-15 05:53 mnt
drwxr-xr-x   2 root root    4096 2008-07-02 10:16 opt
drwxr-xr-x   2 root root    4096 2008-04-15 05:53 proc
drwxr-xr-x   3 root root    4096 2008-09-15 19:37 root
drwxr-xr-x   2 root root    4096 2008-09-15 19:38 sbin
drwxr-xr-x   2 root root    4096 2008-07-02 10:16 srv
drwxr-xr-x   2 root root    4096 2008-04-19 05:05 sys
drwxrwxrwt   2 root root    4096 2008-09-15 19:38 tmp
drwxr-xr-x  11 root root    4096 2008-07-02 10:18 usr
drwxr-xr-x  15 root root    4096 2008-07-02 10:34 var
lrwxrwxrwx   1 root ubuntu    30 2008-09-15 19:37 vmlinuz -> boot/vmlinuz-2.6.24-19-generic

ls -lR /boot

-rw-r--r-- 1 root root  422667 2008-06-18 18:11 abi-2.6.24-19-generic
-rw-r--r-- 1 root root   80049 2008-06-18 18:11 config-2.6.24-19-generic
-rw-r--r-- 1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root  905146 2008-06-18 18:11 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root 1920472 2008-06-18 18:11 vmlinuz-2.6.24-19-generic

---

### Post by caljohnsmith on 2008-09-15
My mistake, while sda2 is mounted on /mnt, do the following:
```
ls -lR /mnt/boot/
```
Also:
```
sudo grub
grub> find /grub/stage1 
grub> quit
```
Please post the output.

---

### Post by MissingScrews on 2008-09-15
Originally I let it install, but after the issues I told it not to. Either way I ended up at the grub> screen.

grub> find /boot/grub/stage1 'Error 15: File not found'

---

### Post by caljohnsmith on 2008-09-15
So you installed Ubuntu without Grub? What issues did you have when you tried to install Ubuntu with Grub?

---

### Post by MissingScrews on 2008-09-15
Same issue where I would end up at the grub> screen.

---

### Post by caljohnsmith on 2008-09-15
OK one last check--while sda2 is mounted on /mnt:
```
ls -lR /mnt/boot
```

---

### Post by MissingScrews on 2008-09-15
ls -lR /mnt/boot

-rw-r--r-- 1 root root    422667 2008-06-18 18:11 abi-2.6.24-19-generic
-rw-r--r-- 1 root root     80049 2008-06-18 18:11 config-2.6.24-19-generic
-rw-r--r-- 1 root ubuntu 7891842 2008-09-15 19:37 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root    103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root    905146 2008-06-18 18:11 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root   1920472 2008-06-18 18:11 vmlinuz-2.6.24-19-generic

---

### Post by caljohnsmith on 2008-09-15
OK, from the Live CD, while sda2 is still mounted:
```
sudo grub-install --root-directory=/mnt /dev/sda
sudo chroot /mnt
update-grub
cat /boot/grub/menu.lst
exit
```
Please post the output, then reboot and tell me what happens on start up.

---

### Post by MissingScrews on 2008-09-15
sudo grub-install --root-directory=/mnt /dev/sda

Probing devices to guess BIOS drives. This may take a long time.
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd

sudo chroot /mnt
update-grub

The program 'update-grub' can be found in the following packages:
 * grub-linuxbios
 * grub
 * grub-efi
 * grub-ieee1275
 * grub-pc
Try: apt-get install <selected package>
bash: update-grub: command not found

cat /boot/grub/menu.lst

cat: /boot/grub/menu.lst: No such file or directory

exit

---

### Post by caljohnsmith on 2008-09-15
Do you have internet access from the Live CD? If you do, and while sda2 is mounted:
```
sudo chroot /mnt
apt-get install grub
update-grub
exit
```

---

### Post by MissingScrews on 2008-09-15
Did all that, back to the grub> screen.

---

### Post by MissingScrews on 2008-09-16
Tried 7.04 and I get the same problem.

---

### Post by MissingScrews on 2008-09-16
Figured it out, had to change BIOS to boot drive first. Stupid mistake. Sorry about that.

---

