---
title: "dapper on second disk"
date: 2006-03-19
forum: Installation &amp; Upgrades
---

### Post by rplantz on 2006-03-19
My 160GB SATA drive has Breezy on one partition and FreeBSD on another. I just installed an 80GB IDE drive and would like to play with Dapper on that drive.

The installation seemed to go well, but I didn't know what to do when it asked if I wanted to instll grub. I already have grub on the SATA drive, and it's set up so I can choose to boot into FreeBSD. I'd like to also be able to boot into Dapper.

I've searched thru lots of multiple-boot posts, but they almost all deal with Windows.

Can anyone point me to some helpful information?

Thanks in advance.

---

### Post by tuxcantfly on 2006-03-19
you need to install to mbr

---

### Post by rplantz on 2006-03-19
[QUOTE=tuxcantfly]you need to install to mbr[/QUOTE]

So I need to install a mbr on my second disk?

Should I allow the CD installer to install grub? Will I be able to convince the installer to put it on the second disk? (I don't think that I want it to install grub on my already working disk.)

---

### Post by tuxcantfly on 2006-03-19
You have to install onto the mbr of the 1st disk.

As for the freebsd booting, you just have to add the freebsd boot entry to /boot/grub/menu.lst once ubuntu is installed; then, you won't need the freebsd bootloader at all.

Alternatively, you could just skip the installation of grub and try using your freebsd bootloader to load ubuntu by adding the appropriate entries

---

### Post by confused57 on 2006-03-20
Would this thread help?  Just change the title to Dapper, I think: 

[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper)

---

### Post by lha on 2006-03-20
You can install Dapper's grub to the mbr of your second drive *or* to the boot sector of Dapper's root partition. (Or to any primary partition's boot sector.) Menu.lst entry would be
```
title Dapper
root (hd1)
chainloader +1
``` for the former and
```
title Dapper
root (hd1,?)
chainloader +1
``` for the latter.

---

### Post by rplantz on 2006-03-21
I apologize for being so dense, but I still cannot get this to work. It seems like my situation is different from most:
1. My first disk is a SATA. It's running Breezy on one partition and FreeBSD on another. I can easily boot into either one through grub.

2. I installed a second disk, but it's an ATA, not SATA. I've installed Dapper on this disk, but I cannot figure out how to tell grub (on the first, SATA disk) about Dapper.

Here's what I've done so far:
```

bob@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9354    75135973+  83  Linux
/dev/hdc2            9355        9729     3012187+   5  Extended
/dev/hdc5            9355        9729     3012156   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2            9363        9727     2931862+  82  Linux swap / Solaris
/dev/sda3            1217        9362    65432745   83  Linux
/dev/sda4   *        9728       19457    78156225   a5  FreeBSD

Partition table entries are not in disk order

```

and my menu.lst
```

# This is for FreeBSD
title FreeBSD
root (hd0,3,a)
kernel /boot/loader

# This is for Dapper
title           Ubuntu, kernel 2.6.15-18-amd64-generic Default
root            (hd2,0)
kernel          /boot/vmlinuz root=/dev/hdc1 ro single
initrd          /boot/initrd.img
boot

--------------

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-10-amd64-k8 Default
root            (hd0,0)
kernel          /boot/vmlinuz root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img
savedefault
boot

------------

```

and my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /home           ext3    defaults        0       2
/dev/sda4       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom2   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# for chroot environment
/home /chroot/home none bind 0 0
/tmp /chroot/tmp none bind 0 0
/dev /chroot/dev none bind 0 0
/proc /chroot/proc proc defaults 0 0
/media/cdrom0 /chroot/media/cdrom0 none bind 0 0
/usr/share/fonts /chroot/usr/share/fonts none bind 0 0

```

And I can mount the new disk:
```

bob@ubuntu:~$ sudo mount -t ext3 /dev/hdc1 /mnt/
bob@ubuntu:~$ ls /mnt
bin   cdrom  etc   initrd      lib    lib64       media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lib32  lost+found  mnt    proc  sbin  sys  usr  vmlinuz
bob@ubuntu:~$

```

---

### Post by randomity on 2006-03-21
Just checking the obvious first...
Are you sure that (hd2,0) is /dev/hdc1? To check, fire up grub and press c or escape or whatever gets you to a command line, and type 
```

root (hd2,0)
kernel /

```
and press tab a few times to see possible completions, to make sure it looks like Dapper.

Once you've found Dapper, type (still at grub)
```

root (hd2,0) # or whatever
kernel /boot/vmlinuz vga=normal root=/dev/hdc1
initrd /boot/initrd.img
boot

```
and see what happens. (I'm assuming those are the right paths for kernel and initrd). It's in vga=normal mode, so you'll get bucketloads of kernel messages if the kernel manages to start. Post back the last couple of lines of that output. It's probably something like "cannot mount root on unknown-device" or something similar, but I don't want to wear my fingers out typing in case it's not ;-)

---

### Post by rplantz on 2006-03-22
[QUOTE=randomity]
```

root (hd2,0)
kernel /

```
and press tab a few times to see possible completions, to make sure it looks like Dapper.
[/code]
[/QUOTE]

What I see is that my current system (breezy) is now on (hd1,0) even though menu.lst clearly shows it on (hd0,0). I can see that my new disk, the IDE one, is now (hd0,0).

Gee, I thought this would be simple. Just add the new disk, install dapper there, edit menu.lst, and start playing.

I think my problems are related to using both a SATA and an IDE disk.

---

### Post by randomity on 2006-03-22
[QUOTE=rplantz]
Gee, I thought this would be simple. Just add the new disk, install dapper there, edit menu.lst, and start playing.[/QUOTE]
From past expeirience, *nothing* that involves menu.lst is *ever* simple. :-(

> I think my problems are related to using both a SATA and an IDE disk.
Nah, if you can pick them both up from a grub prompt then you're ok. Change the root device in menu.lst for Dapper to whatever (hd?,?) seemed to have the files, and try booting.

Did you manage to boot dapper at all from the grub prompt?

---

### Post by rplantz on 2006-03-22
[QUOTE=randomity]
Did you manage to boot dapper at all from the grub prompt?[/QUOTE]

Well, I *think* it tried to boot. But I saw several "failure" messages scroll up the screen.

I'm taking the "start all over again" approach. I've formatted the entire disk as ext3, thus wiping off my dapper. I want to simply play with it for a while as a separate disk to get a feel for what's going on. Then I will try again to install dapper.

---

### Post by randomity on 2006-03-22
Ok.
Good luck!

---

### Post by rplantz on 2006-03-28
[QUOTE=randomity]Ok.
Good luck![/QUOTE]

I got it to work!

First, when I installed Dapper this time, I read the messages from the installer.:rolleyes: Near the end, there is a message saying that it detects another OS, Breezy, then recommends that I install grub. This time I said "yes". In my searching for an answer on the web, I thought that most people said that I should not install this second copy of grub, but I may have misunderstood.

Second, I added the following to my /boot/grub/menu.lst file on my first, SATA, disk:
```

# This is for Dapper
title           Ubuntu, kernel 2.6.15-18-amd64-generic Default
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-18-amd64-generic root=/dev/hdc1 ro single
initrd          /boot/initrd.img-2.6.15-18-amd64-generic
boot

```

I am writing this in Firefox in Dapper. I mounted my Breezy disk:
```

bob@dapper:/mnt/boot/grub$ sudo mount -t ext3 /dev/sda1 /mnt

```
and copy-and-pasted the above lines from the menu.lst file on that disk.

Now I can play with Dapper!
Thanks to all who gave suggestions.

---

