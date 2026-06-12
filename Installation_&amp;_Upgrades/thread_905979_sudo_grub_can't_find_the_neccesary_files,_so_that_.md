---
title: "sudo grub can't find the neccesary files, so that i can boot from harddisk"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by k3ntegra on 2008-08-30
i did "alt F2" to open terminal

then typed sudo grub and clicked the check box and press enter

then when i type find /boot/grub/stage1 or find /grub/stage1 i get the error message "error 15 file not found"

```

Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> find /grub/stage1
find /grub/stage1

Error 15: File not found
grub> 

```

i checked the disk for defects twice and there were no error. My partition are ext3 file journaling for root ( / ) and swap. i even tried the super grub cd and i got similar error, "file not found" . please can someone help, i would really appreciate it.


I also went to the boot directory and only say five files

abi-2.6.24-19-generic
config-2.6.24-19-generic
memtest86+.bin
System.map-2.6.24-19-generic
vmlinuz-2.6.24-19-generic

---

### Post by k3ntegra on 2008-08-31
After going to the boot directory at the swap partition (reads as 42.9GB media not File system) , i could see the grub folder in there.

i could see 10 different files in the grub folder.
when i try to open any of the stage files, it says "couldnt display /media/disk/boot/grub/minix_FILENAME"   in this case FILENAME is a substitute for stage.

i was able to open device map and saw the following

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd

keep in mind i am running ubuntu in live CD mode right now.


still no luck

```

Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /media/disk/boot/grub
find /media/disk/boot/grub

Error 15: File not found
grub> find /media/disk/boot/stage1
find /media/disk/boot/stage1

Error 15: File not found
grub> find /media/disk/boot/grub/stage1
find /media/disk/boot/grub/stage1

Error 15: File not found
grub> find stage1
find stage1

Error 15: File not found
grub> 

```



EDIT:

I've been surfing other topics and tried

```

grub> root (hd1)
root (hd1)

Error 18: Selected cylinder exceeds maximum supported by BIOS

```

I get that same exact error when i try to boot ubuntu from the hard disk. I remember reading something about setting something in harddrive settings in bios to auto, and i'm pretty it is set at that and i still get this error :(

---

### Post by k3ntegra on 2008-08-31
after resintalling ubuntu as "Guided install" instead of "manual install", i was able to fully install it. Because of this i was able to the following things in this thread,
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

but i still get grub error at start up and i still get it when i try to use super grub cd.

```

ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd2,7)
grub> root (hd2,7)
root (hd2,7)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+16 p (hd2,7)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
ubuntu@ubuntu:~$ 

```

---

