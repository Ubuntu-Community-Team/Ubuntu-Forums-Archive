---
title: "Grub error 15 for slackware  with triple boot"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by sachin6870 on 2009-12-13
Today I installed Slackware 13 and I already have Windows XP, Ubuntu karmic installed.
While installing I skipped Lilo cause I wanted to use grub which Ubuntu has already installed for me. hence to boot slackware from grub, I added following entry in /boot/grub/menu.lst,

```
#Slackware
title Slackware 13, kernel 2.6.29.6-huge
root (hd0,5)
kernel /boot/vmlinuz-huge-2.6.29.6 root=/dev/sd6 ro
boot
```

But when selected "slackware" in grub menu, boot fails with error 15 file not found.  I tried various combinations for slackware entry mentioned over Internet but nothing helped.

 Any idea?



```

sachin@sachin-laptop:~$ sudo fdisk -l
[sudo] password for sachin: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            8139       19456    90911835    f  W95 Ext'd (LBA)
/dev/sda3            5100        8138    24410767+  83  Linux
/dev/sda5           14023       19456    43648573+   7  HPFS/NTFS
/dev/sda6            8139       10363    17872249+  83  Linux (Slackware is installed here)
/dev/sda7           10364       11192     6658911   82  Linux swap / Solaris
/dev/sda8           11193       14022    22731943+  83  Linux

Slackware has been installed on /dev/sd6 partition,


```

Can anyone help? Pointers will be helpful.

Thanks, 

-- Sachin.

---

### Post by sliketymo on 2009-12-13
You have to have Lilo installed to your slack root partition ,sda5,according to your output.The way it is now,slack has no boots!

---

### Post by sachin6870 on 2009-12-13
Thanks for quick reply.

Well, I was following few posts on this forum which suggested me to skip "Lilo" installation and add entry to grub as mentioned above, which makes sense to me. I don't want to screw up Ubuntu booting as that will be my primary Operating system.
  I do see "boot" dir at slackware installation by mounting /dev/sda6 in ubuntu.

-- Sachin

---

### Post by phillw on 2009-12-13
> **sachin6870 said:**
> Today I installed Slackware 13 and I already have Windows XP, Ubuntu karmic installed.
While installing I skipped Lilo cause I wanted to use grub which Ubuntu has already installed for me. hence to boot slackware from grub, I added following entry in /boot/grub/menu.lst,

```
#Slackware
title Slackware 13, kernel 2.6.29.6-huge
root (hd0,5)
kernel /boot/vmlinuz-huge-2.6.29.6 root=/dev/sd6 ro
boot
```But when selected "slackware" in grub menu, boot fails with error 15 file not found.  I tried various combinations for slackware entry mentioned over Internet but nothing helped.

 Any idea?



```

sachin@sachin-laptop:~$ sudo fdisk -l
[sudo] password for sachin: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            8139       19456    90911835    f  W95 Ext'd (LBA)
/dev/sda3            5100        8138    24410767+  83  Linux
/dev/sda5           14023       19456    43648573+   7  HPFS/NTFS
/dev/sda6            8139       10363    17872249+  83  Linux (Slackware is installed here)
/dev/sda7           10364       11192     6658911   82  Linux swap / Solaris
/dev/sda8           11193       14022    22731943+  83  Linux

Slackware has been installed on /dev/sd6 partition,


```Can anyone help? Pointers will be helpful.

Thanks, 

-- Sachin.

You say you're on Karmic ?

Then you're on Grub2, not grub legacy, therefore no menu.lst is used.

Can you check, please.

```
grub-install -v
```Thanks,

Phill.

---

### Post by sachin6870 on 2009-12-13
I am still using grub legacy, I decided to skip "grub upgrade" while upgrading to Ubuntu karmic.

sachin@sachin-laptop:/media/windows3$ grub-install -v
grub-install (GNU GRUB 0.97)


-- Sachin.

---

### Post by phillw on 2009-12-13
> **sachin6870 said:**
> I am still using grub legacy, I decided to skip "grub upgrade" while upgrading to Ubuntu karmic.

sachin@sachin-laptop:/media/windows3$ grub-install -v
grub-install (GNU GRUB 0.97)


-- Sachin.

Grub2 is pretty darn good at spotting operating systems as they appear and disappear on its own. The instructions have been revised since i broke my upgrade. If you fancy having a quick read through, head over to [http://www.vpolink.com/blog.php?b=2](http://www.vpolink.com/blog.php?b=2)  If nothing else, it'll give you a chuckle :-)

Regards,

Phill.

---

### Post by sachin6870 on 2009-12-13
> **phillw said:**
> Grub2 is pretty darn good at spotting operating systems as they appear and disappear on its own. The instructions have been revised since i broke my upgrade. If you fancy having a quick read through, head over to [http://www.vpolink.com/blog.php?b=2](http://www.vpolink.com/blog.php?b=2)  If nothing else, it'll give you a chuckle :-)

Regards,

Phill.

upgrading to grub2 solved slackware boot issue. 

Thanks Phill for pointers.

-- Sachin

---

