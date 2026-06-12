---
title: "Boot damaged after resiszing the partition in win7"
date: 2015-09-04
forum: Installation &amp; Upgrades
---

### Post by Amol_Palshetkar on 2015-09-04
My boot repair url as below:

[http://paste.ubuntu.com/12270865/](http://paste.ubuntu.com/12270865/)

[http://paste.ubuntu.com/12270925/](http://paste.ubuntu.com/12270925/)

---

### Post by Bucky Ball on 2015-09-04
Hi and welcome. Which output do you want us to look at? You've provided two links. 

You resized a Ubuntu partition with Windows? As you may have found out, you don't do that. Win partitions are to be resized with Win software, Linux with Linux software. Resizing Win with Gparted, say, can seriously screw your Win partition. And vice versa, as you may have discovered.

Either way, you no longer have Ubuntu installed in either output. Ubuntu uses EXT partitions. You have none. /swap is all that remains. See this from your output (have a good look through your output for clues).

```
1 disks with OS, **1 OS** : 0 Linux, 0 MacOS, **1 Windows**, 0 unknown type OS.
```

You have one disk, one OS, and that OS is Windows.

PS: It would also be helpful if you give more detail about what you've actually done, any error messages, what happened and what is happening now. Also your machine specs and Ubuntu release.

---

### Post by oldfred on 2015-09-04
You have the classic case where Windows rewrites the partition table & "forgets" to include your Linux formatted partition. Inside you extended partition is a large gap from start of extended to start of swap.

Many have used testdisk or parted rescue, restored partition and reinstalled grub and system has fully worked. Some have not.

You need to add missing partition to existing partitions and it is/was a logical partition that must then be inside the current extended partition.

Best to backup current partition table, so if you damage partition table in updating you can easily restore to current condition.

       Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

Others with same issue:

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
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)#

---

