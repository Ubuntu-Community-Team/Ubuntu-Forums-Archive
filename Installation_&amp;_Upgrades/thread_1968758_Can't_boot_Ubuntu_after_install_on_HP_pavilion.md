---
title: "Can't boot Ubuntu after install on HP pavilion"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by JeyPeyy on 2012-04-29
So I just installed Ubuntu 12.04 on my parent's HP Pavilion. The live-USB works fine and all, but when I rebooted, the computer still thought it was supposed to boot Windows. So I booted the live USB again and used gparted to change the boot flag to the Ubuntu partition. I'm not sure if I should pick the extended partiton or the root partition, so I've tried both and neither works.

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5d92a095

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   586144347   292968750    7  HPFS/NTFS/exFAT
/dev/sda3       586145792   617807871    15831040    7  HPFS/NTFS/exFAT
**/dev/sda4   *   617809918  1465147391   423668737    5  Extended**
/dev/sda5       617809920  1457651711   419920896   83  Linux
/dev/sda6      1457653760  1465147391     3746816   82  Linux swap / Solaris

Disk /dev/sdb: 1021 MB, 1021125120 bytes
32 heads, 63 sectors/track, 989 cylinders, total 1994385 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa1d4dbed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         247     1993823      996788+   c  W95 FAT32 (LBA)



If I choose the Extended partition (sda4), there's a blinking underscore line in the upper left corner of the screen forever, and if I choose the root partition (sda5), there's a message that tells me it can't find any partition to boot.

So what partition should be flagged, and why wont it work?

---

### Post by JeyPeyy on 2012-04-29
And here's a pic of gparted
[IMG]http://i.imgur.com/c9SP3.png[/IMG]

---

### Post by carl4926 on 2012-04-29
See if supergrubdisk will boot ubuntu

Then use a terminal and do

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

---

### Post by JeyPeyy on 2012-04-29
> **carl4926 said:**
> See if supergrubdisk will boot ubuntu

Then use a terminal and do

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

Okay so I succeeded to boot Ubuntu from supergrubdisk and I did what you told me, but it still wont work when I reboot. I don't think the problem lies in grub, but rather in BIOS/MBR or the flags.

I'm not very good at those things so I would like to get some help with that.

---

### Post by JeyPeyy on 2012-04-29
I'm not sure why it installed the system under an extended partition. Is it needed? Can I reinstall and make sure it installs without an extended partition?

---

### Post by jadtech on 2012-04-29
the 2 partition look right to me ext4 sda5 for / root and sda6 for swap 

as I understand it grub  goes to sda 

that should give you daul boot windows ubuntu

---

### Post by darkod on 2012-04-29
1. Put the boot flag back to sda1. Windows needs it and linux (grub) doesn't care about the boot flag when it boots.

2. Having ubuntu on logical partitions is fine. The maximum is 4 primary partitions and since you have 3 only for windows, the ubuntu root + swap are logical, the only possible solution (you can't have 5 primary ones). That is not your issue.

3. One thing you can try from terminal in live mode is:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Restart and see if it helped. If it didn't we will take it further.

Don't use supergrub, often it can make things worse.

---

### Post by carl4926 on 2012-04-29
Is sda First HD in BIOS boot order

---

### Post by JeyPeyy on 2012-04-29
> **jadtech said:**
> the 2 partition look right to me ext4 sda5 for / root and sda6 for swap 

as I understand it grub  goes to sda 

that should give you daul boot windows ubuntu

And the boot flag? Should it be on sda4 or sda5? I guess MBR only sees sda1, sda2, sda3 and sda4, right? So if I put the boot flag on sda4, it will boot sda4, but grub is installed on sda5. Therefore it won't boot grub, which is the problem.

---

### Post by carl4926 on 2012-04-29
I think the boot flag doesn't matter for windows either if you are using grub, doesn't for me.

---

### Post by carl4926 on 2012-04-29
The boot flag on the extended is normal when root is a logical inside it. But more typical with grub legacy distros

---

### Post by JeyPeyy on 2012-04-29
> **darkod said:**
> 1. Put the boot flag back to sda1. Windows needs it and linux (grub) doesn't care about the boot flag when it boots.

2. Having ubuntu on logical partitions is fine. The maximum is 4 primary partitions and since you have 3 only for windows, the ubuntu root + swap are logical, the only possible solution (you can't have 5 primary ones). That is not your issue.

3. One thing you can try from terminal in live mode is:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Restart and see if it helped. If it didn't we will take it further.

Don't use supergrub, often it can make things worse.

Okay that fixed it. Thanks all!

---

### Post by darkod on 2012-04-29
> **carl4926 said:**
> I think the boot flag doesn't matter for windows either if you are using grub, doesn't for me.

I think you are right. But I still prefer to keep it on the correct partition in case you go back to windows bootloader even temporary one day in need.

---

### Post by carl4926 on 2012-04-29
> **darkod said:**
> I think you are right. But I still prefer to keep it on the correct partition in case you go back to windows bootloader even temporary one day in need.

Agreed

---

