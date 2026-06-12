---
title: "hd boot problems"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by Wyldeman on 2007-04-28
i cant seem to boot tot he hd with out the cd first. after it boots then everything is ok. what did i do wrong and how do i fix the booter (grub ). ive installed several programs and have L.A.M.P. up and going im useing this as a server . i want it to boot buy its self.
Thanks Wydeman

 AMD Sempron(tm) Processor 2800+
via chip set 1 gig mem

---

### Post by bulldog on 2007-04-28
If you boot from hdd do you see the GRUB menu?

And booting from cd means you use the option boot from the first hdd on the cd?

---

### Post by Wyldeman on 2007-04-28
when i reboot it goes to the boot from cd twice then just hangs


booting cd......
booting cd......

i then have to do a hard boot and put the cd in so it boots. i already checked my bios and its cd.floopy hd.
Thanks

---

### Post by Wyldeman on 2007-04-28
ok this might help
> wylde@wylde-server:~$ sudo fdisk -l
Password:

Disk /dev/hdc: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14664   117788548+  83  Linux
/dev/hdc2           14665       15017     2835472+   5  Extended
/dev/hdc5           14665       15017     2835441   82  Linux swap / Solaris


> nano /boot/grub/menu.lst



## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=38319849-1e29-49c4-ae94-9a91f8f55431 r$
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=38319849-1e29-49c4-ae94-9a91f8f55431 r$
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



---

### Post by bulldog on 2007-04-28
You just have one hdd in your machine?
If so, there seems nothing wrong with menu.lst except this strange end of the kernel /boot/vmlinuz line,it ends with 'r$'.

this is how it looks in my menu.lst```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1e44b9d0-9dff-405d-9fbc-58398539106e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```

Can't say if this is the reason of  the malfunction,but something does.

---

### Post by Wyldeman on 2007-04-28
as far as one drive yes and its all for the server . we have a small online business and i have had to redo Gentoo too many times so i was trying out Ubuntu. This server is jst that a serve for online .No winderz .....
As far as booting yes i use the cd and boot from the first hard drive.
i havent a clue what o do . our electric goes out allot here so i need ot to boot buy itself. thats another reason for no other os on the server.
So what do we do . do you think because the drive is listed as ...hdc.... that might have something to do with it?
:confused:

---

### Post by bulldog on 2007-04-28
Well,normally hdc should be hda but if you have just one hdd I can't imagine this won't let you boot.
Is this hdd set as a master device or is the cd-rom master device and hdd a slave.

Can you post your fstab to the forum and maybe your device.map
You have to mount your ubuntu partition to do so,but I think you'll manage.:)

EDIT;
You can set more than one OS on the hdd,and set menu.lst to boot either one of them [ubuntu is the default but can be changed easily]

---

### Post by Wyldeman on 2007-04-28
ok looking in device.map

> (hd0)	/dev/hdc

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=38319849-1e29-49c4-ae94-9a91f8f55431 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=837aa319-303a-4ccb-8bcf-bfbec86ceb59 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
I hope this helps
Thanks Again
 Wyldeman

---

### Post by bulldog on 2007-04-28
Hmm,doesn't really help at all :( 
Everything is listed as it should be,that's the good news,but I don't have a clue why it won't boot without the cd inserted.

The only thing I can think of,is to set to boot from your hdd in the BIOS instead of booting from cd first.

---

### Post by Wyldeman on 2007-04-28
ok i'll try that real quick.   brb
lol

---

### Post by Wyldeman on 2007-04-28
ok i wouldnt have never belived it but that worked. it boots up just fine....lol
Thanks fro ALL the help. i just wish i could have gotten it to work the other way but at least its working now thanks again!!!!!!!!

---

### Post by bulldog on 2007-04-28
No problem,just have fun with it :guitar:

---

