---
title: "Grub error 17 help needed"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by linux saved my life on 2008-04-16
Hello ubuntu community

Im completly new to any and all linux and i have enjoyed ubntu on my live cd for a few days, so i decided to install it.

I had already partitioned my 400gb HD to 260gb for winXP with the rest for linux.

The instal went without a hitch but when i restarted i got the evil
 "GRUB 17" error message.

Can somebody plese help me with this.
Im using ubuntu 7.10 on a computer without internet

---

### Post by dstew on 2008-04-16
If it is just the error message, with no explanation, it is a grub stage1.5 error. This usually means that grub was mis-installed. You will need to install grub again.

To re-install grub, boot a Live CD, open a terminal window (Applications --> Accessories --> Terminal) and enter the command **sudo grub** on the command line. That gets you the grub shell with the **grub>** prompt. On the grub command line, enter```
find /boot/grub/stage2
```It will return a value, like (hd0,2). Whatever value it returns, use as the argument for the root statement, and setup grub in the MBR of the first disk:```
root (hd2,0)
setup (hd0)
quit
```Close the terminal window, log out of the Live CD system, remove the CD and reboot. Hopefully you will get a grub menu. If not, post back.

---

### Post by linux saved my life on 2008-04-16
No luck

On startup the full message is

```
GRUB Loading stage 1.5.

Grub Loading,please wait...
Error 17
```

**sudo fdisk -l** results in ```
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd56d3c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       32203   258665368+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *       32204       48501   130913685   83  Linux
/dev/sda3           48502       48641     1124550    5  Extended
/dev/sda5           48502       48641     1124518+  82  Linux swap / Solaris

Disk /dev/sdb: 2048 MB, 2048901120 bytes
64 heads, 63 sectors/track, 992 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000


```

Finaly, In the partitionor thier is 5MB free space after the windows partion but before the linux partion. This may be causeing the cylinder boundary issue.

---

### Post by dstew on 2008-04-17
What was the output of find /boot/grub/stage2?

---

### Post by linux saved my life on 2008-04-17
The file aparently does not exist

I tried manualy searching for the file but it doesnt show up in the explorer

Prior to entering the code you sedgested the file existed. Is it posible that the code deleted the file?

---

### Post by dstew on 2008-04-17
> Is it posible that the code deleted the file?The grub find command would not delete the file. It seems that your Ubuntu installation did not go properly. To double check, boot the Ubuntu Live CD. Open a terminal window and enter these commands:```
sudo mkdir /media/sda2
sudo mount -t ext3 /dev/sda2 /media/sda2
ls -l /media/sda2
```That should give you a directory listing of the root directory of /dev/sda2, which supposedly contains your Ubuntu root file system. If any of these commands gives you an error, please post the command and the error message to this forum.

---

