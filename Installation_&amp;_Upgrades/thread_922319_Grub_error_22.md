---
title: "Grub error 22"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by M8M on 2008-09-17
After resizing my Vista/Ubuntu partition, my notebook could not boot up. It came up with the following message 
"GRUB Loading stage1.5."
"GRUB loading, please wait. . . . . Error 22"

So as mentioned in the threads, I did the following commands from the Live CD I had.
- "sudo fdisk -lu" and as a result I got the following
"Disk /dev/sda: 100.0GB
 255 heads, 63 sectors/track, 12161 cylinders, total 195371568         sectors
 Units = sectors of 1 * 512 = 512 bytes
 Disk identifier: 0x69664f0a
 Device Boot   Start    End        Blocks     Id   System
 /dev/sda1 *   2048     126445551  63221752   7    HPFS/NTFS
 /dev/sda2    126445568 175597567  24576000   6    FAT16

and then I did the following command
"sudo grub"
"find /boot/grub/stage1" 
and as a result, I got Error 15: File not found.

I hope this info. helps in trying to resolve my problem of trying to get my notebook to boot up. THANKS

---

### Post by Pumalite on 2008-09-17
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by Pumalite on 2008-09-17
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by yabune on 2008-09-17
> **Pumalite said:**
> [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

I have the same problem... I can't boot in any of the operating systems and I get the error 22.

None of this links answer the question.

Anyone knows how to fix this?

---

### Post by yabune on 2008-09-17
the way I found to fix this was this:

[http://www.linuxforums.org/forum/470899-post8.html](http://www.linuxforums.org/forum/470899-post8.html)

I'm going now to try to reinstall ubuntu...

---

### Post by M8M on 2008-09-17
> **yabune said:**
> the way I found to fix this was this:

[http://www.linuxforums.org/forum/470899-post8.html](http://www.linuxforums.org/forum/470899-post8.html)

I'm going now to try to reinstall ubuntu...

This is m8m, just a thank you - this process worked. MERCI

---

