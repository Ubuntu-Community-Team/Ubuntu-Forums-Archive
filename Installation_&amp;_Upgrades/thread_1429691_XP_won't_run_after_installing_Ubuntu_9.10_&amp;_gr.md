---
title: "XP won't run after installing Ubuntu 9.10 &amp; grub2"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by duanekf2jc on 2010-03-14
I installed Ubuntu 9.10 & grub2 on a Toshiba sattellite laptop last night:
- Win XP shows up in the Grub2 menu.
- When I boot Win XP, it says autock program not found, skipping autocheck, then Win XP stops booting.
- I did a little digging on the net, & found I have to unhide the NTFS partition for Win XP (hd0,1)
- Grub2 doesn't have an unhide command.
- I tried to run parttool, & got the "command not found".

Have I been following the right path to solve this problem?
Any other ideas?
Thanks in advance!

Duane

---

### Post by oldfred on 2010-03-14
One of the instructions I found had a download that looked like all it did was set the partition boot flag (active partition in windows). if you run this is your window partition show the boot flag (*)?

```
sudo fdisk -l
```

fred@fred-desktop:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa51fa51

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7179    57665286    7  HPFS/NTFS
/dev/sda2            9730       19457    78140160   83  Linux
/dev/sda4            7180        9729    20482875

---

### Post by phillw on 2010-03-14
Now, this may sound a bit weird, so let others have a say..

When windows complains, I find the least pain and messing about with "is it Win / Is it Grub / Is it Ubuntu etc" way to get on the right side of it is to allow Win to have the MBR back (the bit that does the booting)

So, I'd head over here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  And put Win back in charge.

Once win is in charge and happy booting, head back to the same thread and put Grub in charge.

I have long given up trying to argue with a non-booting Win system via Ubuntu -- Virus ridden, fine - we can help ... but win has to be able to start itself !!!!

Unless you do something suicidal, like formatting the hard drive - Win cannot touch your ubuntu area - and it will sit there patiently for you to put grub back on.

Regards,

Phill

---

### Post by duanekf2jc on 2010-03-16
Hi Phil & Fred,
   I solved the problem. I went into Ubuntu's Disk Utility Program & unhid the Windows disk partition. As received, the windows partition was marked as empty (0x00). I changed it to HPFS/NTFS (0x07).

Thanks for your help!
Duane

---

