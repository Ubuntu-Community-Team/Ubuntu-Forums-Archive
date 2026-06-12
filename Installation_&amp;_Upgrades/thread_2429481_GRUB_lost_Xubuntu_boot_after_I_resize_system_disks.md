---
title: "GRUB lost Xubuntu boot after I resize system disks on windows 7"
date: 2019-10-18
forum: Installation &amp; Upgrades
---

### Post by nguyenhaison18 on 2019-10-18
Hello, 

My computer setup dual boot: Xubuntu and Windows 7. Today, I used AOMEI to resize the C drive on windows 7. AOMEI creates a WinPE to complete this. After restart computer, my GRUB like this picture. I type "exit" and it go straight to windows 7, no more the list to choose Xubuntu. I have restarted twice to check it but same result. Is there any way to fix it? Thanks you so much for any help :). (Sr if my English is not good)
Edit 1: I have use Boot-Repair with Recommend Repair but it's not change. My log here: [http://paste.ubuntu.com/p/P6S6GhhWCN/](http://paste.ubuntu.com/p/P6S6GhhWCN/)
[ATTACH=CONFIG]284198[/ATTACH]

---

### Post by oldfred on 2019-10-18
You show no Linux partition.

Windows has for years with MBR partitioning, "forgets" to write partition table on updates to include Linux partitions.

I think this is the first time I have seen this with gpt. They must have added the "bug" to newer partitioning tools to make sure to frustrate Linux users.

You have a large gap where you Linux partition(s) were. If more than one partition a bit more complicated.
```
/dev/sda3               468,992    83,886,767    83,417,776 Data partition (Windows/Linux)
/dev/sda4           223,890,096   250,065,583    26,175,488 Data partition (Windows/Linux)

```

backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print

Check to see if backup gpt partition table was also incorrectly rewritten. Windows does not always see backup gpt table. 
sudo gdisk -l /dev/sda

If not you can see what testdisk shows or use parted rescue.
With parted rescue and if one partition the start of missing partition will be a few sectors after sda3 and end just before sda4. Partitions have been renumbered, but that in most cases does not matter as UUID or GUID are correct ways to refer to partitions. You may have to totally reinstall grub also, using Boot-Repair's advanced mode.

Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988) &
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[https://www.gnu.org/software/parted/manual/parted.html#rescue](https://www.gnu.org/software/parted/manual/parted.html#rescue)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition](https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition)

Recently have seen several users using AOMEI having this issue. Best to only use Windows tools to shrink a NTFS partition and that from inside Windows. And then use gparted for everything else.

---

### Post by nguyenhaison18 on 2019-10-20
Thanks you for your help. You right, my ubuntu partitions (root and home) were deleted while AOMEI resize the C drive. I have re-installed ubuntu. I think it doesn't have any solution to fix it, except re-install this :(.

---

