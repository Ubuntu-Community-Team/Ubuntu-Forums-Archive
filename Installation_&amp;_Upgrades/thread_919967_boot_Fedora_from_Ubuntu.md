---
title: "boot Fedora from Ubuntu"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by thecaligarmo on 2008-09-14
So I started off with an Ubuntu PC, and added Fedora onto it, and the reinstalled the grub file for ubuntu in order to get the ubuntu boot menu rather than Fedoras. The issue is that now I can't seem to get Fedora to boot. Here is what I put in the menu.lst file in ubuntu

title Fedora (2.6.26.3-29.fc9.i686)
     root (hd1,1)
     chainloader +1
kernel /boot/vmlinuz-2.6.26.3-29.fc9.i686 ro root=/dev/sdb2 rhgb quiet
initrd /boot/initrd-2.6.26.3-29.fc9.i686.img

If it helps, I have it installed on my second harddrive in the particition /dev/sdb2 and I also took the root(hd1,1) and the kernel/initrd from the fedora menu.lst directly without altering it. Another thing that may help is that I get the following error:

Error 13: Invalid or unsupported executable format

Any help would be greatly appreciated.

---

### Post by caljohnsmith on 2008-09-15
> **thecaligarmo said:**
> So I started off with an Ubuntu PC, and added Fedora onto it, and the reinstalled the grub file for ubuntu in order to get the ubuntu boot menu rather than Fedoras. The issue is that now I can't seem to get Fedora to boot. Here is what I put in the menu.lst file in ubuntu

title Fedora (2.6.26.3-29.fc9.i686)
     root (hd1,1)
     chainloader +1
kernel /boot/vmlinuz-2.6.26.3-29.fc9.i686 ro root=/dev/sdb2 rhgb quiet
initrd /boot/initrd-2.6.26.3-29.fc9.i686.img

If it helps, I have it installed on my second harddrive in the particition /dev/sdb2 and I also took the root(hd1,1) and the kernel/initrd from the fedora menu.lst directly without altering it. Another thing that may help is that I get the following error:

Error 13: Invalid or unsupported executable format

Any help would be greatly appreciated.
One option would be to look inside the menu.lst/grub.conf file that Fedora uses, and just copy over the Fedora entries. Or, if you want a really easy solution, just put this in your Ubuntu menu.lst:
```
title Fedora
root  (hdX,Y)
configfile /boot/grub/menu.lst

```
You used (hd1,1) before for Fedora, but if Fedora is on the same drive as Ubuntu, it should be in the form (hd0,X). Also, in the above entry, make sure you give the correct full path to menu.lst or grub.conf, whichever Fedora uses. If you would like more specifics, then please post the output of:
```
sudo fdisk -lu
```
And let me know which is your Fedora partition. Let me know how it goes. :)

---

### Post by thecaligarmo on 2008-09-16
Here you go:
```
Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfa88fa88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    76903154    38451546   83  Linux
/dev/sda2        76903155    80292869     1694857+  82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1af11af0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *    39616290    40676579      530145   82  Linux swap / Solaris
/dev/sdb2              63    39616289    19808113+  83  Linux
/dev/sdb3        40676580    80292869    19808145   83  Linux

Partition table entries are not in disk order

```

Also, that is what I had originally done. I went into Fedora's menu.lst and literally copied and pasted the details into my Ubunut's menu.lst But even after doing that it did not work. That is how I know the position should be (hd1,1) and also how I know what the kernal and everything is. 

After the original text did not work I also tried the following varieties:
```
chainloader +1
```
and then another time I replaced the root with:
```
/dev/sdb2
```
when instead I used to have some random UUID code for the root. All of these methods have not worked yet and all repeat the same error.

---

### Post by caljohnsmith on 2008-09-16
OK, from Ubuntu, open a terminal and do:
```
sudo umount /dev/sdb2
```
Don't worry if it gives an error complaining sdb2 is not mounted, that command is just to make sure. Then do:
```
sudo mount /dev/sdb2 /mnt
ls -lR /mnt/boot
ls -l /mnt/grub
```
Please post the above output. And if you can find the menu.lst or grub.conf in the above listings, please print out the contents of it with the "cat" command if you know how.

---

### Post by thecaligarmo on 2008-09-17
Ok so here is the output of the first one (from /mnt/boot):
```
/mnt/boot:
total 11500
-rw-r--r--+ 1 root root   86348 2008-05-01 03:34 config-2.6.25-14.fc9.i686
-rw-r--r--+ 1 root root   88852 2008-09-03 00:50 config-2.6.26.3-29.fc9.i686
drwxr-xr-x+ 3 root root    4096 2008-05-07 18:41 efi
drwxr-xr-x+ 2 root root    4096 2008-09-12 03:58 grub
-rw-------+ 1 root root 2702074 2008-09-12 01:04 initrd-2.6.25-14.fc9.i686.img
-rw-------+ 1 root root 2704752 2008-09-12 08:51 initrd-2.6.26.3-29.fc9.i686.img
-rw-r--r--+ 1 root root  112076 2008-04-03 14:16 memtest86+-2.01
-rw-r--r--+ 1 root root  892575 2008-05-01 03:34 System.map-2.6.25-14.fc9.i686
-rw-r--r--+ 1 root root  916077 2008-09-03 00:50 System.map-2.6.26.3-29.fc9.i686
-rwxr-xr-x+ 1 root root 2088288 2008-05-01 03:34 vmlinuz-2.6.25-14.fc9.i686
-rwxr-xr-x+ 1 root root 2125184 2008-09-03 00:50 vmlinuz-2.6.26.3-29.fc9.i686

/mnt/boot/efi:
total 4
drwxr-xr-x+ 3 root root 4096 2008-05-07 18:41 EFI

/mnt/boot/efi/EFI:
total 4
drwxr-xr-x+ 2 root root 4096 2008-05-07 18:41 redhat

/mnt/boot/efi/EFI/redhat:
total 212
-rwxr-xr-x+ 1 root root 211919 2008-04-07 10:31 grub.efi

/mnt/boot/grub:
total 332
-rw-r--r--+ 1 root root     82 2008-09-12 01:04 device.map
-rw-r--r--+ 1 root root  11768 2008-09-12 01:04 e2fs_stage1_5
-rw-r--r--+ 1 root root  11528 2008-09-12 01:04 fat_stage1_5
-rw-r--r--+ 1 root root  10776 2008-09-12 01:04 ffs_stage1_5
-rw-------+ 1 root root   1074 2008-09-12 03:58 grub.conf
-rw-------+ 1 root root   1074 2008-09-12 03:58 grub.conf~
-rw-r--r--+ 1 root root  10768 2008-09-12 01:04 iso9660_stage1_5
-rw-r--r--+ 1 root root  12440 2008-09-12 01:04 jfs_stage1_5
lrwxrwxrwx+ 1 root root     11 2008-09-12 01:04 menu.lst -> ./grub.conf
-rw-r--r--+ 1 root root  10984 2008-09-12 01:04 minix_stage1_5
-rw-r--r--+ 1 root root  13376 2008-09-12 01:04 reiserfs_stage1_5
-rw-r--r--+ 1 root root  66003 2008-04-11 13:02 splash.xpm.gz
-rw-r--r--+ 1 root root    512 2008-09-12 01:04 stage1
-rw-r--r--+ 1 root root 110532 2008-09-12 01:04 stage2
-rw-r--r--+ 1 root root  11040 2008-09-12 01:04 ufs2_stage1_5
-rw-r--r--+ 1 root root  10376 2008-09-12 01:04 vstafs_stage1_5
-rw-r--r--+ 1 root root  13016 2008-09-12 01:04 xfs_stage1_5

```

For the /mnt/grub... I assume you wanted me to actually check the /mnt/boot/grub folder so here it is:
```
total 332
-rw-r--r--+ 1 root root     82 2008-09-12 01:04 device.map
-rw-r--r--+ 1 root root  11768 2008-09-12 01:04 e2fs_stage1_5
-rw-r--r--+ 1 root root  11528 2008-09-12 01:04 fat_stage1_5
-rw-r--r--+ 1 root root  10776 2008-09-12 01:04 ffs_stage1_5
-rw-------+ 1 root root   1074 2008-09-12 03:58 grub.conf
-rw-------+ 1 root root   1074 2008-09-12 03:58 grub.conf~
-rw-r--r--+ 1 root root  10768 2008-09-12 01:04 iso9660_stage1_5
-rw-r--r--+ 1 root root  12440 2008-09-12 01:04 jfs_stage1_5
lrwxrwxrwx+ 1 root root     11 2008-09-12 01:04 menu.lst -> ./grub.conf
-rw-r--r--+ 1 root root  10984 2008-09-12 01:04 minix_stage1_5
-rw-r--r--+ 1 root root  13376 2008-09-12 01:04 reiserfs_stage1_5
-rw-r--r--+ 1 root root  66003 2008-04-11 13:02 splash.xpm.gz
-rw-r--r--+ 1 root root    512 2008-09-12 01:04 stage1
-rw-r--r--+ 1 root root 110532 2008-09-12 01:04 stage2
-rw-r--r--+ 1 root root  11040 2008-09-12 01:04 ufs2_stage1_5
-rw-r--r--+ 1 root root  10376 2008-09-12 01:04 vstafs_stage1_5
-rw-r--r--+ 1 root root  13016 2008-09-12 01:04 xfs_stage1_5

```

(If it helps, there is no file /mnt/grub so I wouldn't know what to check anyway)

I don't know the cat command, but this is what I typed (after some research).. so tell me if I typed it wrong:
```
 cat <path>/menu.lst 
```

And I got this result:
```
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd1,1)
#          kernel /boot/vmlinuz-version ro root=/dev/sdb2
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd1,1)/boot/grub/splash.xpm.gz
hiddenmenu
password --md5 *****
title Fedora (2.6.26.3-29.fc9.i686)
	root (hd1,1)
	kernel /boot/vmlinuz-2.6.26.3-29.fc9.i686 ro root=UUID=bc954c44-8640-4da4-b2ca-cf46c18b22d4 rhgb quiet
	initrd /boot/initrd-2.6.26.3-29.fc9.i686.img
title Fedora (2.6.25-14.fc9.i686)
	root (hd1,1)
	kernel /boot/vmlinuz-2.6.25-14.fc9.i686 ro root=UUID=bc954c44-8640-4da4-b2ca-cf46c18b22d4 rhgb quiet
	initrd /boot/initrd-2.6.25-14.fc9.i686.img
title Ubuntu 8.04.1, kernel 2.6.24-19-generic
	root (hd0,0)
	kernel /boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 quiet splash
	initrd /boot/initrd.img-2.6.24-19-generic
	quiet

```

Note that the Ubuntu section had been previously added by myself so that I can access Ubuntu after I had installed Fedora.

---

### Post by confused57 on 2008-09-17
You might try a configfile entry, as caljohnsmith suggested:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Add the following configfile entry to the end of your Ubuntu menu.lst:
```
title  Fedora
configfile (hd1,1)/boot/grub/menu.lst
```
or
```
title  Fedora
configfile (hd1,1)/boot/grub/grub.conf
```

---

### Post by caljohnsmith on 2008-09-17
> **confused57 said:**
> You might try a configfile entry, as caljohnsmith suggested:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Add the following configfile entry to the end of your Ubuntu menu.lst:
```
title  Fedora
configfile (hd1,1)/boot/grub/menu.lst
```
+1. I wasn't around to post, so thanks for that confused57. That's exactly what I would try. :)

---

### Post by thecaligarmo on 2008-09-18
That last one ended up working. Thanks much!

---

