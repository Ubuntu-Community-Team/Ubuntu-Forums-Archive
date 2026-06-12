---
title: "No XP in grub - ubuntu 10.04"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by zob on 2010-06-13
Hi.
I just bought myself a second hand T60 yesterday. It came with a windows license and windows XP installed. I thought I would keep it, so I installed ubuntu 10.04 as a dualboot.

Unfortunately XP doesn't show up in grub. As you can see if I run update-grub: ```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```
As you can see it doesn't find it.
However, if i run fdisk:```
lars@T60-laptop:~$ sudo fdisk -l

Disk /dev/sda: 320.1 Gb, 320072933376 byte
240 heads, 63 sectors/track, 41345 cylinders
Units = cylindre of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcd76cd76

    Enhed Opstart   Start         ****     Blokke   Id  System
/dev/sda1   *       13817       30134   123364080   83  Linux
/dev/sda2           30135       30405     2042968+  82  Linux swap / Solaris
/dev/sda3               2       13816   104441369+   f  w95 udvidet (LBA)
/dev/sda5               2       13816   104441368+   7  HPFS/NTFS


```The sda3 contains the XP-installation. As you can see, I can mount it under /media/System
```
lars@T60-laptop:~$ ls /media/System/
3eef5106b0644866b94eb4469267f6  DRIVERS       Program Files
AUTOEXEC.BAT                    hiberfil.sys  RECYCLER
$AVG                            IO.SYS        System Volume Information
Config.Msi                      MSDOS.SYS     WINDOWS
CONFIG.SYS                      MSOCache
Documents and Settings          pagefile.sys

```

I've attached results from the boot info script. I would appreciate any help on this.

---

### Post by darkod on 2010-06-13
Was there any other ntfs partition that you deleted? XP is installed in a logical partition, /dev/sda5. Its boot files had to be on primary partition otherwise windows can't boot. The boot files are gone now, maybe a primary partition where they were was deleted.

And you can't add XP boot files in a logical partition. Since the boot files don't exist, update-grub doesn't pick XP up, naturally.

There is not much you can do, depending if you think it's worth it. You could create small primary ntfs partition for the boot files, but if you don't have XP cd you will need a workaround to get the boot files. There are few links to download just the boot files and hopefully it would work.

But resizing your ubuntu now to make space for the small ntfs partition can mess it up.

---

### Post by zob on 2010-06-13
Oh thanks. Well yes, actually I did delete something. He had XP on that sda3 drive, but then he had a DATA drive that to me seemed empty. That were I choose to install ubuntu (formatting it to ext4). I must have wiped something in that process, or what?

He actually gave me the original CD also, so I could what?
Make a primary partition containing something...
Do you have a link to that kind of solution, or do you mind to explain it a bit?
Thanks.


Maybe the easiest is just to reinstall windows and the recover GRUB afterwards?!

---

### Post by darkod on 2010-06-13
If you don't mind deleting XP and reinstalling it, that's the easiest way. Of course you would have to add any programs too.

Do you want to reinstall or try to save it?

---

### Post by zob on 2010-06-13
Thanks darkrod. I think I'll just delete windows. And install it, if or when I might need it.
But thanks for your help darkrod. I would probably have been sitting around all day going sudo update-grub if you hadn't shared your knowledge here.

---

### Post by confused57 on 2010-06-13
> **darkod said:**
> Was there any other ntfs partition that you deleted? XP is installed in a logical partition, /dev/sda5. Its boot files had to be on primary partition otherwise windows can't boot. The boot files are gone now, maybe a primary partition where they were was deleted.

And you can't add XP boot files in a logical partition. Since the boot files don't exist, update-grub doesn't pick XP up, naturally.

There is not much you can do, depending if you think it's worth it. You could create small primary ntfs partition for the boot files, but if you don't have XP cd you will need a workaround to get the boot files. There are few links to download just the boot files and hopefully it would work.

But resizing your ubuntu now to make space for the small ntfs partition can mess it up.

I realize the OP is planning on reinstalling XP and you probably already have this one bookmarked that meierfra posted:
[http://ubuntuforums.org/showpost.php?p=5082723&postcount=1](http://ubuntuforums.org/showpost.php?p=5082723&postcount=1)
Maybe it will help someone else.

---

### Post by zob on 2010-06-13
Oh thanks. I sure does look kind of complicated.

---

