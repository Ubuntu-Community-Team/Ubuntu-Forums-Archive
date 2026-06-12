---
title: "Windows 7 Set Active Partition Mistake, Now Boots Into GRUB Rescue"
date: 2015-11-30
forum: MINT
---

### Post by mix2 on 2015-11-30
I had an Ubuntu derived OS (Mint, but that shouldn't matter, because the issue is more with GRUB) installed alongside Windows 7. GRUB was the bootloader that chose an OS on boot. In Windows 7, I used the Disk Management to set the Active Partition to the same partition that was my C:\ drive. The computer now boots into GRUB with the message, "error: no such partition. Entering rescue mode... grub rescue>"

Note to self: do not follow Microsoft's instructions for anything, ever.

Researching GRUB rescue, I found these two commands that provide info that might be useful.

The "set" command shows
```

cmdpath=(hd0)
prefix=(hd0,msdos6)/boot/grub
root=hd0,msdos6
```

And "ls" shows

```
(hd0) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1)
```

Calling "ls hd(0, x)" for various values of x (0, 1, 2, 3, msdos1, msdos2, msdos5) returns that the file system is unrecognized for all of them.

"rootnoverify" is an unknown command.

I do not remember offhand which partition was the Linux one (though I'd guess it's the non-msdos one). All I know is that there was only one hard drive with 2 OSes in two main partitions, but there were some extra hidden partitions for system boot stuff.

This is probably something that would be easy to fix if you know exactly what to do, but clearly, someone who sets their Active Partition to their C:\ drive has absolutely no idea what they're doing. I'm sorry for the stupid question, but I need to get this computer functional again as soon as possible and figured it would be better to ask for help.

So... what's the best way to fix this? I have not yet messed with any Windows or Linux repair disks, because I really do not want to erase anything accidentally.

EDIT:

Booted with Linux Mint Live install CD, opened GParted, and it appears that the Linux partition is unallocated! What fun.

EDIT EDIT:

Used parted to rescue unallocated partition. Everything appears to be back to normal.

Also, found this [http://askubuntu.com/questions/577609/i-set-windows-c-drive-as-acitve-and-now-my-ubuntu-partition-has-become-free-spa](http://askubuntu.com/questions/577609/i-set-windows-c-drive-as-acitve-and-now-my-ubuntu-partition-has-become-free-spa) which appears to be the same problem I had. Followed second answer, which fixed everything.

---

### Post by howefield on 2015-11-30
Thread moved to the "*MINT*" forum.

---

