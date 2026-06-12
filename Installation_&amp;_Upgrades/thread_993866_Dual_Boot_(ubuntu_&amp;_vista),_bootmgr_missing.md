---
title: "Dual Boot (ubuntu &amp; vista), bootmgr missing"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by viranth on 2008-11-26
Hello.

I have a couple of hardrives one has vista on it(c:), and when I installed ubuntu 8.10 last night, I went with the guided install and it chose another hardrive(e:) than the one vista is on.

The install went fine, and when I rebooted I did not get a boot menu at all, it just loaded into vista. Where e: is now 400GB smaller (I selected that for ubuntu).

How do I boot into ubuntu? When I select e: as first boot drive in bios, I get the BOOTMGR is missing error. If I choose c: I load right into vista.

Thank you in advance.

---

### Post by TFX360 on 2008-11-26
Look [here]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm").

---

### Post by viranth on 2008-11-26
Yes, this shows you to use the same hardrive as your windows system, just shrink the partition and make one availiable for linux.

But mine is on another hardrive alltogether, and not the main drive.

I'm interested in finding a way to choose which one to boot from, like back in the dos days when you needed more memory for example.

---

### Post by TFX360 on 2008-11-26
Check

```
vim /boot/grub/menu.lst
```

There you can define the bootable sdx's/hdd's.

---

### Post by viranth on 2008-11-26
But how do I get into ubuntu to write that?

I assume that if I use the livecd it won't boot into the partition I already made?

Like I said, I can get into vista like I always did, but unable to boot into ubuntu.

---

### Post by caljohnsmith on 2008-11-26
How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by viranth on 2008-11-26
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb5b7b5b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       16065   312576704   156280320    f  W95 Ext'd (LBA)
/dev/sda5           16128   312576704   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4fe759c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   293044223   146521088    7  HPFS/NTFS

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3de05faa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   625844204   312921078+   7  HPFS/NTFS
/dev/sdc2       625844205  1465144064   419649930    5  Extended
/dev/sdc5       625844268  1446910289   410533011   83  Linux
/dev/sdc6      1446910353  1465144064     9116856   82  Linux swap / Solaris

Disk /dev/sdd: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1b161b15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   586067264   293033601    7  HPFS/NTFS

---

### Post by viranth on 2008-11-26
ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
ubuntu@ubuntu:~$ sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system

Edit. the others came back with nothing.

---

### Post by viranth on 2008-11-26
ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
8204

---

### Post by caljohnsmith on 2008-11-26
Which drive is your Vista drive? Also, to make the Ubuntu drive bootable, you'll need to install Grub to its MBR (Master Boot Record), which you can do with:
```
sudo grub
grub> root (hd2,4)
grub> setup (hd2)
grub> quit

```
Then reboot, set your BIOS to boot the Ubuntu drive, and let me know what happens. We can work from there. :)

---

### Post by viranth on 2008-11-26
caljohnsmith: That worked, thanks.

---

### Post by caljohnsmith on 2008-11-26
Glad that worked OK; in case you need a hand booting Vista from your Grub menu, I can help with that too. Otherwise, cheers and have fun with Ubuntu. :)

---

