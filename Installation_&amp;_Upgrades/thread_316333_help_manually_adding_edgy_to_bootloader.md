---
title: "help: manually adding edgy to bootloader"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by abh83 on 2006-12-10
I have a silly problem and i hope someone out there can help me.

First off i have little experience with ubuntu and linux in general.

currently i have 3 OS installed.

1) windows XP Pro
2) ubuntu 6.06 dapper
3) ubuntu 6.10 edgy

When I start my notebook only 2 OS options show up in the bootloader: Windows and ubuntu 6.06 dapper.

It seems this problem ocured while i was installing ubuntu 6.10 edgy. I reached the final stage of the installation around 97% "The Clean up phase" when all of a sudden my notebook switched off automatically.

Is it possible to manually add ubuntu 6.10 edgy to the bootloader?? If so please guide me through the steps!

thx in advance
abh

---

### Post by taurus on 2006-12-10
Just use the same entry for Dapper except replace the kernel to the version that Edgy is using in /boot/grub/menu.lst.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by abh83 on 2006-12-10
so how exactly would i do this (please keep in mind i'm a newb)?

This is what i have for dapper:

> title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


is this the latest kernel version: 2.6.17-10-generic ??

---

### Post by taurus on 2006-12-10
I also need to know what partition do you have Edgy on!  Right now, it looks like you have Dapper on /dev/hda2, (hd0,1).

---

### Post by abh83 on 2006-12-10
thx for ur help!!

its on hda4


not sure what the "(hd0,1)" stands for or if you need that from me too?

---

### Post by abh83 on 2006-12-10
would it have to look something like this:

title Ubuntu, kernel 2.6.17-10
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10 root=/dev/hda4 ro quiet splash
initrd /boot/initrd.img-2.6.17-10
savedefault
boot

---

### Post by bulldog on 2006-12-10
> **abh83 said:**
> would it have to look something like this:

title Ubuntu, kernel 2.6.17-10
root (hd0,4) <-------
kernel /boot/vmlinuz-2.6.17-10 root=/dev/hda4 ro quiet splash
initrd /boot/initrd.img-2.6.17-10
savedefault
boot

Almost,GRUB starts counting with a zero,so it would be (hd0,3):D

---

### Post by abh83 on 2006-12-10
okay thx for your help... i will test this now however why did use hd0,3??

thx

---

### Post by bulldog on 2006-12-10
Grub counting start with zero,so your first partition would be (hd0,0)the second is (hd0,1) and so on.
So your fourth partition is (hd0,3) in Grub talk.:cool:

---

### Post by abh83 on 2006-12-10
okay just tried this and i got an error... something along the line: ...e15... :(

anything else i can try?

---

### Post by bulldog on 2006-12-10
If you've got an error I should appreciate the exact error.
This is my Edgy entry```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```I modified it for you to use.

**EDIT:**
If you add it to your menu.lst,can you post the menu.lst so I can have a look?

---

### Post by abh83 on 2006-12-10
maybe the kernel version is wrong?

i had to google myself for 2.6.17-10

---

### Post by bulldog on 2006-12-10
Take a look in /boot to see which kernels are listed there.

---

### Post by abh83 on 2006-12-10
sorry for the delayed response... it takes a while to restart test and boot back into linux/winXP :)

my error:
> Booting' Ubu, kernel 2.6.17-10'
root (hd0,3)
 file system type is ext2fs, partition type 0x83
kernel: /boot/vmlinuz-2.6.17-10 root=/dev/hda4 ro quiet splash

error 15: file not found

i think it could be the kernel version?

---

### Post by bulldog on 2006-12-10
See my previous post.....and I have to warn you,I have a habit to edit my post frequently when a question comes in mind,so watch for edits. :D
Try this one instead.```
title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

```

---

### Post by abh83 on 2006-12-10
okay i am still getting the same error.

this is my menu list:

> title    Ubuntu, kernel 2.6.17-10-generic
root     (hd0,3)
kernel   /boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro quiet splash
initrd   /boot/initrd.img-2.6.17-10-generic
savedefault
boot


title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

could i be using the wrong partition? is it possible to see what partitions i have?

thx again... greatly appreciate ur help!

---

### Post by bulldog on 2006-12-10
Give the outcome of ```
sudo fdisk -l (l as in like ) 
```

**EDIT:**
Don't think the partition is wrong.
In the last stage GRUB will be installed and I think there's some file missing in your /boot directory.
We can copy and paste a lot from my Edgy install but I can't guarantee it will boot.

In my opinion a new install is the safest way to solve this.
```
title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hda4 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot
```
You can put this one to the menu.lst but I think it's useless.

I'm off for tonight,have to be up at six and it is half past midnight here.
I bookmark this thread and be back over 17 hours,if you haven't solved it I will read it here.

---

### Post by abh83 on 2006-12-10
so this is my sudo fdisk -l:
> Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3819    30676086    7  HPFS/NTFS
/dev/hda2            3820        8026    33792727+  83  Linux
/dev/hda3           11686       12161     3823470    5  Extended
/dev/hda4            8027       11685    29390917+  83  Linux
/dev/hda5           11974       12161     1510078+  82  Linux swap / Solaris
/dev/hda6   *       11686       11956     2176744+  83  Linux
/dev/hda7           11957       11973      136521   82  Linux swap / Solaris

Partition table entries are not in disk order


could it be on hda6? i know hda2 is my current dapper installation!

i guess you're right maybe a reinstall is best solution!

---

### Post by bulldog on 2006-12-10
Change (hd0,3) in (hd0,5) and the hda4 in hda6 to see if that works

Maybe we can work it out but than we have to mount your partitions to see where the distro is.
Tomorrow I have plenty of time if you want,but I call it a day for now.
Let me know what your decision is by a PM or something.

---

### Post by abh83 on 2006-12-10
excellent!!! it works... thx again! Hope i didn't waste too much of your precious time! ;)

---

