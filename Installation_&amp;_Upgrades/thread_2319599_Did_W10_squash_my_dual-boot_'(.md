---
title: "Did W10 squash my dual-boot? :'("
date: 2016-04-05
forum: Installation &amp; Upgrades
---

### Post by williamstome on 2016-04-05
I previously had W7 and Ubuntu 14.04 dualbooting, running fine for the longest time.
The other day, I upgraded W7 to W10. Foolish me!
Now, I can no longer boot into Linux! I've used boot-repair, but to no avail.
When (in boot repair) I do an fdisk -l, I get what's seen at the end of this post.
/dev/sda4 looks like it must be my Linux partition, right? It looks like the only thing big enough, but its "extended" label bodes ill.
Furthermore, GParted shows sda4 as unallocated!!!
How can I get my 'buntu back? 
Or did W10 squash it?
:/
-Tom

=====================================================


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4e9d6223

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1047654399   523723776    7  HPFS/NTFS/exFAT
/dev/sda3      1047654400  1048575999      460800   27  Hidden NTFS WinRE
/dev/sda4      1048578046  1953523711   452472833    5  Extended
/dev/sda5      1936814080  1953523711     8354816   82  Linux swap / Solaris

Disk /dev/sdb: 4089 MB, 4089446400 bytes
61 heads, 60 sectors/track, 2182 cylinders, total 7987200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcc38a5b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         736     7987199     3993232    b  W95 FAT32

---

### Post by light_yagami2 on 2016-04-05
Press ESC when booting up and see if it shows your partition. You should be able to boot from it. After that, I'd backup any files, format that partition and reinstall ubuntu to get grub back.

---

### Post by oldfred on 2016-04-05
You have been bitten by a bug in Windows, since many versions ago. Does not seem like a priority for them to fix.

 [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by yancek on 2016-04-05
As I understand this problem from reading a number of posts from people who have upgraded to windows 10, the upgrade modifies the partition table and doesn't include the Linux partition.  If you look at the start and end points for sd4 and sda5 (swap) you will see a very large protion of unused space which is where I expect your Ubuntu was, about 460GB partition.  I don't use windows so never had to deal with this.  You might do a search here at the forums while you are waiting for a response.

---

### Post by williamstome on 2016-04-06
I followed the instructions above, and successfully got the machine to recognize Linux. However, I multiple errors prevented booting into it. I ended up flushing it and reinstalling Linux on the relevant partition, as everything important was backed up. :/

---

