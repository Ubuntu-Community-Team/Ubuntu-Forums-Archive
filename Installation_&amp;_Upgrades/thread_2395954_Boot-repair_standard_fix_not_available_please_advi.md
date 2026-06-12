---
title: "Boot-repair standard fix not available please advise"
date: 2018-07-09
forum: Installation &amp; Upgrades
---

### Post by beulzabob611 on 2018-07-09
If anyone could lend a hand I'd greatly appreciate it.

I was trying to install windows 7 on an unused partition and it seems to have hosed my bootloader.

Please look at [http://paste.ubuntu.com/p/FktFP6csHn/](http://paste.ubuntu.com/p/FktFP6csHn/)

Robert

---

### Post by oldfred on 2018-07-09
You are not showing Windows nor Ubuntu install.
Drive is only showing extended partition and part of extended has swap partition.

Windows is known to hose Linux partition, but usually recoverable. It updates partition table but does not rewrite into partition table any logical Linux partitions. Since partition is still there, you usually can use testdisk to add partition table entry back again. Many also have to re-install grub.

Windows has done this for years and still does it if using BIOS/MBR and a major Windows update or change or install is done.

You can use testdisk or parted rescue.

       Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[https://www.gnu.org/software/parted/manual/parted.html#rescue](https://www.gnu.org/software/parted/manual/parted.html#rescue)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition](https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition)

---

### Post by beulzabob611 on 2018-07-09
SOLVED!

Thanks so much Oldfred!

"Parted" couldn't find any missing partitions, but after doing an extended search with testdisk, I was able to figure out which partitions were the original Linux partitions.  I still had to use Boot-repair after fixing the partitions as you mentioned.

Also, thanks for getting back to me so quickly!

Robert

:KS:KS:KS:KS:KS

---

### Post by oldfred on 2018-07-09
Glad it worked.
You can change to solved.

If this is a newer system with UEFI, you can convert the Windows 7 installer to UEFI boot. DVD is BIOS only, but copy to flash drive & move & rename a couple of files will convert it to UEFI boot.

Then you can use gpt partitioning which Windows does not seem to have the same issues.
But all versions of Windows in UEFI mode must use gpt and all versions of Windows in BIOS boot mode must use MBR(msdos) partitioning. 

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

