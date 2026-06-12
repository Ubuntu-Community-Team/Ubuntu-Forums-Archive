---
title: "Cant boot into Ubuntu 14.04 after Windows 8.1 install"
date: 2015-11-13
forum: Installation &amp; Upgrades
---

### Post by addlednoob on 2015-11-13
Dear Benevolent Givers of Ubuntu Advice,

I installed windows 8.1 in a partition alongside Ubuntu 14.04.

Ubuntu will no longer boot, as Windows boots immediately upon startup. 

Running boot repair on live disc has not changed the situation.

Details are here; [http://paste.ubuntu.com/13246917/](http://paste.ubuntu.com/13246917/)

Ive pasted a snap of the drive layout below..

Would be brilliant if someone here could help get my Ubuntu booted up again..

Thanks


[ATTACH=CONFIG]265541[/ATTACH]

---

### Post by grahammechanical on 2015-11-13
> 1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

You do not have Ubuntu installed. I have no idea what you have done. Where did you intend Windows to be installed? I can only guess that the Windows Installer did not create a Windows partition in that unallocated space to install Windows in but instead installed Windows in the only partition large enough partition and that was the partition Ubuntu was in (sda2). 

With all the goodwill in the world, we cannot change reality.

Regards.

---

### Post by oldfred on 2015-11-13
It looks like the unallocated in the extended partition was your Linux partition. 
Windows (all versions)  rewrites partition table and always forgets to include the logical Linux partitions. It includes swap for some reason.

Many users have used parted rescue or testdisk and been able to fully restore the Ubuntu install.

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

### Post by addlednoob on 2015-11-14
Thanks old Fred. Your links and tips did the trick. 

I used testdisc running in LiveCD to restore partition table, then ran boot-repar again and upon startup was greeted with a lovely grub boot menu and a functioning boot into windows 8.1 and Ubuntu.

Next time ill keep windows in a vBox where it belongs..

---

### Post by addlednoob on 2015-11-14
> **grahammechanical said:**
> You do not have Ubuntu installed. I  have no idea what you have done. Where did you intend Windows to be  installed? I can only guess that the Windows Installer did not create a  Windows partition in that unallocated space to install Windows in but  instead installed Windows in the only partition large enough partition  and that was the partition Ubuntu was in (sda2). 

With all the goodwill in the world, we cannot change reality.

Regards.

Thanks for your fatalistic wisdom, 
but as "oldfred" observed, it is not immutable "reality" we are trying to change, but simply a windows overwrite of my partition table!

---

