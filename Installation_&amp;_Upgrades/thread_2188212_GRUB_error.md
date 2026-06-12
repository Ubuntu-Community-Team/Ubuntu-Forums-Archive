---
title: "GRUB error"
date: 2013-11-16
forum: Installation &amp; Upgrades
---

### Post by alfirdaous on 2013-11-16
Hello everybody,

I Would like to access Ubuntu, installed using wubi on Windows, but it showing this error:

[http://cdn.ttgtmedia.com/digitalguide/images/Misc/figuur1.gif](http://cdn.ttgtmedia.com/digitalguide/images/Misc/figuur1.gif)

Ubuntu is 12.10
Windows Vista

I used LiveCD to access Ubuntu, and here are some commnd results:

```

ubuntu@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            1.5G   44M  1.5G   3% /
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           606M  864K  606M   1% /run
/dev/sdb1       976M  753M  224M  78% /cdrom
/dev/loop0      723M  723M     0 100% /rofs
tmpfs           1.5G  8.0K  1.5G   1% /tmp
none            5.0M  4.0K  5.0M   1% /run/lock
none            1.5G   76K  1.5G   1% /run/shm
none            100M   40K  100M   1% /run/user
/dev/sda2        32G  478M   31G   2% /media/ubuntu/Linux Ubuntu
/dev/sr1         24M   24M     0 100% /media/ubuntu/WD Unlocker


==================================


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x347bad10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   192890879    96445408+   7  HPFS/NTFS/exFAT
/dev/sda2       192890880   258426879    32768000    7  HPFS/NTFS/exFAT
/dev/sda3       258426880   289146879    15360000    f  W95 Ext'd (LBA)
/dev/sda4       289146880   312571903    11712512    7  HPFS/NTFS/exFAT
/dev/sda5       258428928   289146879    15358976    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1027 MB, 1027603968 bytes
255 heads, 63 sectors/track, 124 cylinders, total 2007039 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     2007038     1003488    b  W95 FAT32


===================================================


ubuntu@ubuntu: $ cd /boot/grub/
ubuntu@ubuntu:/boot/grub$ ls
gfxblacklist.txt  grubenv


```

I am looking for recovering my data using any tool, and I can re-install Ubuntu later on.

Thanks for your reply

---

### Post by oldfred on 2013-11-16
A couple of ways that others have posted. Can you then mount it?
 How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

   [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
Then check if you can mount it & read it:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt


 Missing root.disk
[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
[http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted](http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted)

---

### Post by bcbc on 2013-11-16
Run chkdsk /f from windows before you try anything else.

See 'missing root disk' links above.

---

### Post by alfirdaous on 2013-11-19
thx for your reply, I think data was lost, the doler found000 size is 0 KB

---

