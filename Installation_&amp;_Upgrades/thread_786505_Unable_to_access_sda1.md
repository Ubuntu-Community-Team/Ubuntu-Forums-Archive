---
title: "Unable to access sda1"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by CLomax on 2008-05-08
After upgrading from 7.10 to 8.04, which is awesome by the way, I am now unable to access my Windows partition. Menu.lst as follows...

> ## ## End Default Options ##

title		Windows Vista
root		(hd0,0)
savedefault
chainloader	+1

title		Ubuntu 8.04
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3c7d5ff6-b716-499a-9bb8-9fcc8e021a35 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04 Recovery Mode
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3c7d5ff6-b716-499a-9bb8-9fcc8e021a35 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04 memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

As you can see, I have two partitions and one OS on each. I am absolutely certain that this is the correct configuration because I used this with 7.10.

Now the problem is that I can't mount the first partition, I consulted gParted which told me that...
> Unable to read the contents of this filesystem! Because of this some operations may be unavailable.

So I can't see it, can't look into it and am unable to fix it on my own initiative. I have a feeling that this happened because I was playing about with EasyBCD before installing, just getting rid of NeoGrub that 7.10 used. If you need more information, let me know.

I appreciate any help. Thanks

---

### Post by Pumalite on 2008-05-08
Post:
sudo fdisk -l

---

### Post by CLomax on 2008-05-08
> Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f1503e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17416   139890688    7  HPFS/NTFS
/dev/sda2           17416       20023    20941824   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf4dd2a78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312568832    7  HPFS/NTFS


Forgot about that.

---

### Post by Herman on 2008-05-08
```
## ## End Default Options ##

title        Ubuntu 8.04
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=3c7d5ff6-b716-499a-9bb8-9fcc8e021a35 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04 Recovery Mode
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=3c7d5ff6-b716-499a-9bb8-9fcc8e021a35 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04 memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

title        Windows Vista
 root        (hd0,0)
 savedefault
 chainloader    +1
 
```:) Hello CLomax,
Hey, your Windows Visat boot stanza has ended up in your Debian automagic kernels list! You should remove it from there and paste it below the bottom of the Debian automagic kernels list.

I think your Windows Vista partition probably just needs a file system check, so you should run CHKDSK from your Windows Vista Installation CD.

Regards, Herman

---

### Post by Pumalite on 2008-05-08
map it too:
map (hd0) (hd1)
map Hd1) (hd0)

---

### Post by CLomax on 2008-05-08
Thanks guys, I'll try restarting it.
But before I do, how exactly do I map it? Where do I put the "map (hd0) (hd1); map Hd1) (hd0)"?

---

### Post by Pumalite on 2008-05-08
title        Windows Vista
 root        (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
 savedefault
 chainloader    +1

---

### Post by CLomax on 2008-05-08
Awesome, thanks alot.

---

### Post by CLomax on 2008-05-08
Turns out my suspicion about NeoGrub was correct.

> Try (hd0,0):NTFS5:No NeoGrub
{It then went on to check other drives and partitions}
Error: Cannot find NeoGrub in all devices.

Looks like my Windows is well and truly screwed. No biggie though.

Thanks for the help, everyone.

---

### Post by Herman on 2008-05-08
> Looks like my Windows is well and truly screwed. No biggie though.:) Probably not, only if you give up easily.
Well, that's up to you. It is easier sometimes to just re-install than to continue trying to fix things, especially if you have a new installation that you haven't put very much work into yet or if you have an old installation with a lot of problems and you weren't too happy with it any more anyway.
But, if you have an operating system you like, you can always make a [Vista Boot Floppy]("http://www.multibooters.co.uk/floppy.html") and boot your Vista with that for now.
I haven't tried yet, but I don't see why we can't figure out how to make a boot CD for Vista as well, using isolinux possibly, and the same files as you would use for the floppy disc.

I don't know for sure if you need the map commands or not. 
Is Windows on your first hard disk or your second hard disk?
I was assuming it was on you first hard disk.
The map commands are only needed when Windows is on a non-first hard disk.

---

### Post by CLomax on 2008-05-08
> **Herman said:**
> :) Probably not, only if you give up easily.
Well, that's up to you. It is easier sometimes to just re-install than to continue trying to fix things, especially if you have a new installation that you haven't put very much work into yet or if you have an old installation with a lot of problems and you weren't too happy with it any more anyway.
But, if you have an operating system you like, you can always make a [Vista Boot Floppy]("http://www.multibooters.co.uk/floppy.html") and boot your Vista with that for now.
I haven't tried yet, but I don't see why we can't figure out how to make a boot CD for Vista as well, using isolinux possibly, and the same files as you would use for the floppy disc.

I don't know for sure if you need the map commands or not. 
Is Windows on your first hard disk or your second hard disk?
I was assuming it was on you first hard disk.
The map commands are only needed when Windows is on a non-first hard disk.

I will not give up easy if it means making more mistakes to learn from :).
I actually know why it isn't booting, it's just a case of making it work.
I have to somehow run EasyBCD and install NeoGrub again because it has been removed, I must have moved or deleted it by accident while doing a bit of operation on the Windows directory or something.

Can this be done?
The only relevant Windows command I know is CHKDSK -f which didn't help at all and I don't have restore points ><.

---

### Post by Herman on 2008-05-09
Okay CLomax, now, you are getting an error message about not being able to find neogrub when you try to boot your Vista installation with GRUB from Ubuntu.

GRUB from Ubuntu will be trying to chainload Vista by it's boot sector.
Your Vista boot sector seems to be pointing to neogrub, but it can't find it, so you are being given an error message instead.

You probably just need to re-install the code for Vista's original boot loader to Vista's boot sector to get Vista to boot for you to begin with.

You should be able to do that by following the advice from lswest or bodhi.zazen in the following how-to, [HOW-TO restoring XP and Vista Bootloader & Restoring GRUB]("http://ubuntuforums.org/showthread.php?t=740221&highlight=lswest").
I think you need to do 'bootrec /fixboot', and that should get your original Visat boot loader working again.

Did your  [Vista Boot Floppy]("http://www.multibooters.co.uk/floppy.html") work?

Regards, Herman :)

---

### Post by CLomax on 2008-05-09
> **Herman said:**
> Okay CLomax, now, you are getting an error message about not being able to find neogrub when you try to boot your Vista installation with GRUB from Ubuntu.

GRUB from Ubuntu will be trying to chainload Vista by it's boot sector.
Your Vista boot sector seems to be pointing to neogrub, but it can't find it, so you are being given an error message instead.

You probably just need to re-install the code for Vista's original boot loader to Vista's boot sector to get Vista to boot for you to begin with.

You should be able to do that by following the advice from lswest or bodhi.zazen in the following how-to, [HOW-TO restoring XP and Vista Bootloader & Restoring GRUB]("http://ubuntuforums.org/showthread.php?t=740221&highlight=lswest").
I think you need to do 'bootrec /fixboot', and that should get your original Visat boot loader working again.

Did your  [Vista Boot Floppy]("http://www.multibooters.co.uk/floppy.html") work?

Regards, Herman :)

Hello Herman, it turns out that I didn't need to carry out any of those instructions but thatk you for sending them anyway, I did learn something from them so they're not completely redundant :).

I solved this problem a different way, a clever one I might add, and I'll post it here in the hopes that someone with the same problem will find it.

It seemed that all I needed to do was install EasyBCD on wine, it will complain about missing .dlls but if you enable all of the .dlls beginning with 'm', it should install. I then went into the directory under Wine and found two files, 'NeoGrub' and 'NeoGrub.mbr' and copied them to the appropriate folder in my Windows partition 'C:\\NTS\' or something like that.

I then booted the vista CD which told me that I had problems with one of my drivers automatically. I let it fix it and restart and it worked :).

I'd like to thank everyone for their ideas, and to Herman distinctively for his/her undying support.

Btw, we don't mark threads as [Solved] anymore, right?

---

### Post by Herman on 2008-05-09
:) Okay, good, I'm glad you have it fixed now. Thanks for letting me know.
Regards, Herman :)

---

